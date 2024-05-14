# ping 命令

使用 `ping <ip> -f -l <字节数>`，通过修改`字节数`，可以试探出路径上的最小 MTU。
```shell
root@123:/home/123# ping 192.168.77.254 -f -l 1314
PING 192.168.77.254 (192.168.77.254) 56(84) bytes of data.
^C
--- 192.168.77.254 ping statistics ---
6333 packets transmitted, 2474 received, 60.9348% packet loss, time 1484ms
rtt min/avg/max/mdev = 6.981/137.060/241.008/54.509 ms, pipe 1251, ipg/ewma 0.234/236.369 ms
root@123:/home/123# ping 192.168.77.254 -f -l 1315
ping: WARNING: probably, rcvbuf is not enough to hold preload  # 不能超过 1315 了
PING 192.168.77.254 (192.168.77.254) 56(84) bytes of data.
^C
--- 192.168.77.254 ping statistics ---
7039 packets transmitted, 2878 received, 59.1135% packet loss, time 1667ms
rtt min/avg/max/mdev = 6.708/179.222/303.280/83.713 ms, pipe 1515, ipg/ewma 0.236/252.700 ms
```

 `-f` 和 `-l` 的含义如下：
```shell
man ping
 -f
           Flood ping. For every ECHO_REQUEST sent a period “.” is printed, while for
           every ECHO_REPLY received a backspace is printed. This provides a rapid
           display of how many packets are being dropped. If interval is not given,
           it sets interval to zero and outputs packets as fast as they come back or
           one hundred times per second, whichever is more. Only the super-user may
           use this option with zero interval.
           
 -l preload
           If preload is specified, ping sends that many packets not waiting for
           reply. Only the super-user may select preload more than 3.
```