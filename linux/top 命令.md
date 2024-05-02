# top 命令
top 命令用于显示当前正在运行的进程。

```bash
top - 14:47:55 up 4 days, 16:44,  3 users,  load average: 0.11, 0.06, 0.01
Tasks: 206 total,   1 running, 205 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.3 us,  0.3 sy,  0.0 ni, 99.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   3925.3 total,    291.8 free,    304.9 used,   3328.7 buff/cache
MiB Swap:      0.0 total,      0.0 free,      0.0 used.   3429.6 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
    910 root      20   0 1343644  42468  26792 S   1.3   1.1  90:59.11 containerd
      1 root      20   0  168492  10948   7420 S   0.0   0.3   0:46.90 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.47 kthreadd
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
```
其中，CPU 时间片分为 
- us（user）
- sy（system）
- ni（nice）
- id（idle）
- wa（iowait）
- hi（hardware IRQ）
- si（software IRQ）
- st（steal）

| 字段 | 含义                                                     |
|----|--------------------------------------------------------|
| us | CPU 在用户态下所占用的时间百分比                                     |
| sy | CPU 在内核态下所占用的时间百分比                                     |
| ni | 调整过优先级的进程所占用的时间百分比                                     |
| id | CPU 在空闲状态所占用的时间百分比                                     |
| wa | CPU 在等待 I/O 状态所占用的时间百分比                                |
| hi | CPU 在硬件中断状态所占用的时间百分比                                   |
| si | CPU 在软件中断状态所占用的时间百分比                                   |
| st | 该项指标只对虚拟机有效，表示分配给当前虚拟机的 CPU 时间中，被同一台物理机上的其它虚拟机占用的时间百分比 |

Linux 系统中一个 nice 值，表示进程的优先级，取值范围是 -20 到 19，默认值为 0。正值表示进程优先级高，负值表示进程优先级低。（从上面的命令输出里可以看到，进程 3 的 nice 值为 -20，表示该进程优先级最高。）