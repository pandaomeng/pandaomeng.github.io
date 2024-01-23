# web 网络协议 - 学习笔记

以 TCP/IP 协议栈为依托，由上之下从应用层秩基础设施介绍协议

- 应用层： HTTP/1.1、websocket、HTTP/2.0
- 应用层的安全基础设施：TLS/SSL
- 传输层：TCP
- 网络层及数据链路层：IP层及以太网



涉及工具：

- chrome network 面板
- wireshark
- tcpdump



## HTTP 协议

Hypertext Transfer Protocol (HTTP)

> a **stateless** application-level **request/response** protocol that uses **extensible semantics** and **self-descriptive** message payloads for flexible interaction with network-based **hypertext information** systems
>
> (RFC7230 2014.6)

一种无状态的、应用层的、以请求/应答方式运行的协议，它使用可扩展的予以和自描述的消息格式，与基于网络的超文本信息系统灵活的互动。

### HTTP 协议格式

ABNF（扩充巴科斯-瑙尔范式）操作符

- 空白字符： 用来翻个定义中的各个元素
  - method SP request-target SP HTTP-version CRLF
- 选择 /：表示多个规则都是可供选择的规则
  - start-line = request-line / status-line
- 值范围 %c##-##
  - OCTAL = "0" / "1" / "2" / "3" / "4" / "5" / "6" / "7"  与 OCTAL = %x30-37 等价
- 序列组合()：将规则组合起来，视为单个元素
- 不定量重复 m*n
  - 元素表示零个或更多元素：*(header-field CRLF)
  - 1* 元素表示一个或更多元素，2*4元素表示两个至四个元素
- 可选序列[]:
  - [message-body]

![](https://images.pandaomeng.com/20210512233417.png)





