# Channel Synchronization

Channel can be used to synchronise execution among goroutine because reciever is always blocking. We can use this to halt return from main unc to wait for goroutine to finish, as shown in example below

```go
func Blocker(finish chan bool) {
    fmt.Println("Started Working")
    time.Sleep(time.Second)
    fmt.Println("Done Working")
    finish <- true
}
func main() {
    finish := make(chan string)
    go Blocker(finish)
    <- finish
}
```

