# URI
## spec		

		[scheme:][//authority][path][?query][#fragment]
		authority = [user-info@]host[:port]
		
## demo

		http://spccold:123@localhost:8080/index.html#fragment
		userInfo : wuwo:123
		authority: wuwo:123@localhost:8080
		
		http://spccold:123@localhost/index.html#fragment
		authority: wuwo:123@localhost