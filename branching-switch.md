# Branching: Switch

Like any other programming language out there, `switch` is a shorter and more concise way to `if/else` . In Go `switch` runs the first case that matches the conditional expression. 

Go only runs first case that matches the conditional expression and unlike other language `break` is not required, it is implicitely provided by Go.

In Go, cases need not be constants, it could be any value or conditional statement to be evaluated. Here is first glance at simplest `switch` statement

```go
package main
import (
	"fmt"
	"runtime"
)
func main() {
	fmt.Print("Go runs on ")
	os := runtime.GOOS
	switch os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		fmt.Printf("%s.\n", os)
	}
}
// Go runs on Linux
```

{% hint style="info" %}
Notice, that it has automatically ejected once case matched to 'linux'
{% endhint %}

#### Switch with shorthand expression

In addition to this `switch` also allows short statement to be evaluated before the case. Above example can be redone like following \(with short statement\)

```go
package main
import (
	"fmt"
	"runtime"
)
func main() {
	fmt.Print("Go runs on ")
	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		fmt.Printf("%s.\n", os)
	}
}
// Go runs on Linux
```

#### Switch without condition

Go allows `switch` without condition and when there are no conditions, first case evaluating to true would be evaluated. For illustration consider following

```go
package main
import (
	"fmt"
)
func main() {
	switch {
	case true:
		fmt.Println("I am first statement")
	case true:
		fmt.Println("I am second statement")
	default:
		fmt.Println("You reached the bottom")
	}
}
// I am first statement
```

Seen that, though second case condition is also true, but Go has exited as soon as first condition evaluated to true

#### Switch allows multiple expressions

Go allows, multiple expression in case seperated by comma. The way it works is that whichever expression evaluates to true, following block will be executed. You can imagine a hidden or there in place of comma. Here is an illustration

```go
package main
import "fmt"
import "time"
func main() {
    switch time.Now().Weekday() {
    case time.Saturday, time.Sunday:
        fmt.Println("Yay! it's weekend")
    default:
        fmt.Println("it's still weekday, :(")
    }
}
```

In above code snippet, whenever `time.Now().Weekday()` evaluates to either `time.Saturday` or `time.Sunday` , first block will be executed else the default

