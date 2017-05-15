# zookeeper internal(version:3.4.8)
* sessionTimeout需要与服务端的minSessionTimeout(defaut: 2 * tickTime)和maxSessionTimeout(default: 10 * tickTime)协商

	~~~java
	//确定client端最终的sessionTimeOut
	int minSessionTimeout = getMinSessionTimeout();
	if (sessionTimeout < minSessionTimeout) {
	    sessionTimeout = minSessionTimeout;
	}
	int maxSessionTimeout = getMaxSessionTimeout();
	if (sessionTimeout > maxSessionTimeout) {
	    sessionTimeout = maxSessionTimeout;
	}
	~~~

* connectTimeout = sessionTimeout / zk-hosts-size
* readTimeout = sessionTimeout * 2 / 3
* 客户单持续向服务端发送心跳, 逻辑如下

	~~~java
	if (state.isConnected()) {
	//1000(1 second) is to prevent race condition missing to send the second ping
	//also make sure not to send too many pings when readTimeout is small 
    int timeToNextPing = readTimeout / 2 - clientCnxnSocket.getIdleSend() - 
    		((clientCnxnSocket.getIdleSend() > 1000) ? 1000 : 0);
    //send a ping request either time is due or no packet sent out within MAX_SEND_PING_INTERVAL
    if (timeToNextPing <= 0 || clientCnxnSocket.getIdleSend() > MAX_SEND_PING_INTERVAL) {
        sendPing();
        clientCnxnSocket.updateLastSend();
    } else {
        if (timeToNextPing < to) {
            to = timeToNextPing;
        }
    }
}
	~~~
* ClientCnxn.seenRwServerBefore表示当前客户端实例是否曾经连接到读写的Zookeeper上

	~~~java
	bos.writeBool(this instanceof ReadOnlyZooKeeperServer, "readOnly");
	~~~
* 当readTimeout或者connectTimeout出现的时候, 客户端会抛出SessionTimeoutException
* 客户端发生异常的时候(常见的例如SessionTimeoutException, SessionExpiredException), 连接会重新建立, 当seenRwServerBefore为true的时候, 会用之前的sessionId和sessionPasswd发送ConnectRequest, 注意此时如果发生的异常是SessionExpiredException, 并且seenRwServerBefore为true时一定要关闭当前的Zookeeper, 重新建立新的Zookeeper实例, 因为此时的sessionId已经不合法
* 客户端需要关注的是KeeperState, 而不是States