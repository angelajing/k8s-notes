参考文档：<br>
https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/

### Labels & Selectors

- 示例
```
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  # Unique key of the Deployment instance
  name: deployment-example
spec:
  # 3 Pods should exist at all times.
  replicas: 3
  template:
    metadata:
      labels:
        # Apply this label to pods and default
        # the Deployment label selector to this value
        app: nginx
    spec:
      containers:
      - name: nginx
        # Run this image
        image: nginx:1.10
```
- 操作
```
$ kubectl get pods --show-labels
$ kubectl get pods --selector owner=michael
$ kubectl get pods -l owner=michael
$ kubectl get pods -l 'env in (production, development), tier in (frontend)'
$ kubectl get pods -l 'tier, tier notin (frontend, backend)'
```

### Field Selectors

- 操作
```
$ kubectl get pods --field-selector metadata.name=my-service
$ kubectl get pods --fileld-selector metadata.namespace != default
$ kubectl get pods --field-selector status.phase != Running, spec.restartPolicy=Always
$ kubectl get statefulsets,services --all-namespaces --field-selector metadata.namespace!=default
```

================= Q&A ====================

*1.哪些信息可以使用labels来记录？*

- 应用程序的名称（app.kubernetes.io/name）：mysql
- 用于唯一确定应用实例的名称（app.kubernetes.io/instance）：wordpress-abcxzy
- 应用程序的当前版本（app.kubernetes.io/version）：5.7.21
- 运行环境（app.kubernetes.io/environment）：dev, pre, test, prod
- 架构中的组件（app.kubernetes.io/component）：database
- 此级别的更高级别应用程序的名称（app.kubernetes.io/part-of）：wordpress
- 用于管理应用程序的工具（app.kubernetes.io/managed-by）：helm
- release：stable
- region：jp-tokyo