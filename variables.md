# Variables

Go is strictly typed laguage, meaning that one has to define type of the value a variable can hold. In Go, variables needs to be explicitely declared and further used by compiler to infer types and typechecking.

Let's look at an example

```go
package main
import "fmt"
func main() {
    var str = "This would be auto infered as string"
    fmt.Println(str)
    // multiple variable declaration at once 
    var one, two int = 1, 2
    fmt.Println(one, two)
    // Again type will be inferred here on first initialization
    var isHappy = true
    fmt.Println(isHappy)
    // variable is declared but not initialized
    var willHold int
    fmt.Println(willHold)
    // shorthand for declaration as well as initialization
    fruit := "oranges"
    fmt.Println(fruit)
}
```

To try the above example, I would prefer to use [Go playground](https://play.golang.org/), since these are small example and Go playground is perfect example. Let go and put out code in Go Playground and hit 'Run'. Here is the output

```bash
This would be auto infered as string
1 2
true
0
oranges
```

Now lets examine, what we did line by line. At line\#4, we declared a variable while initializing it to string, but we did not mention type. Whe type is not mentioned while declaration and initialization, Go will automatically infer type of that variable by type of the value being assigned. So in our case `var str` will be of type `string` 

But Go will complain, when a variable is declared but not assigned without type declaration. Let's remove the assignment and run program again, what does one see? Obviously an error

```go
var str
```

```go
./prog.go:4:12: syntax error: unexpected newline, expecting type
```

It complains regarding type of var str is not defined, because Go could not infer type in absence of assignment, so it needs type to be declared explicitly when variable is not assigned any value

When variable is declared but not assigned, then go will by default assign zero value for that type. So for string type zero value is bank string `''` , for type int its `0` 

Similarly Go allows one to declare multiple variable, multiple assignment at same time in one line, see line\#7

```go
var one, two int = 1, 2
```

Here we declared variable `one` and `two`  as int and assigned 1 and 2 to them. On Line\#10, Go again auto infers type by value it is being assigned. But what about Line\#16?, one asks.

This `:=` is shorthand for variable declaration and assignment, this is equal to 

```go
var isHappy = true
```

