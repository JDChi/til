# traceroute 命令

使用 traceroute 命令用于查看主机到目的地址所经过的路由器

```shell
root:~# traceroute www.baidu.com
traceroute to www.baidu.com (183.2.172.185), 30 hops max, 60 byte packets
 1  _gateway (192.168.20.2)  0.337 ms  0.332 ms  0.284 ms
 2  192.168.31.1 (192.168.31.1)  6.210 ms  6.089 ms  5.960 ms
 3  * * *
 4  * * *
 5  * * *
 6  14.147.135.198 (14.147.135.198)  13.839 ms 14.147.135.206 (14.147.135.206)  7.886 ms *
 7  237.32.63.58.broad.gz.gd.dynamic.163data.com.cn (58.63.32.237)  12.506 ms * *
 8  113.96.5.102 (113.96.5.102)  14.069 ms 113.96.5.46 (113.96.5.46)  10.708 ms 113.96.5.202 (113.96.5.202)  13.403 ms
 9  113.96.4.210 (113.96.4.210)  9.719 ms * *
10  14.29.117.178 (14.29.117.178)  16.382 ms  16.323 ms *
11  * 14.29.117.178 (14.29.117.178)  13.832 ms *
12  * * *
13  * * *
14  * * *
```