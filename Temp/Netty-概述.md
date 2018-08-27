# Netty 概述

[TOC]

> Netty is an asynchronous event-driven network application framework for rapid development of maintainable high performance protocol servers & clients.
>
> Netty是 一个异步事件驱动的网络应用程序框架， 用于快速开发可维护的高性能协议服务器和客户端。

> Netty is a NIO client server framework which enables quick and easy development of network applications such as protocol servers and clients. It greatly simplifies and streamlines network programming such as TCP and UDP socket server.
>
> Netty是一个NIO客户端服务器框架，可以快速和轻松地开发协议服务器和客户端等网络应用程序。它极大地简化并简化了TCP和UDP套接字服务器等网络编程。

![](D:\docs\myNote\images\netty.png)

### 特征

- **设计**
  - 各种传输类型的统一API，包括阻塞与非阻塞套接字。
  - 基于灵活且可扩展的事件模型，可以清晰分离关注点。
  - 高度可定制的线程模型，单线程、一个或多个线程池，如SEDA。
  - 真正的无连接数据报套接字支持（自3.1起）

- 性能
  - 高吞吐量，低延时。
  - 少的资源消耗。
  - 最小不必要的内存复制。
- 安全
  - 完整的 SSL/TLS 和 StartTLS 支持。

