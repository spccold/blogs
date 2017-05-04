# AWS eureka

~~~
Region: 每个region对应一块地理区域(甚至整个洲)，包含多个Zone
Zone: 包含多个数据中心组成, zone之间相互独立，独立的供电，网络，在同一个region内不同的zone通过高数网络连接

对于自建机房的我们来说，region就对应到机房，zone就对应到机柜(rack)

Eureka 在WAS的部署策略是: 每个region部署一套集群，每个zone上部署一个实例
~~~