# Buffered Channels

By default channels are not buffered \(i.e does not hold value\), meaning that connection has to be active with both ends \(sending, recieving\) being present. Buffered channel allows sent values to buffered \(upto its capacity\) until reciever recieves it

```go
func main() {
    msg := make(chan string, 2)
    msg <- "Hello World"
    msg <- "Hola"
    fmt.Println(<-msg)
    fmt.Println(<-msg)
}
```

Assigning more than buffered before receiver receiving it will panic \(if error is not captured\)

```go
    msg <- "Hello World"
    msg <- "Hola"
    msg <- "Holaa"            // will panic
    fmt.Println(<-msg)
    fmt.Println(<-msg)
```

