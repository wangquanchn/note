启动Jenkins镜像：

```shell
docker run \
  -u root \
  --rm \
  -d \
  --name docker_jenkins \
  -p 8081:8080 \
  -v /data/program/docker/volume/jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkinsci/blueocean
```



```shell
docker run \
  -d \
  -p 8082:80 \
  --name docker_gitlab \
  --restart always \
  -v /data/program/docker/volume/gitlab/config:/etc/gitlab \
  -v /data/program/docker/volume/gitlab/logs:/var/log/gitlab \
  -v /data/program/docker/volume/gitlab/data:/var/opt/gitlab \
  gitlab/gitlab-ce
```



# -d：后台运行

# -p：将容器内部端口向外映射

# --name：命名容器名称

# -v：将容器内数据文件夹或者日志、配置等文件夹挂载到宿主机指定目录



wget https://mirrors.tuna.tsinghua.edu.cn/jenkins/redhat-stable/jenkins-2.204.3-1.1.noarch.rpm

sudo yum install jenkins-2.204.3-1.1.noarch.rpm

### 修改jenkins_home、port

vim /etc/sysconfig/jenkins

JENKINS_HOME=xxx

JENKINS_POST=xxx



/etc/rc.d/init.d/jenkins

添加或修改jdk：candidates

新增前缀：--prefix=/jenkins



yum install fontconfig

systemctl start jenkins.service

### 修改默认镜像源

vim /var/lib/jenkins/hudson.model.UpdateCenter.xml

<?xml version='1.1' encoding='UTF-8'?>
<sites>
  <site>
    <id>default</id>
    <url>https://mirrors.tuna.tsinghua.edu.cn/jenkins/updates/update-center.json</url>
  </site>
</sites>

