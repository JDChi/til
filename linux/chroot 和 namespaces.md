# chroot 和 namespaces
Unix 在 1979年提供了 chroot 命令。
- chroot
  - change root 的缩写
  - 当某个进程经过 chroot 操作后，它的根目录就会被锁定在命令参数所指定的位置，不能再访问和操作该目录之外的其它文件

由于 chroot 存在可能的安全漏洞。2000 年，Linux 引入了 pivot_root 技术来实现文件隔离，直接切换了根文件系统（rootfs）。

2002 年，Linux 引入了一种全新的隔离机制：namespaces。让进程在里面觉得自己拥有整个主机的一切资源。
- namespaces 的八种资源隔离
  - Mount：隔离文件系统
  - UTS：隔离主机的 Hostname,Domain names
  - IPC: 隔离进程间通信的渠道
  - PID：隔离进程编号，无法看到其它名称空间中的 PID
  - Network：隔离网络资源，如网卡、网络站、IP地址、端口等
  - User：隔离用户和用户组
  - Cgroup：隔离 cgroups 信息，进程有自己的 cgroups 的根目录视图
  - Time：隔离系统时间

