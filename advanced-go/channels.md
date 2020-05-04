# Channels

In last [part](goroutines.md), we talked about `goroutines` and channels. As discussed there is much more to channels, like channel direction, by default a channel is bi-directional, but it can be restricted to sending or receiving.

Lets first understand channels, channels in Go can be seen as pipe, that when data is put in at one end can be recieved at another end, where the both the ends are goroutine. In Go, channel can be defined as

```go
ch := make(chan int)
```

Above code defines a channel that can pass through an integer. By default channels are blocked until the reciever picks up the item supplied to it, then only sender can send next item. 

In sender, receiver example from previous [chapter](goroutines.md), sender can only be restricted to sending, by redifining it like

```go
func sender(ch chan <- int) {
  for i := 0; i < 10 ; i++ {
    ch <- i
  }
}
```

So in above illustration `chan` followed by either `->` `<-` makes channel unidirection, in direction of arrow. So now channel `ch` in sender function can only recieve a value of type int.

Now sender can only send signal to channel `ch`. Similarly receiver can be restricted just to receive, by redifining it like

```go
func receiver(ch <- chan int) {
  for i := 0; i < 10 ; i++ {
    message := <- ch
    fmt.Println("received: ", message)
    time.Sleep(time.Millisecond * 100)
  }
}
```

Channel can be closed with utility finction `close` 

```go
close(ch)
```

That way we have restricted channel to only recieve a value of type int. By default channel are synchronous and blocking in nature. What do we mean by synchronous and blocking is that at any given time channel \(as defined above\) can hold only one value at a time, unless it is recieved by reciever. Once reciever has recieved previous value channel can hold another, otherwise it can in some scenarios result in **deadlock**.

To overcome this Go has provided buffered channel. We will talk about channel buffering in next Chapter

