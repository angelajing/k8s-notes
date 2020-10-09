参考文档：<br>
https://kubernetes.io/docs/concepts/overview/working-with-objects/names/#names

### Names

- 示例
```
apiVersion: v1
kind: Pod
metadata:
  name: nginx-demo
spec:
  containers:
  - name: nginx
    image: nginx:1.7.9
    ports:
    - containerPort: 80
```