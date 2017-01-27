# Running multiple Cassandra  nodes in a single host 

* create virtual network interfaces in your pc(linux) 
	*  sudo ifconfig lo:0 127.0.0.2
	*  sudo ifconfig lo:1 127.0.0.3
* edit seeds in cassandra.yaml for every node
	* seeds "127.0.0.1,127.0.0.2,127.0.0.3" 
* edit listen_address and rpc_address in cassandra.yaml for every node
* edit JMX_PORT in cassandra-env.sh for every node
* Changing the location of directories
	* data_file_directories
	* commitlog_directory
	* saved_caches_directory
	* hints_directory 

## directory topology

	--node1
	   -- data
	   -- log
	   -- cache
	   -- hint
	   --apache-cassandra
		 -- bin
		 -- conf
		 --logs
		 -- ......
	--node2
	   -- same to node1
	--node3
	   -- same to node1