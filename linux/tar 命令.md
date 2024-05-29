# tar 命令

`-f` 是必须的，位于最后，后面跟压缩包的名字

```shell
# 不解压，仅查看压缩包里的内容
➜  ~ tar -tf hello.zip

# 进一步查看指定文件
➜  ~ tar -tf hello.zip | grep png
```

```shell
# 会在当前目录把内容都平铺解压出来
➜  ~ tar -xf hello.zip

# 如果不想平铺开来，而是想都解压到某个指定文件夹，就需要先创建文件夹，再指定解压的位置
➜  ~ mkdir hello
➜  ~ tar -xf hello.zip -C hello
```

```shell
# 压缩某个目录
➜  ~ tar -cf hello.zip hello
```

