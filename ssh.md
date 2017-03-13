# ssh

## 无密码登录
* ssh-keygen -t rsa -C "xxx@yyy.com"(`全部直接回车即可`)
* 默认用户的当前目录的.ssh目录下会生成id_rsa和id_rsa.pub
* 把id_rsa.pub复制到你想登陆机器的home/xxx/.ssh/authorized_keys中即可
* 后面的ssh和scp都不需要再输入密码了

## agent forwarding
经常会出现你在已经登录的目标服务器上还想通过scp向其它服务器传递文件(这些文件拥有相同的id_rsa.pub)，你有两种方法解决这个问题

* 把你的id_rsa(私钥)复制到你现在登录的服务器即可，问题是你把自己的私钥暴露了出去，这非常不安全
* 利用ssh的agent forwarding功能，通过ssh -A连接到指定的目标服务器，目标服务器会生成一个`$SSH_AUTH_SOCK`环境变量,通过`echo $SSH_AUTH_SOCK`发现不为空，说明你当前的ssh client开启了agent forwarding，那么当前被连接的目标服务器就知道了你本地的私钥，这样就可以在当前的服务器上通过scp给其它服务器传递文件了
* 很多的ssh gui client也提供配置， 例如Zoc7(edit session profile->secure shell->Advanced SSH Settings->Provide agent forwarding for ......)
		