# PersistVolume & PersistVolumeClaim
k8s 规定
- PersistVolume 是由管理员负责提供的集群存储
- PersistVolumeClaim 是由用户负责提供的存储请求
  （也就是在这里我们要明白这个资源是分角色的，并不是由某一方全权负责）

一般情况下，两者的工作过程是：
- 管理员准备好存储系统
- 管理员根据存储系统的实际情况，配好 PersistVolume
- 用户根据业务的实际情况，创建 PersistVolumeClaim，声明 Pos 所需的存储能力
- k8s 在创建 Pod 的过程中，综合考虑这两者，如果有 PersistVolume 可以满足 PersistVolumeClaim，则成功；否则 Pod 不会创建，直至等到合适的 PersistVolume 出现。

