# CentOS--常用配置

[TOC]

## 1. 免密钥登录

```shell
ssh-keygen -t rsa （四个回车）
执行完这个命令后，会生成两个文件id_rsa（私钥）、id_rsa.pub（公钥）
将公钥拷贝到要免登陆的机器上
ssh-copy-id localhost
```

