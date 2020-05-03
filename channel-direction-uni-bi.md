# Channel Direction \(uni/bi\)

By default channels can receive and send, but channels direction can be controlled by restricting them to either send or receive \(applicable only for method/func signature\). This ensures safety where required. For example

```go
func Ping( c chan<- string, msg string){
  c <- msg
}
func Pong( c <-chan string, cc chan<- string ){
  msg := <-c
  cc <- msg
}
func main(){
  pic := make(chan string, 1)
  poc := make(chan string, 1)
  Ping(pic, "Pass the message")
  Pong(pic, poc)
  fmt.Println(<-poc)
}
```

#### Channels with Range and Close

Channel can be iterated over using range and can be closed. Channel, closed once will allow no more values to passed across.

```go
func fib(num int, c chan int) {
  x, y := 0, 1
  for i := 0; i < num; i++ {
    c <- x
    x, y = y, x+y
  }
  close(c)
}
func main() {
  c := make(chan int, 10)
  go fib(cap(c), c)
  for i := range c {
    fmt.Println(i)
  }
}
```

