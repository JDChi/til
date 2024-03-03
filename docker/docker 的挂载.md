# docker 的挂载类型

docker 支持三种挂载类型：
- Bind
  - --mount type=bind
  - 把宿主机的某个目录挂载到容器的指定目录下
  - e.g. `docker run --mount type=bind,source=/hello/html,destination=/usr/nginx/hmtl nginx:latest`
- Volume
  - --mount type=volume
  - 提升 docker 对不同存储介质的支撑能力
- tmpfs
  - --mount type=tmpfs
  - 用于在内存中读写临时数据