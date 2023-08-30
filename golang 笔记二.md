# 1. golang数据类型

## 1.1 整型

整型分为以下两个大类： 按长度分为：`int8`、`int16`、`int32`、`int64`对应的无符号整型：`uint8`、`uint16`、`uint32`、`uint64`

其中，`uint8`就是我们熟知的`byte`型，`int16`对应C语言中的`short`型，`int64`对应C语言中的`long`型。



## 1.2 浮点型

Go语言支持两种浮点型数：`float32`和`float64`。这两种浮点型数据格式遵循`IEEE 754`标准： `float32` 的浮点数的最大范围约为`3.4e38`，可以使用常量定义：`math.MaxFloat32`。 `float64` 的浮点数的最大范围约为 `1.8e308`，可以使用一个常量定义：`math.MaxFloat64`。



## 1.3 复数

```
complex64`和`complex128
```

复数有实部和虚部，`complex64`的实部和虚部为32位，`complex128`的实部和虚部为64位。



## 1.4 布尔型

Go语言中以`bool`类型进行声明布尔型数据，布尔型数据只有`true（真）`和`false（假）`两个值。

```
    注意：

    布尔类型变量的默认值为false。

    Go 语言中不允许将整型强制转换为布尔型.

    布尔型无法参与数值运算，也无法与其他类型进行转换。
```



## 1.5 字符串

Go语言中的字符串以原生数据类型出现，使用字符串就像使用其他原生数据类型`（int、bool、float32、float64 等）`一样。 Go 语言里的字符串的内部实现使用UTF-8编码。 <font color="red">字符串的值为双引号(")中的内容</font>，可以在Go语言的源码中直接添加非`ASCII`码字符，例如：

```go
s1 := "hello"
s2 := "你好"
```

### 1.5.1 字符串中的转义符

Go 语言的字符串常见转义符包含回车、换行、单双引号、制表符等，如下表所示。

| 转义 | 含义                               |
| ---- | ---------------------------------- |
| \r   | 回车符（返回行首）                 |
| \n   | 换行符（直接跳到下一行的同列位置） |
| \t   | 制表符                             |
| \'   | 单引号                             |
| \"   | 双引号                             |
| \    | 反斜杠                             |

### 1.5.2 多行字符串

Go语言中要定义一个多行字符串时，就必须使用`反引号`字符：

```
    s1 := `第一行
    第二行
    第三行
    `
    fmt.Println(s1)
```

反引号间换行将被作为字符串中的换行，但是所有的转义字符均无效，文本将会原样输出。

### 1.5.3 字符串的常用操作

| 方法                                | 介绍           |
| ----------------------------------- | -------------- |
| len(str)                            | 求长度         |
| +或fmt.Sprintf                      | 拼接字符串     |
| strings.Split                       | 分割           |
| strings.Contains                    | 判断是否包含   |
| strings.HasPrefix,strings.HasSuffix | 前缀/后缀判断  |
| strings.Index(),strings.LastIndex() | 子串出现的位置 |
| strings.Join(a[]string, sep string) | join操作       |

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	s1 := "hello"
	s2 := "你好"
	fmt.Printf("s1: %v\n", s1)
	fmt.Printf("s2: %v\n", s2)

	s3 := "D:\\bsm\\Navicat_CN"
	fmt.Printf("s3: %v", s3)

	// 多行字符串
	s4 := `
		晏伟健
		是大帅
		B
	`
	res := strings.Split(s3, "\\")
	fmt.Printf("res: %v\n", res)

	lens := len(s3)
	fmt.Println(lens)
	fmt.Println(strings.Index(s3, "CN"))

	s5 := "晏伟健"
	s6 := []rune(s5)
	s6[0] = '马'
	fmt.Println(s6)

	s7 := "y"
	s8 := 'y'

	fmt.Printf("s7: %v\ns8: %v", s7, s8)
}
```

