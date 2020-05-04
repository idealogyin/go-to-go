# Select

{% hint style="warning" %}
This page is under active revision, content may be updated without notice
{% endhint %}

Golang's select lets you wait on multiple channel operations. Combining goroutines and channels with select is a powerful feature of Go.

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
for i := 0; i < 2; i++ {
    select {
    case msg1 := <-c1:
        fmt.Println("Received first message: ", msg1)
    case msg2 := <-c2:
        fmt.Println("Received second message: ", msg2)
    }
}
```

A select blocks until one of its cases can run, then it executes that case. It chooses one at random if multiple are ready.

Golang's select lets you wait on multiple channel operations. Combining goroutines and channels with select is a powerful feature of Go.

```go
import (
  "fmt"
  "sync"
  "time"
)
// SafeCounter is safe to use concurrently.
type SafeCounter struct {
  v       map[string]int
  mux  sync.Mutex
}
// Inc increments the counter for the given key.
func (c *SafeCounter) Inc(key string) {
  c.mux.Lock()
  // Lock so only one goroutine at a time can access the map c.v.
  c.v[key]++
  c.mux.Unlock()
}
// Value returns the current value of the counter for the given key.
func (c *SafeCounter) Value(key string) int {
  c.mux.Lock()
  // Lock so only one goroutine at a time can access the map c.v.
  defer c.mux.Unlock()
  return c.v[key]
}
```

