# 

[TOC]

出现的错误：

```shell
 max file descriptors [4096] for elasticsearch process is too low, increase to at least [65536]
```

- 原因分析

`elasticsearch`用户拥有的可创建文件描述的权限太低，至少需要65536。

- 解决方案

修改`/etc/security/limits.conf`，添加如下内容：

```shell
es hard nofile 65536
es soft nofile 65536
```

出现的错误：

```shell
[1]: max virtual memory areas vm.max_map_count [65530] is too low, increase to at least [262144]
```

- 原因分析



- 解决方案

修改`/etc/sysctl.conf`，添加如下内容，后执行`sysctl -p`。

```shell
vm.max_map_count=655360
```

