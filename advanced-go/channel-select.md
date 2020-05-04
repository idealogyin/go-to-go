# Select

{% hint style="warning" %}
This page is under active revision, content may be updated without notice
{% endhint %}

In Go,  `select` statement lets a goroutine wait on multiple communication operations. A `select` blocks until one of its cases can run, then it executes that case. It chooses one at random if multiple are ready. Combining goroutines and channels with select is a powerful feature of Go.

```go
c1 := make(chan string)
c2 := make(chan string)
go func() {
    time.Sleep(time.Second * 1)
    c1 <- "Hello"
}()
go func() {
    time.Sleep(time.Second * 2)
    c2 <- "World"
}()
for {
    select {
        case msg1 := <-c1:
            fmt.Println("Received first message: ", msg1)
        case msg2 := <-c2:
            fmt.Println("Received second message: ", msg2)
            return
    }
}
```

Here we have put `select` statement within indefinite `for` loop. So It will keep on listening to channels unless it returns by calling `return` in one of them. In illustration above, when first anonymous goroutine function is called, it returns "Hello" to channel that in turn printed on I/O module \(in our case cli\), but select it does not finish, its ready to listens to another round of call and then second anonymous function is called and that does return, returning from select. And hence program exits

Golang's select lets you wait on multiple channel operations. Combining goroutines and channels with select is a powerful feature of Go. 

Go, also provides `default` case when no other cases match, default will run. In simplest form it would look like following

```go
select {
case i := <-c:
    // use i
default:
    // receiving from c would block
}
```

