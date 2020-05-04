# Errors & Panic

{% hint style="warning" %}
This page is under active revision, content may be updated without notice
{% endhint %}

In Go it is idiomatic to communicate errors explicitly, as separate return value. This contrasts with the exceptions used in languages like Java and Ruby. That meaning that Go leaves implementing error for programmer. Go implements error type and this would work similar to other primitive types.

In Go, programmer can create and error by calling `error.New` with a string passed to it as an error message. Consider the example bwlo

```go
func testError(a int) (int, error) {
  if a < 0 {
    return -1, errors.New("Negative number")
  }
  return a + 1, nil
}
```

`errors.New` constructs a basic error with a message, nil as second argument means no errors. Make a thumb rule to return error as last return value. 

{% hint style="warning" %}
**Note:** Some of you may have noticed weird return type compatibility in example above. But in Go, `nil` is considered of type error and hence they are compatible. Though it is still sounding weird to me :\)
{% endhint %}

Go allows one to define custom error method, by implementing `Error()` method on any type. Consider the following example

```go
type MyError struct{
  stamp  time.Time
  msg    string
}
func (e *MyError) Error() string{
  return fmt.Sprintf("At %v - %s", e.stamp, e.msg)
}
func testError(a int) (int, error) {
  if a < 0 {
    return -1, &MyError{ time.Now(), "Cant process negative integers" }
  }
  return a + 1, nil
}
func main() {
  if _, err := testError(-1); err != nil {
    fmt.Println(err)
  }
}
```

In example as illustrated above, we have created a struct and defined a method `Error` on it

### Panic

Panic is a built-in function that stops the flow of control and begins _panicking_. When any function in Go calls panic**,** execution of function stops immediately. Any deferred functions are executed normally, and then it returns to its caller. 

To the caller, then it behaves like a call to panic. The process keep continues up the stack until all functions in the current goroutine have returned, at which point the program crashes. One can imagine it like house of cards, where crashing one card in structure would almost crashes everything around. Or cascaded structure, where making one slip will crash up to the bottom of function call stack.

Panics can be initiated by invoking panic directly. They can also be caused by runtime errors, such as out-of-bounds array accesses. to call a panic in Go, simply call to`panic` will suffice. Consider following example

```go
panic()
```

