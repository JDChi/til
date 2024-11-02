# sshpass

sshpass 是一个免交互的 ssh 登录工具，一般我们都会通过 ssh 指令进行远程登录，但在这个过程里会有些交互，如确认 fingerprint，输入密码等。

ssh 需要确保内容是用户键盘输入的，但 sshpass 不需要，它会误导 ssh，以为是用户键盘输入的。

例如有个脚本，可以先设置密码，然后登录对应的主机：
```bash 
#!/bin/bash

host_list='172.16.100.50 172.16.100.51'
user_name=root
user_pwd=redhat

for host in $host_list;do
    sshpass -p$user_pwd ssh -o StrictHostKeyChecking=no $user_name@$host "$1"
done

```

由于密码我们会先记录下来，所以在生产环境里有一定的安全隐患。