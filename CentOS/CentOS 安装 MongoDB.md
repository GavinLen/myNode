# CentOS - 安装 MongoDB

[TOC]

## 1. 安装 MongoDB

### 1.1 下载并安装

下载`node-v10.7.0-linux-x64.tar.xz`，并加压到指定位置，如`/opt/mongodb`，创建数据库路径与日志路径即可完成安装。

### 1.2 创建配置文件

```shell
> vim mongodb.conf
# 设置数据文件的存放目录
dbpath=/opt/mongodb/data/db
# 设置日志文件的存放目录及其日志文件名
logpath=/opt/mongodb/data/logs/mongodb.log
# 设置 pid 文件的存放目录
# pidfilepath=/opt/mongodb/mongodb-4.0.0
# 设置端口号（默认的端口号是 27017）
port=27017
# 设置为以守护进程的方式运行，即在后台运行
fork=true
# 绑定IP
bind_ip=0.0.0.0
# 日志文件追加写入
logappend=true
```

### 1.3 启动并测试

```shell
# 启动 MongoDB
> ./bin/mongod -f mongodb.conf
# 连接 MongoDB
> mongo 192.168.1.200:27017/test -u user -p password
```

### 1.4 常用的配置

```shell
--quiet # 安静输出
--port arg  # 指定服务端口号，默认端口27017
--bind_ip arg   # 绑定服务IP，若绑定127.0.0.1，则只能本机访问，不指定默认本地所有IP
--logpath arg   # 指定MongoDB日志文件，注意是指定文件不是目录
--logappend # 使用追加的方式写日志
--pidfilepath arg   # PID File 的完整路径，如果没有设置，则没有PID文件
--keyFile arg   # 集群的私钥的完整路径，只对于Replica Set 架构有效
--unixSocketPrefix arg  # UNIX域套接字替代目录,(默认为 /tmp)
--fork  # 以守护进程的方式运行MongoDB，创建服务器进程
--auth  # 启用验证
--cpu   # 定期显示CPU的CPU利用率和iowait
--dbpath arg    # 指定数据库路径
--diaglog arg   # diaglog选项 0=off 1=W 2=R 3=both 7=W+some reads
--directoryperdb    # 设置每个数据库将被保存在一个单独的目录
--journal   # 启用日志选项，MongoDB的数据操作将会写入到journal文件夹的文件里
--journalOptions arg    # 启用日志诊断选项
--ipv6  # 启用IPv6选项
--jsonp # 允许JSONP形式通过HTTP访问（有安全影响）
--maxConns arg  # 最大同时连接数 默认2000
--noauth    # 不启用验证
--nohttpinterface   # 关闭http接口，默认关闭27018端口访问
--noprealloc    # 禁用数据文件预分配(往往影响性能)
--noscripting   # 禁用脚本引擎
--notablescan   # 不允许表扫描
--nounixsocket  # 禁用Unix套接字监听
--nssize arg (=16)  # 设置信数据库.ns文件大小(MB)
--objcheck  # 在收到客户数据,检查的有效性，
--profile arg   # 档案参数 0=off 1=slow, 2=all
--quota # 限制每个数据库的文件数，设置默认为8
--quotaFiles arg    # number of files allower per db, requires --quota
--rest  # 开启简单的rest API
--repair    # 修复所有数据库run repair on all dbs
--repairpath arg    # 修复库生成的文件的目录,默认为目录名称dbpath
--slowms arg (=100) # value of slow for profile and console log
--smallfiles    # 使用较小的默认文件
--syncdelay arg (=60)   # 数据写入磁盘的时间秒数(0=never,不推荐)
--sysinfo   # 打印一些诊断系统信息
--upgrade   # 如果需要升级数据库
```



## 2. 配置开启启动脚本

### 2.1 创建脚本文件

```shell
> vim /etc/init.d/mongodb
```

### 2.2 编写 shell 脚本

```shell
#!/bin/bash
# chkconfig: - 85 15
#author:gavinlen
name=mongod
path_bin=/opt/mongodb/mongodb-4.0.0
path=/opt/mongodb
case "$1" in
  start)
    ${path_bin}/bin/mongod -f ${path_bin}/mongodb.conf --logappend --fork
    if [ $? -eq 0 ];then
      echo "${name}启动成功..."
    else
      echo "${name}启动失败..."
    fi
  ;;
  stop)
    if [ $(ps -ef|grep "mongod" |grep "fork"|awk {'print $2'}) -gt 0 ];then
      kill `ps -ef|grep "mongod" |grep "fork"|awk {'print $2'}`
      if [ $? -eq 0 ];then
        echo "${name}停止成功"
      else
        echo "${name}停止失败"
      fi
    else
      echo "${name}进程已经停止"
    fi
  ;;
  restart)
    if [ $(ps -ef|grep "mongod" |grep "fork"|awk {'print $2'}) -gt 0 ];then
      kill `ps -ef|grep "mongod" |grep "fork"|awk {'print $2'}`
      if [ $? -eq 0 ];then
        echo "${name}停止成功"
      else
        echo "${name}停止失败"
      fi
    else
      echo "${name}进程已经停止"
    fi
    echo "${name}启动中..."
    sleep 3s
    ${path_bin}/bin/mongod -f ${path_bin}/mongodb.conf --logappend --fork
    if [ $? -eq 0 ];then
      echo "${name}重启成功"
    else
      echo "${name}重启失败"
    fi
   ;;
   *)
    echo "${name}|start|stop|restart"
   ;;
esac
```

### 2.3 加入系统服务

```shell
> cd /etc/init.d/
# 设置执行权限
> chmod a+x mongodb
# 加入系统服务
> chkconfig --add mongodb
# 开机服务自启
> chkconfig mongodb on
# 重启系统生效
> shutdown -r now
```

### 2.4 测试脚本

```shell
#开启
> service mongodb start
#停止
> service mongodb stop
#重启
> service mongodb restart
```



## 备注

