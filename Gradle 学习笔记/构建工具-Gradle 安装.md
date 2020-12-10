# 构建工具-Gradle 安装

[toc]

## 1. Gradle 简介

Gradle是源于Apache Ant和Apache Maven概念的项目自动化构建开源工具，它使用一种基于Groovy的特定领域语言(DSL)来声明项目设置，抛弃了基于XML的各种繁琐配置面向Java应用为主。当前其支持的语言暂时有Java、Groovy、Kotlin和Scala。

Gradle是一个基于JVM的构建工具，是一款通用灵活的构建工具，支持maven， Ivy仓库，支持传递性依赖管理，而不需要远程仓库或者是pom.xml和ivy.xml配置文件，基于Groovy，build脚本使用Groovy编写。

## 2. Gradle 下载

[Gradle官网地址](https://gradle.org/) 提供了两种方式的安装包，*Binary-only*与*Complete*，具体如下所示：

- [**Binary-only**](https://gradle.org/next-steps/?version=6.7&format=bin)

仅包含二进制，没有文档与资料。

- [**Complete**](https://gradle.org/next-steps/?version=6.7&format=all)

完成的包，提供了文档与资料。

## 3. Gradle 安装配置

### 3.1 安装

> 在开发中为了查看文档，因此安装的完成包:**gradle-x.y-all.zip**

解压安装包到需要的文件夹中。

```shell
> unzip gradle-6.7-all.zip

> ll
total 76
drwxr-xr-x 1 lianghongwei01 1049089     0 11月  5 11:12 bin/
drwxr-xr-x 1 lianghongwei01 1049089     0 11月  5 11:12 docs/
drwxr-xr-x 1 lianghongwei01 1049089     0 11月  6 15:24 init.d/
drwxr-xr-x 1 lianghongwei01 1049089     0 11月  5 11:12 lib/
-rw-r--r-- 1 lianghongwei01 1049089 23606  2月  1  1980 LICENSE
-rw-r--r-- 1 lianghongwei01 1049089   803  2月  1  1980 NOTICE
-rw-r--r-- 1 lianghongwei01 1049089   976  2月  1  1980 README
drwxr-xr-x 1 lianghongwei01 1049089     0  2月  1  1980 src/
```

### 3.2 配置

完成安装之后的需要配置环境变量与仓库相关信息。

#### 3.2.1 配置环境变量

- **配置 GRADLE_HOME**

![](img/2020-11-06_151835.png)

- **配置 path**

![](img/2020-11-06_152000.png)

#### 3.2.2 配置仓库信息

- **配置 GRADLE_USER_HOME**

![](img/2020-11-06_152306.png)

- **配置仓库源**

**Gradle**的安装目录中的*init.d*中存放的是 Gradle 的初始化脚本，其中的*readme.txt*中的内容如下：

> You can add .gradle init scripts to this directory. Each one is executed at the start of the build.
>
> 你可以添加 *.gradle*初始化脚本在这个目录下，

