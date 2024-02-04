# ngrok
使用 ngrok 可以很快地实现一个临时的内网穿透，帮助我们方便地调试下本地的一些功能。

以 macos 为例：
```shell
brew install ngrok/ngrok/ngrok #安装

ngrok config add-authtoken <TOKEN> #去网站注册后填写 token

ngrok http http://localhost:8080 # 启动
```

访问 [ngrok doc](https://ngrok.com/docs/getting-started/) 查看更多内容。