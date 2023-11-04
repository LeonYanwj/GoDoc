# 名词解释

如下是一个标准的k8s yaml文件：

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

* GV：`apiVersion`字段中的`apps`和`v1`，其中apps就是`GV`中的G。
* GVK：`kind`字段中的资源类型是Deployment。就是`GVK`中的K
* GVR：R就是`Resource`是kind的对象表示，存储的是kind的api对象的一个集合



# client-go

​	如果我们需要对kubernetes中的资源进行增删查改等，则需要通过操作api接口进行操作，我们不需要自己去调用各种api接口来实现，官方有开源的SDK来供我们使用，即client-go。

## 源代码结构解析

```
├── discovery                   # DsicoveryClient客户端,用于发现k8s所支持GVR。
├── dynamic                     # DynamicClient客户端, 用于访问k8s Resources，也可以访问CRD。
├── informers                   # k8s中各种Resources的Informer机制的实现。
├── kubernetes                  # 对RestClient进行了封装，定义多种Client的客户端集合，俗称clientset。
├── listers                     # 提供对Resources的获取功能。对于Get()和List()而言，listers提供给二者的数据都是从缓存中读取的。
├── pkg
├── plugin                      # 提供第三方插件。
├── scale                       # 提供 ScaleClient 客户端，用于扩容或缩容 Deployment, Replicaset, Replication Controller 等资源对象。
├── tools                       # 实现client查询和缓存机制，以及定义诸如SharedInformer、Reflector、DealtFIFO和Indexer等常用工具。
├── transport                   # 提供安全的TCP连接，支持 HTTP Stream，某些操作需要在客户端和容器之间传输二进制流，例如 exec，attach 等操作。
└── util                        # 提供诸如WorkQueue、Certificate等常用方法。
```



client-go提供四种客户端对象来和apiserver进行交互：

```
1: RESTClient：这是最基础的客户端对象，仅对HTTPRequest进行了封装，实现RESTFul风格API，这个对象的使用并不方便，因为很多参数都要使用者来设置，于是client-go基于RESTClient又实现了三种新的客户端对象；
2: ClientSet：把Resource和Version也封装成方法了，一个资源是一个客户端，多个资源就对应了多个客户端，所以ClientSet就是多个客户端的集合了，不过ClientSet只能访问内置资源，访问不了自定义资源；
3: DynamicClient：是一种动态客户端，它可以动态的指定资源的组，版本和资源。因此它可以对任意 K8S 资源进行 RESTful 操作，包括自定义资源。它封装了 RESTClient。所以同样提供 RESTClient 的各种方法。该类型的官方例子:https://github.com/kubernetes/client-go/tree/master/examples/dynamic-create-update-delete-deployment。
4: DiscoveryClient：用于发现kubernetes的API Server支持的Group、Version、Resources等信息；
```



scheme

```
当我们和apiserver通信操作资源时，需要根据资源对象类型的 Group、Version、Kind 以及规范定义、编解码等内容构成 Scheme 类型，然后 Clientset 对象就可以来访问和操作这些资源类型了，Scheme 的定义主要在 api 子项目之中，源码仓库，被同步到 Kubernetes 源码的 staging/src/k8s.io/api 下。

tree staging/src/k8s.io/api/apps/v1
staging/src/k8s.io/api/apps/v1
├── BUILD
├── doc.go
├── generated.pb.go
├── generated.proto
├── register.go
├── types.go                            
├── types_swagger_doc_generated.go
└── zz_generated.deepcopy.go
```





























