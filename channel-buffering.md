# Buffered Channels

As hinted in previous Chapter, by default channels are not buffered \(i.e does not hold value\), meaning that connection has to be active with both ends \(sending, recieving\) being present. Buffered channel allows sent values to buffered \(upto its capacity\) until reciever recieves it.

This way sender can still enqueue messages in channel, without bothering about reciever being stuck or not attached. Lets look at example with buffer size two

```go
func main() {
    msg := make(chan string, 2)
    msg <- "Hello World"
    msg <- "Hola"
    fmt.Println(<-msg)
    fmt.Println(<-msg)
}
```

In above illustration, channel received first message `"Hello World"` and then while the message was still in the queue, it recieved another message `"Hola"` and recievers were not even defined by then. Buffered channel  can overflow in case buffer is full and we try to assign another value to it, ant throw panic

```go
    msg <- "Hello World"
    msg <- "Hola"
    msg <- "Holaa"            // will panic
    fmt.Println(<-msg)
    fmt.Println(<-msg)
    
    // fatal error: all goroutines are asleep - deadlock!
```

