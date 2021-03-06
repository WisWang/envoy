术语
===========

在深入研究主架构文档之前本文介绍一些定义。部分定义在行业中略有争议，但是在整个文档和代码库中，Envoy 就是这么使用的，所以，我们就这样定义吧。

**主机（Host）**: 能够进行网络通信的实体（如移动设备、服务器上的应用程序）。在此文档中，主机是逻辑网络应用程序。一块物理硬件上可能运行有多个主机，只要它们是可以独立寻址的。

**下游（Downstream）**: 下游主机连接到 Envoy，发送请求并接收响应。

**上游（Upstream）**: 上游主机接收来自 Envoy 的连接和请求，并返回响应。

**监听器（Listener）**: 监听器是被命名的网络地址（例如，端口、Unix 域套接字等)，它可以被下游客户端连接。Envoy 给下游主机暴露一个或多个监听器来连接。

**集群（Cluster）**: 集群是指 Envoy 连接到的逻辑上相同的一组上游主机。Envoy 通过 :ref:`服务发现 <arch_overview_service_discovery>` 来发现集群的成员。可以选择通过 :ref:`主动健康检查 <arch_overview_health_checking>` 来确定集群成员的健康状态。Envoy 通过 :ref:`负载均衡策略 <arch_overview_load_balancing>` 来决定将请求路由到哪个集群成员。

**网格（Mesh）**: 一组协调提供一致网络拓扑的主机。在本文档中，“Envoy 网格”是一组 Envoy 代理，它们构成了分布式系统的消息传递基础，这个分布式系统由很多不同服务和应用程序平台组成。

**运行时配置（Runtime configuration）**:  外置实时配置系统和 Envoy 一起部署。可以更改配置设置来影响运行，而无需重启 Envoy 或更改主要配置。
