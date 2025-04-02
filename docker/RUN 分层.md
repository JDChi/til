# RUN 分层

### 1. 分层机制

Docker 镜像是由多个层组成的，每个层代表一个 `RUN` 指令、`COPY` 指令、`ADD` 指令等的操作结果。这些层是只读的，并且可以被多个镜像共享，从而提高存储效率和构建速度。

### 2. `RUN` 指令的分层

每个 `RUN` 指令都会创建一个新的层。例如：

```dockerfile
RUN apt-get update
RUN apt-get install -y some-package
RUN rm -rf /var/lib/apt/lists/*
```


上述 Dockerfile 会创建三个层：
1. 第一层：执行 `apt-get update`。
2. 第二层：执行 `apt-get install -y some-package`。
3. 第三层：执行 `rm -rf /var/lib/apt/lists/*`。

### 3. 分层的影响

#### 3.1 构建速度

Docker 会缓存每个 `RUN` 指令的结果。如果 `RUN` 指令的内容没有变化，Docker 可以直接使用缓存的层，从而加快构建速度。但是，如果 `RUN` 指令的内容发生变化，Docker 需要重新执行该指令并创建新的层，这会减慢构建速度。

例如：

```dockerfile
RUN apt-get update && \
    apt-get install -y some-package && \
    rm -rf /var/lib/apt/lists/*
```


将上述三个 `RUN` 指令合并为一个，可以减少层的数量，并且如果 `some-package` 没有变化，Docker 可以直接使用缓存的层。

#### 3.2 镜像大小

虽然每个 `RUN` 指令都会创建一个新的层，但这些层是只读的，并且可以被多个镜像共享。然而，如果 `RUN` 指令中创建了大量不必要的文件或数据，这些文件和数据会被包含在层中，从而增加镜像的大小。

例如：

```dockerfile
RUN apt-get update && \
    apt-get install -y some-package && \
    rm -rf /var/lib/apt/lists/*
```


在这个例子中，`rm -rf /var/lib/apt/lists/*` 命令用于清理 `apt-get` 的缓存，从而减小镜像的大小。

### 4. 优化建议

#### 4.1 合并 `RUN` 指令

尽量将多个 `RUN` 指令合并为一个，以减少层的数量。例如：

```dockerfile
RUN apt-get update && \
    apt-get install -y some-package && \
    rm -rf /var/lib/apt/lists/*
```


#### 4.2 清理不必要的文件

在每个 `RUN` 指令中清理不必要的文件，以减小镜像的大小。例如：

```dockerfile
RUN apt-get update && \
    apt-get install -y some-package && \
    rm -rf /var/lib/apt/lists/*
```


#### 4.3 使用 `.dockerignore`

使用 `.dockerignore` 文件来排除不需要复制到镜像中的文件和目录，以减少中间镜像的大小。例如，创建一个 `.dockerignore` 文件：

```
*.log
__pycache__/
```


这会排除所有 `.log` 文件和 `__pycache__` 目录。
