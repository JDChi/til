# 创建 & 注册 runner

- 使用 docker 安装 gitlab-runner
```shell
docker pull gitlab/gitlab-runner
```
- 运行容器，并挂载配置目录到本地
```shell
docker run -itd --name=gitlab-runner -v $(pwd)/gitlab-runner/config:/etc/gitla
b-runner -v /var/run/docker.sock:/var/run/docker.sock gitlab/gitlab-runner
```

- 在 gitlab 上创建项目，然后进入 cicd，创建 runner，获取配置

![](../assets/新建项目runner-1.png)

![](../assets/新建项目 runner-2.png)

- 按照步骤提示注册 runner

![](../assets/注册 runner.png)

```shell
$ gitlab-runner register  --url https://gitlab.com  --token xxxxxxxxxxxxxxx
Runtime platform                                    arch=arm64 os=linux pid=83 revision=9882d9c7 version=17.2.1
Running in system-mode.                            
                                                   
Enter the GitLab instance URL (for example, https://gitlab.com/):
[https://gitlab.com]: https://gitlab.com
Verifying runner... is valid                        runner=Gkh1rWSDD
Enter a name for the runner. This is stored only in the local config.toml file:
 [65dfdea6abff]: ls
Enter an executor: virtualbox, docker+machine, kubernetes, docker-autoscaler, instance, custom, parallels, docker, docker-windows, shell, ssh:
docker
Enter the default Docker image (for example, ruby:2.7):
alpine:latest
Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!
Configuration (with the authentication token) was saved in "/etc/gitlab-runner/config.toml" 

$ gitlab-runner run
Runtime platform                                    arch=arm64 os=linux pid=96 revision=9882d9c7 version=17.2.1
Starting multi-runner from /etc/gitlab-runner/config.toml...  builds=0 max_builds=0
Running in system-mode.                            
                                                   
Configuration loaded                                builds=0 max_builds=1
listen_address not defined, metrics & debug endpoints disabled  builds=0 max_builds=1
[session_server].listen_address not defined, session endpoints disabled  builds=0 max_builds=1
Initializing executor providers                     builds=0 max_builds=1

```
- 在 gitlab 的 cicd 上就会提示 runner 创建成功了