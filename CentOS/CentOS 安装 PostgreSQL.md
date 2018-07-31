# CentOS - 安装 PostgreSQL

[TOC]

## 1. 安装 PostgreSQL

### 1.1 下载并安装

### 1.2 创建配置文件

### 1.3 启动并测试

```shell
# 初始化
> ./bin/initdb -E utf8 -D /opt/postgresql/data/db

# 启动
>./bin/postgres -D /opt/postgresql/data/db > /opt/postgresql/data/logs/postgres.log &

# 关闭
> 
```





### 1.4 常用的配置

## 2. 配置开启启动脚本 

## 备注

