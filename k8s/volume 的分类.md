# Volume 的分类

k8s 里 Volume 分为两类：
- 持久化的 PersistVolume
  - PersistVolume 独立于 Pod 存在
- 非持久化的普通 Volume
  - 普通 Volume 不是为了持久化，它的生命周期与 Pod 一致

