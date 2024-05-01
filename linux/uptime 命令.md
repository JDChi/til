# uptime 命令
显示系统在过去 1min、5min、15min 的平均负载情况。

```shell
➜ uptime
22:54  up 6 days, 22 hrs, 3 users, load averages: 2.76 2.49 2.53
```
对于单核 CPU 来说，如果 load averages: 中的值都等于 1，说明刚好满载运行。如果小于 1，说明 CPU 还有空闲时间。

对于多核（N) CPU 来说，如果 load averages: 中的值都等于 N，说明刚好满载运行。如果小于 N，说明 CPU 还有空闲时间。

理想情况下，CPU 应该满载运行。但在实际生产环境中，我们会有所预留，一般是 平均负载 = 0.7 * CPU 逻辑核数。如果超过了，就是我们要警惕的时候。

另外 Load1、Load5、Load15 的变化，也能让我们用来判断趋势。


