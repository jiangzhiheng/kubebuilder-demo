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

### 3. 定义AppSpec 
```go
package v1beta1
// edit app_types.go
//...
type AppSpec struct {
	// INSERT ADDITIONAL SPEC FIELDS - desired state of cluster
	// Important: Run "make" to regenerate code after modifying this file

	// Foo is an example field of App. Edit app_types.go to remove/update
	EnableIngress 	bool 	`json:"enable_ingress,omitempty"`
	EnableService 	bool 	`json:"enable_service"`
	Replicas 		int32 	`json:"replicas"`
	Image 			string 	`json:"image"`
}
//...
```
运行`make manifests`生成crd定义

### 3. 创建webhook
```shell
kubebuilder create webhook --group ingress --version v1beta1 --kind App --defaulting  --programmatic-validation --conversion
```

## Controller-runtime 介绍