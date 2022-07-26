## Kubebuilder 使用
### 1.初始化
```shell
kubebuilder init --domain jzh.tech
# --domain string     domain for groups (default "my.domain")
```

### 2.创建api
```shell
kubebuilder create api --group ingress --version v1beta1 --kind App
```

## Controller-runtime 介绍