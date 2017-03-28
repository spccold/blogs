# zookeeper

~~~
1. git clone https://github.com/spccold/zookeeper_v3_4_8.git
2. ant eclipse
3. eclipse -> import(General)
4. edit conf/zoo.cf(dataDir and dataLogDir)
5. edit org.apache.zookeeper.server.ZooKeeperServerMain.main(String[]) with correct zoo.cfg full path
6. build path -> Configure Build path -> Add folder -> choose main/resources
~~~