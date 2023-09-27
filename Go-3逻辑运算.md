# 1. 条件判断if

条件可以理解成if语句。和其他的语言类似，通过判断条件是否为true或者是false在决定是否执行语句。

```go
// 可以省略表达式的括号 

if 布尔表达式 {
    // 在布尔表达式为true时执行
}

// 简单的if实例
package main
import "fmt"
n =: 1
if n == 1 {
    fmt.Printl(n)
}

// if..else if...else
package main
import "fmt"

n =: 1
x =: 2
if n != 1 {
    fmt.Printl(n)
} else if x != 2{
    fmt.Printl(x)
} else{
    fmt.Printl("xxxxx")
}
```



# 2. 条件判断switch

switch可以简单理解成shell中的case语句。

```go
package main

import "fmt"

func main () {
    var n int = 1
    
    swith n {
    case 1 :
        fmt.Printl("晏伟健太帅")
    case 2:
        fmt.Printl("晏伟健太shuai")
   	case 3:
        fmt.Printl("xxxxx")    
    default :
        fmt.Printl("晏伟健还是太帅")
    }
    
    // 使用下面的这一段也可以
    
    swith {
    case n == 1:
        fmt.Printl("晏伟健太帅")
    case n ==2:
        fmt.Printl("晏伟健xxxx")
    case n == 3:
        fmt.Printl("晏伟健asdf")
    default:
        fmt.Printl("晏伟健还是太帅")
    }
}

```



# 3. 循环语句for

go for支持三种循环方式，包括类似while的语法。

for循环的语法格式：

`for init; condition; post {}`

`for condition {}`

`for {}`

* init: 一般为赋值表达式，给控制变量赋初始值（n = 1）
* condition: 关系表达式或者是逻辑表达式
* post:  一般为赋值表达式，给控制变量增量或减量。

```go
var string s = "abc"
// 初始化两个变量i，n，它们的值分别是0和s的长度
for i, n := 0, len(s); i < n; i++ {
    printl(s[i])
}

// 第二种写法

s := "abc"
n := len(s)
for ; n > 3; n-- {
    fmt.Printl(s[n-1])
}

// 第三种写法

s := "abc"
n := len(s)
for n > 3 {
    fmt.Printl(s[n-1])
    n--
}

// for 死循环

for true {
    fmt.Printl("这是死循环")
}
```



# 4. 循环语句range

Go语言中可以使用for range遍历`数组`、`切片`、`字符串`、`map`及`通道`。通过for range遍历的返回值有以下规律：

1. 数组，切片，字符串返回索引和值。
2. map返回键和值
3. 通道高只返回通道内的值

```go
package main

import "fmt"

func main () {
    s := "Hello 晏伟健"
    for _,v := range s {
        // _：匿名变量，直接丢弃
        fmt.Printf("%c\n",v)
    }
}
```



# 5. 循环控制Goto、Break、Continue

Break、continue和Python中是一样的。

Goto可以理解成传送符。
