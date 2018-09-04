# Redis 概述

[TOC]

## 1. Redis 简介



## 2. Redis 安装

```shell
> cd redis
> make
> make install PREFIX=/opt/redis/
```



Redis 安装完成后，`/bin`中常用的命令。

| 可执行文件       | 作用                            |
| :--------------- | ------------------------------- |
| redis-server     | 启动 Redis                      |
| redis-cli        | Redis 的客户端连接工具          |
| redis-benchmark  | 基准测试工具                    |
| redis-check-aof  | AOF持久化文件检测工具和修复工具 |
| redis-check-dump | RDB持久化文件检测工具和修复工具 |
| redis-sentinel   | 启动redis-sentinel              |

https://www.cnblogs.com/kongzhongqijing/p/6867960.html == Redis 命令

客户端连接 Redis 出现中文乱码

> redis-cli --raw 可以避免乱码

## 3. Redis 