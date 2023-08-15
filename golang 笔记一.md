# golang 笔记一

 

# golang开发环境搭建

## 下载 

Golang1.17.13 

	* windows [https://go.dev/dl/go1.17.13.windows-amd64.msi](https://go.dev/dl/go1.17.13.windows-amd64.msi)
	* MacOs [https://go.dev/dl/go1.17.13.darwin-amd64.pkg](https://go.dev/dl/go1.17.13.darwin-amd64.pkg)



## 设置环境变量

golang从1.11开始就已经使用go mod方式管理项目，所以对GOPATH依赖并不是很严重了。所以Mac版本的GOPATH我就没有去进行配置环境变量了。

### Mac版本设置

* 能够执行`go env`命令执行就可以了

    ![image-20230811214310963](/Users/yanweijian/Library/Application Support/typora-user-images/image-20230811214310963.png)

  

### windows版本设置

* 在进行golang msi安装的时候勾选到安装到系统环境变量中就可以在`cmd`中执行`go`相关命令
* 在系统环境变量中添加`GOPATH`环境变量，并将项目根目录加入到环境变量中即可



### go mod设置（主流管理方式）

* 创建项目目录（通过golang或者是vscode创建即可）
* 在项目根目录执行`go mod init <path>`进行初始化项目即可（golang会自动创建此目录）

![image-20230811215117171](/Users/yanweijian/Library/Application Support/typora-user-images/image-20230811215117171.png)

# golang运行第一段代码



## 使用golang创建第一个项目

在`golang`创建`awesomeProject`项目，并创建一个`main.go`的文件，main.go内容如下：

```go
package main

import "fmt"

func main(){
	fmt.Printf("Hello Go")
}
```

写完代码后通过idle运行代码即可返回`Hello Go`内容





