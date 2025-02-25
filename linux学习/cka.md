1、权限控制 RBAC（权重4%）
设置配置环境：
[candidate@node-1] $ kubectl config use-context k8s
Context
为部署流水线创建一个新的 ClusterRole 并将其绑定到范围为特定的 namespace 的特定 ServiceAccount。
Task
创建一个名为 deployment-clusterrole 且仅允许创建以下资源类型的新 ClusterRole：
Deployment
StatefulSet
DaemonSet
在现有的 namespace app-team1 中创建一个名为 cicd-token 的新 ServiceAccount。
限于 namespace app-team1 中，将新的 ClusterRole deployment-clusterrole 绑定到新的 ServiceAccount cicd-token。

重点概念：ClusterRole 集群角色 ，ServiceAccount 服务账户（对应还有user账户）
详解：https://juejin.cn/post/7195038500087922744?from=search-suggest
![image](https://github.com/user-attachments/assets/2b34c89e-262d-40a1-90c9-666f93f6e407)

权限授予给clusterrole，绑定到serviceaccount上

