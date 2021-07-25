---
title: "Gin_Notes"
date: 2021-04-14T14:47:18+08:00
draft: false
tags: ["Golang", "Web", "Go Web", "Gin", "Gorm"]
categories: ["Go Web Develop"]
---

# About Web

- Web 是基于 HTTP/HTTPS 协议进行交互的应用网络。

- Web 就是通过使用浏览器/App 访问的各种资源。

- C/S 架构：

  1. request(请求)
  2. response(响应)

- HTTP 轮询与 WebSocket

  - HTTP 与 WebSocket 轮询的区别：
  - HTTP 缺点：通信只能由客户端发起，服务器数据变化时不能主动通知客户端，只能客户端(不断轮询访问)每隔一段时间向服务器发起请求，若服务端数据没有发生变化时，很多次轮询都是无用的，这样资源都被浪费掉
  - WebSocket 优点：服务端可以主动向客户端推送消息，客户端可以主动向服务器端发送消息。它们是双向平等的通信
