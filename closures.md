# Closures

> In [programming languages](https://en.wikipedia.org/wiki/Programming_language), a **closure**, also **lexical closure** or **function closure**, is a technique for implementing [lexically scoped](https://en.wikipedia.org/wiki/Lexically_scoped) [name binding](https://en.wikipedia.org/wiki/Name_binding) in a language with [first-class functions](https://en.wikipedia.org/wiki/First-class_function). [Operationally](https://en.wikipedia.org/wiki/Operational_semantics), a closure is a [record](https://en.wikipedia.org/wiki/Record_%28computer_science%29) storing a [function](https://en.wikipedia.org/wiki/Function_%28computer_science%29) together with an environment.
>
> Wikepedia.org

For a function to be clousers, at least; these following conditions should be met 

* Record storing function \(retains copy of env/scope it is defined in\)
* Can be passed around as a variable 
* Execution of clousers can be differed

Let see, if we can implement a clouser in Go. Dive in

```go
func Seq() func() int {
    i := 0
    return func() int {
        i += 1
        return i
    }
}
```

Let's look at the function, illustrated above; closely. we have defined a function `Seq()` that takes no argument and returns a value of type `func()` that in turn has a return value of type `int` 

Now lets see it in action

```go
mySeq := Seq()
mySeq()  // 1
mySeq()  // 2
mySeq()  // 3
mySeq = Seq()
mySeq()  // 1
```

Did you see that ? 

**Record Storing function**: So when we call `Seq()` for first time, it returns a function, with value of `i` encapsulated with it. So our variable `mySeq` holds a function and when we call it for first time, it increments the value of `i` to 1 and returns one, on subsequent call, it increments value of `i` on previously returned value, that prooves that it is keeping record of `i` .

**Can be passed around as a variable**: On our first call we assigned return value of function `Seq()` to local variable `mySeq` and it can be passed around freely, so it does satisfy our second condition

**Execution of clousers can be differed:** That also holds tru in this case, our variable holding function can be passed around; used with differ keyword and can also be passed to other context and executed later

