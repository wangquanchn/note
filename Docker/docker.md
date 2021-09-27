### 卸载旧版本

```shell
sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

#### 设置存储库

安装`yum-utils`软件包（提供`yum-config-manager` 实用程序）并设置**稳定的**存储库。

```shell
sudo yum install -y yum-utils

sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

#### 安装DOCKER引擎

1. 安装*最新版本*的Docker Engine和容器，或者转到下一步安装特定版本：

```shell
sudo yum install docker-ce docker-ce-cli containerd.io
```

3. 启动Docker。

```shell
sudo systemctl start docker
```

4. 通过运行`hello-world` 映像来验证是否正确安装了Docker Engine 。

```shell
sudo docker run hello-world
```











## Docker命令

进入容器

```shell
docker exec -it {容器名} /bin/bash
```



### Docker Library

在这里能找到大多数官方image的Dockerfile

`https://github.com/docker-library`

