参考文档：<br>
https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/

### Annotations

- 示例
```
apiVersion: v1
kind: Pod
metadata:
  name: annotations-demo
  annotations:
    imageregistry: "https://hub.docker.com/"
spec:
  containers:
  - name: nginx
    image: nginx:1.7.9
    ports:
    - containerPort: 80
```

================= Q&A ====================

*1.哪些信息可以使用annotations来记录？*
- Fields managed by a declarative configuration layer. Attaching these fields as annotations distinguishes them from default values set by clients or servers, and from auto-generated fields and fields set by auto-sizing or auto-scaling systems.
- Build, release, or image information like timestamps, release IDs, git branch, PR numbers, image hashes, and registry address.
- Pointers to logging, monitoring, analytics, or audit repositories.
- Client library or tool information that can be used for debugging purposes: for example, name, version, and build information.
- User or tool/system provenance information, such as URLs of related objects from other ecosystem components.
- Lightweight rollout tool metadata: for example, config or checkpoints.
- Phone or pager numbers of persons responsible, or directory entries that specify where that information can be found, such as a team web site.
- Directives from the end-user to the implementations to modify behavior or engage non-standard features.

===== 阿里云课堂 =====
- service.beta.kubernetes.io/alicloud-loadbalancer-cert-id: CA证书
- nginx.ingress.kubernetes.io/service-weigth:"new-nginx:20,old-nginx:60"
- kubectl.kubernetes.io/last-applied-configuration: yaml文件的json格式