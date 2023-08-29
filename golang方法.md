# fmt

fmt打印输出的一个方法，类似于Python中的print()

```go
import "fmt"

func main() {
    var (
    	var name string
        var age int
        var isok bool
    )
    name = "leon"
    age = 18
    isok = true
    
    fmt.Print(name) //在终端中输出想要的内容
    fmt.Printf("age: %s",age) //格式化输出，%s是一个占位符，使用age去替换占位符。
    fmt.PrintLn(isok) //打印完指定内容之后在后面加上换行符
}
```

