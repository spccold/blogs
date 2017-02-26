# cassandra

## understand cassandra advantage of vnodes
* http://stackoverflow.com/questions/19995342/cassandra-num-tokens-is-this-really-num-token-partitions
* http://www.datastax.com/dev/blog/virtual-nodes-in-cassandra-1-2


## run cassandra in eclipse(configure run configurations)

* VM arguments

		-Dcassandra-foreground=yes 
		-Djava.library.path=/Users/xxx/github/cassandra/lib/sigar-bin
		-Dlogback.configurationFile=logback.xml
		-Dcassandra.logdir=/Users/xxx/github/cassandra/logs
		-Dcassandra.storagedir=/Users/xxx/github/cassandra/data
		-Dcassandra.jmx.local.port=7199
		
* Classpath(User Entries, remove default classpath of cassandra  first)

		main - /cassandra/build/classes/
		thrift - /cassandra/build/classes/
		conf - /cassandra/
		all jars in /cassandra/lib/
	
	