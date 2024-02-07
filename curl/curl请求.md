# curl 基本请求
## Get
不带任何参数，就是默认 GET 请求 *（在一开始 HTTP/0.9 的协议里，就只有 GET 请求）*
```shell
curl www.example.com
```
## POST
```shell
curl -X POST www.example.com
# 带参数
curl -d"login=hello" -X POST www.example.com
```
## DELETE
```shell
curl -X DELETE www.example.com
```
## HEAD
```shell
curl -I www.example.com

curl --head www.example.com
```