# Constants

Constants in Go are declared similar to variables but with `const` keyword. Constant in Go can appear anywhere variable can appear and does not have shorthand like var has. The simplest way to define a string constant would be 

```go
const str = "Hey, I am defined as constant"
```

Yes, I know what you may be thinking, should the constant name not be all capital? No, in Go, its not mandatory, constant can be all capital, came cased or usaul snake cased. There sre no such specific guidelines on how constants should be named

But for the sake of consistancy, I would suggest that one should use camel case while naming constants. But how does constants differ from variables in Go? In Go, like any other language constants can not be reassigned. To test this hypothesis, lets run following code in Go Playground.

```go
package main
import "fmt"
const Pi = 3.14
func main() {
	const World = "世界"
	fmt.Println("Hello", World)
	fmt.Println("Happy", Pi, "Day")
	World = "World"
}
```

The above code, when executed would error. Because constants can not be reassiged

```go
./prog.go:8:8: cannot assign to World

Go build failed.
```

All set, right? :\) No

In Go, a numeric constant has no type, until its given one. One need to force typecast const to have it its type, like following

```go
const Big = 1 << 60
fmt.Println(int64(Big))
// => 1152921504606846976
```

{% hint style="info" %}
In Go, a numeric constant has no type, until its given one.
{% endhint %}

