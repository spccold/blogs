# cpu cache

## 在多核CPU的结构中，L1和L2是物理核心(带有超线程功能的cpu的一个物理核心可以虚拟出多个虚拟核心, 下面的例子也可以看出来处于同一个物理核心的虚拟核心共享L1和L2)私有的，L3则是单个物理cpu中所有核心共享的

~~~
single physical cpu, 6core, 12 threads

ls /sys/devices/system/cpu/cpu0/cache

=> index0 index1 index2 index3(说明有L1,L2,L3三级缓存)
ls index0/

=> level(几级缓存?), shared_cpu_list(被那些虚拟core共享?), size(缓存大小?), type(缓存类型，只针对L1有效， 分为Data和Instruction)

cat index0/type
=> Data

cat index0/level
=> 1

cat index0/shared_cpu_list 
=> 0,6 (说明L1缓存被core:0 和 core:6共享)

cat index2/shared_cpu_list 
=> 0,6 (说明L2缓存被core:0 和 core:6共享)

cat index3/shared_cpu_list
=> 0-11 (说明L3被0-11之间12个core共享)

cat index1/type
=> Instruction

cat index1/level
=> 1
~~~