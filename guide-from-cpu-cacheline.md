# guide from cpu cache line

* Spatial Locality and Temporal Locality, 64kb/cacheline( /sys/devices/system/cpu/cpu%d/cache/index%d/coherency_line_size)
*  use padding to optimize false sharing

## some articles about cpu cacheline
* http://mechanical-sympathy.blogspot.co.uk/2011/07/false-sharing.html