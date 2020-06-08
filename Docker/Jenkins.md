ssh传jdk

```shell
# scp [可选参数] file_source file_target 

mkdir -p /data/program/java

scp /data/program/java/jdk-11.0.6_linux-x64_bin.tar.gz root@101.133.217.220:/data/program/java/jdk-11.0.6_linux-x64_bin.tar.gz

tar -zxvf jdk-11.0.6_linux-x64_bin.tar.gz



vim /etc/profile

export JAVA_HOME=/data/program//jdk-11.0.6
export JRE_HOME=${JAVA_HOME}/jre
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib
export PATH=${JAVA_HOME}/bin:$PATH

source /etc/profile



ln -s /data/program/java/jdk-11.0.6/bin/java /usr/bin/java
ln -s /data/program/java/jdk-11.0.6/bin/javac /usr/bin/javac
```



## 下载rpm包

```shell
mkdir -p /data/program/jenkins
cd /data/program/jenkins
wget https://mirrors.tuna.tsinghua.edu.cn/jenkins/redhat-stable/jenkins-2.204.3-1.1.noarch.rpm
```

安装：

```shell
sudo yum install jenkins-2.204.3-1.1.noarch.rpm
```

编辑配置：

```shell
vim /etc/sysconfig/jenkins
```

修改配置：

```
JENKINS_HOME="/data/program/jenkins/jenkins_home"
JENKINS_PORT="8081"
```

编辑配置：

```shell
/etc/rc.d/init.d/jenkins

# 添加或修改jdk：candidates
candidates="
/data/program/java/jdk-11.0.6/bin/java

# 新增前缀：--prefix=/jenkins
PARAMS="--logfile=/var/log/jenkins/jenkins.log --webroot=/var/cache/jenkins/war --daemon --prefix=/jenkins"
```

安装字体库:

```
yum install fontconfig
```

重载配置

```shell
mkdir -p /data/program/jenkins/jenkins_home
chmod -R 777 /data/program/jenkins/jenkins_home
systemctl daemon-reload
```

启动服务

```
systemctl start jenkins.service
```



nginx配置：

```conf
        location /jenkins/ {
            proxy_pass   http://127.0.0.1:8081/jenkins/;

            proxy_set_header Host $http_host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-Proto $scheme;
        }
```



### 修改默认镜像源

```
vim /var/lib/jenkins/hudson.model.UpdateCenter.xml
```

```xml
<?xml version='1.1' encoding='UTF-8'?>
<sites>
  <site>
    <id>default</id>
    <url>https://mirrors.tuna.tsinghua.edu.cn/jenkins/updates/update-center.json</url>
  </site>
</sites>
```



```shell
yum install -y unzip zip
```



### Maven

```shell
mkdir -p /data/program/maven
cd /data/program/maven

rz [文件]
unzip apache-maven-3.6.3-bin.zip

vi /etc/profile

MAVEN_HOME=/data/program/maven/apache-maven-3.6.3
export PATH=${MAVEN_HOME}/bin:${PATH}

source /etc/profile

ln -s /data/program/maven/apache-maven-3.6.3/bin/mvn /usr/bin/mvn

mkdir -p /data/program/maven/repository
chmod -R 777 /data/program/maven/repository


<localRepository>/data/program/maven/repository</localRepository>
<mirror>
     <id>alimaven</id>
     <name>aliyun maven</name>
     <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
     <mirrorOf>central</mirrorOf>
</mirror>
```



### Node

```shell
mkdir -p /data/program/node

scp /data/program/node/node-v14.2.0-linux-x64.tar.xz root@101.133.217.220:/data/program/node/node-v14.2.0-linux-x64.tar.xz

tar xf node-v14.2.0-linux-x64.tar.xz

cd node-v14.2.0-linux-x64

ln -s /data/program/node/node-v14.2.0-linux-x64/bin/npm /usr/bin/
ln -s /data/program/node/node-v14.2.0-linux-x64/bin/node /usr/bin/
```





把当前用户加入docker用户组

```
gpasswd -a ${USER} docker
```

重启docker,jenkins

```
systemctl restart docker
systemctl restart jenkins
```

更新用户组

```
newgrp docker 
```





cat /etc/passwd 可以查看所有用户的列表

cat /etc/group 查看用户组





```shell
ssh-keygen -t rsa -C "youremail@example.com"
```

