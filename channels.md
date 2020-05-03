# Channels

In last [part](http://blog.bagwanpankaj.com/go-to-go-concurrency), we talked about `goroutines` and channels. As discussed there is much more to channels, liked channel direction, by default a channel is bi-directional, but it can be restricted to sending or receiving.

In sender, receiver example from [part](http://blog.bagwanpankaj.com/go-to-go-concurrency), sender can only be restricted to sending, by redifining it like

```go
func sender(ch chan <- int) {
  for i := 0; ; i++ {
    ch <- i
  }
}
```

Now sender can only send signal to channel `ch`. Similarly receiver can be restricted just to receive, by redifining it like

```go
func receiver(ch <- chan int) {
  for {
    message := <- ch
    fmt.Println("received: ", message)
    time.Sleep(time.Millisecond * 100)
  }
}
```

**Buffering in channels**

Generally `channels` are synchronous, but they can have buffer of specified size. Buffer size can be specified by passing a second argument while creating a channel

```go
ch := make(chan int, 10)
```

Now this channel can buffer at most 10 messages, working as a pub/sub.

**Select**

Select work like a case switch for channels, basic construct looks like:

```go
select {
case message_from_ch1 := <- ch1:
    fmt.Println(message_from_ch1)
case message_from_ch2 := <- ch2:
    fmt.Println(message_from_ch2)
}
```

