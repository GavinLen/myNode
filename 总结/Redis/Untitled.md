# zookeeper 监控
[TOC]

## 1. zkui
zkui 是一款`Java`语言开发的监控 zookeeper 的 web 项目，可以实现集群监控、增删改查操作等。
### 1.1 初始化环境

zkui 是`Java`开发并通过`Maven`构建的，因此在编译之前需要构建初始化环境。

### 1.2 生成 jar 包

通过 `git clone` 从 [Zkui Git](https://github.com/DeemOpen/zkui)下载源码，通过`mvn clean package`编译生成 jar。

```shell
> git clone https://github.com/DeemOpen/zkui.git
> mvn clean package
```

`maven`打包后生成了`zkui-2.0-SNAPSHOT.jar`和`zkui-2.0-SNAPSHOT-jar-with-dependencies.jar`两个文件，其中`zkui-2.0-SNAPSHOT-jar-with-dependencies.jar`才是我们需要的jar文件。

### 1.3 启动

在启动之前需要修改`config.cfg`中的启动端口、Zppkeeper 集群主机、登录账号与密码等。

#### a. 修改配置文件

修改配置文件`config.cfg`，如下内容：

```shell
#Server Port
serverPort=9090
#Comma seperated list of all the zookeeper servers
zkServer=c-128:2181,c-128:2181
```

#### b. 启动

通过`nohup java -jar zkui-2.0-SNAPSHOT-jar-with-dependencies.jar &`启动，然后访问`http://c-128:9090`即可访问监控应用。

## 2. zkdash

https://blog.csdn.net/lylclz/article/details/78633074