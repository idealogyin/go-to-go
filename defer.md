# Defer

In Go, a defer statement is similar to `final` or `ensure` in other programming language out there. It simply used for a cleanup for a function and most programming languages guarantee its execution at the end of function call or even when there are errors.

This can be used where we need to do some cleanup, like unsubscribe from a channel or close database connection etc.

Consider following simple example 

```go
package main
import "fmt"
func main() {
	defer fmt.Println("Go")
	fmt.Println("Hello")
}
// Hello
// Go
```

As we can deduce from example above `defer` gets called after the callee function is done returning. However, arguments for defer are evaluated at the time of declaration.

### Stacking Defer

Defer functions are stacked in a function stack, so in Go having multiple defer per function is allowed. Since `defer` are stacked so calls to it would behave like LIFO \(last in- first out\)

```go
package main
import "fmt"
func main() {
	for i := 0; i < 10; i++ {
		defer fmt.Println("Calling: ", i)
	}
	fmt.Println("Done")
}
// Done
// Calling:  9
// Calling:  8
// Calling:  7
// Calling:  6
// Calling:  5
// Calling:  4
// Calling:  3
// Calling:  2
// Calling:  1
// Calling:  0
```

So now it should be clear that out main function hash first stacked the defer calls to stack and made value of variable `i` available to defer. Once `main` has returned Go, started popping defer out of stack and executed them one by one

