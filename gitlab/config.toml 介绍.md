# config.toml 介绍

```toml
concurrent = 1   # 限制 runner 能够同时执行多少个作业
check_interval = 0 # 检查新任务的时间间隔，以秒为单位
shutdown_timeout = 0

[session_server]
  session_timeout = 1800

[[runners]]
  name = "ls"
  url = "https://gitlab.com"
  id = 40369749
  token = "xxxxxxxxxxxxxxxxxx"
  token_obtained_at = 2024-08-03T07:10:31Z
  token_expires_at = 0001-01-01T00:00:00Z
  executor = "docker"
  [runners.custom_build_dir]
  [runners.cache]
    MaxUploadedArchiveSize = 0
    [runners.cache.s3]
    [runners.cache.gcs]
    [runners.cache.azure]
  [runners.docker]
    tls_verify = false
    image = "alpine:latest"
    privileged = false
    disable_entrypoint_overwrite = false
    oom_kill_disable = false
    disable_cache = false
    volumes = ["/cache"]
    shm_size = 0
    network_mtu = 0
```