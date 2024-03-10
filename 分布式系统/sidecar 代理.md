# sidecar 代理
内容来自《凤凰架构》

sidecar 代理的三个问题：
- 代理注入：sidecar 如何注入到应用程序中？
- 流量劫持：sidecar 如何劫持应用程序的通信流量？
- 可靠通信：sidecar 如何保证应用程序的通信可靠性？

## 代理注入
三种方式：
- 基座模式
  - 接入 sdk，有代码侵入性
- 注入模式
  - 手动注入
    - 修改 Pod 的配置文件
  - 自动注入
    - 设置 istio-injection=enabled 标签的 namespace，istio 会自动注入

[安装 Sidecar](https://istio.io/latest/zh/docs/setup/additional-setup/sidecar-injection/)

## 流量劫持
典型的方式是基于 iptables 进行数据转发。

istio 在注入 sidecar 代理后，除了生成封装 Envoy 的 istio-proxy 容器外，还会生成一个 initContainer 来自动修改容器的 iptables。

## 可靠通信
例如 Nginx 一类的传统代理程序，是使用静态配置文件来描述转发策略。

Envoy 则是通过将行为规则抽象成资源，然后提供相应的 API 来访问和访问这些资源。一方面让数据平面有了如何描述各种配置和策略的标准，也让控制平面和数据平面的交互有了标准接口。

