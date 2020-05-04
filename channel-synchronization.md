# Channel Synchronization

Channel can be used to synchronisze execution among goroutine, keep in mind that out main function is also run in goroutine. We have already seen that once goroutine is spawned from another goroutine, it runs seperately and the parent goroutine will exit once it is done running itself and will not wait for goroutine that it has created in process. 

Do you remember we used  `fmt.Scanln` that's because we wanted our main program to wait for unless user presses any key, actually we wanted to showcase console prints from goroutine and `fmt.Scanln` is a hack for that

But go does provide way to communicate between goroutines and by now we know that reciever is blocked until channel receives a message from sender. We can create a goroutine from our main goroutine with a channel that recieves a message of some kind from child goroutine and make our main program reciever for that message, done. Let's see that in action 

```go
func Blocker(finish chan bool) {
    fmt.Println("Started Working")
    time.Sleep(time.Second)
    fmt.Println("Done Working")
    finish <- true // Once blocker is done doing thing it notifies the channel
}
func main() {
    finish := make(chan bool)
    go Blocker(finish) // spawn blocker 
    <- finish          // wait for blocker to finish
}
// Started Working
// Done Working
// Program exited.
```

See, how simply we achieved with channels what we were trying to achieve with `Scanln` hack. But do notice

```go
<- finish
```

here since there is no reciever mentioned explicitly, current context itself is a reciever. There are several other way to wait for goroutines.

