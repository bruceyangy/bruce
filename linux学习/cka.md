CKA真题：https://zhuanlan.zhihu.com/p/675819358

### 1.RBAC

简介：用户绑定角色，角色对应n个权限

为部署流水线创建一个新的 [ClusterRole](https://zhida.zhihu.com/search?content_id=238312036&content_type=Article&match_order=1&q=ClusterRole&zhida_source=entity) 并将其绑定到范围为特定的 namespace 的特定 [ServiceAccount](https://zhida.zhihu.com/search?content_id=238312036&content_type=Article&match_order=1&q=ServiceAccount&zhida_source=entity)。
**Task**
创建一个名为 deployment-clusterrole 且仅允许创建以下资源类型的新 ClusterRole：
Deployment
StatefulSet
DaemonSet
在现有的 namespace app-team1 中创建一个名为 cicd-token 的新 ServiceAccount。
限于 namespace app-team1 中，将新的 ClusterRole deployment-clusterrole 绑定到新的 ServiceAccount cicd-token。

详解：https://juejin.cn/post/7195038500087922744?from=search-suggest

```shell
#创建clusterrole并赋予创建deployments,daemonsets,statefulsets权限
kubectl create clusterrole deployment-clusterrole --verb=create --resource=deployments,daemonsets,statefulsets
#创建serveraccount并指定namespace
kubectl create serviceaccount cicd-token -n app-team1
#绑定
kubectl create rolebinding cicd-token --serviceaccount=app-team1:cicd-token --clusterrole=deployment-clusterrole -n app-team1
```

