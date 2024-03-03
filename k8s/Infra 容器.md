# Infra 容器
Infra Container 是 Pod 中第一个启动的容器，体积很小。

它是 Pod 中其它容器的父容器，Pod 内部多个容器共享 UTS、IPC、网络等名称空间都是通过它来实现的。

如果容器设置为共享 PID 名称空间，则 Infra Container 中的进程将作为 PID 1 进程，其它容器的进程将以它的子进程方式存在。

由于 Infra Container 的实现除了只是注册一些信号的处理器外，就只是以一个 pause() 方法为循环体的无限循环，永远处于 Pause 状态，所以也叫 Pause Container。