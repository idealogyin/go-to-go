# Recursion

A recursive function is a function that call itself unless it reaches matches a certain condition. 

{% hint style="warning" %}
A breakpoint for recursive function is necessary otherwise it could keep calling itself for indefinite times, growing heap and stack that could be detrimental to program's performance
{% endhint %}

We are going to implement a classic example to calculate factorial or given number using Go, with recursive methodology

```go
package main
import "fmt"
func factorial(n int) int {
    if n == 0 {
        return 1
    }
    return n * factorial(n-1)
}
func main() {
    fmt.Println(factorial(5))
}
// 120
```

