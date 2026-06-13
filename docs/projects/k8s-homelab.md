# Kubernetes Homelab

目标：搭建并长期维护一个家庭 Kubernetes/homelab 集群，覆盖 GPU 节点、边缘节点、存储、网络、监控和 GitOps。

参考项目：

- Kubernetes The Hard Way: https://github.com/kelseyhightower/kubernetes-the-hard-way
- k3s-ansible: https://github.com/k3s-io/k3s-ansible
- Flux CD: https://github.com/fluxcd/flux2
- pi-cluster: https://github.com/geerlingguy/pi-cluster

## Milestones

### M1: Inventory

记录：

- 节点型号
- CPU/RAM/GPU
- 磁盘
- 网络
- 电源
- 故障域

必须能解释：

- 哪些节点适合 control plane？
- 哪些节点适合 storage？
- GPU workload 的调度约束是什么？

### M2: The Hard Way Lab

先在虚拟机里手动搭一次：

- CA/certs
- etcd
- kube-apiserver
- controller-manager
- scheduler
- kubelet
- CNI

这一步不是为了生产使用，而是为了把 control plane 真正拆开看。

### M3: k3s Production-ish Cluster

实现：

- Ansible inventory
- k3s server/agent
- CNI
- ingress
- local-path 或 Longhorn
- node labels/taints

### M4: GitOps

实现：

- Flux bootstrap
- app manifests
- secrets strategy
- environment overlays
- rollback

Codex 任务：

```text
请审查我的 homelab GitOps 目录结构。
重点找 secret 泄漏、环境耦合、升级风险、灾难恢复缺口。
```

### M5: Observability And Recovery

实现：

- Prometheus
- Grafana
- Loki
- alert rules
- backup/restore drills

## Completion

完成时你应该能解释：Kubernetes 不是“装一个集群”，而是证书、网络、调度、存储、控制循环、声明式状态和故障恢复的组合。
