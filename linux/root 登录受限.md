# root 登录受限
我在使用 ssh 登录某台主机的 root 用户下的时候，输入了 root 的密码，但却一直提示无权限，即使我在那台机子上，想自己连自己，也是同样的问题：
```shell
ssh root@192.168.20.136
root@192.168.20.136's password:
Permission denied, please try again.
```

问题在于那台主机的 `sshd_config` 配置有问题，里面有这一项
```
#PermitRootLogin prohibit-password
```
这个表示当前未启用 root 用户的 SSH 登录限制。

应该修改为：
```
PermitRootLogin yes
```
允许 root 用户使用 SSH 密钥登录。

然后重启 shell：
```shell
sudo systemctl restart ssh
```