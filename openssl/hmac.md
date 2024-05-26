# hmac

```shell
# 对文件做哈希
root@root:/tmp$ openssl dgst -sha1 hello.txt
SHA1(hello.txt)= f572d396fae9206628714fb2ce00f72e94f2258f
```

使用 hmac，既可以证明消息未被篡改，也能证明消息是正确的发送者发送。它需要一个密钥。

```shell
jdchi1@jdchi1:/tmp$ openssl dgst -sha1 -hmac "mykey" hello.txt
HMAC-SHA1(hello.txt)= 67b36ba31dda5651a4f28d7f61dbc7ae88ff70d3

```


