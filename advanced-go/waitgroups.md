# Waitgroups

{% hint style="warning" %}
This page is under active revision, content may be updated without notice
{% endhint %}

In previous chapters, we talked about how goroutines in Go language works. We have also seen several hacks to make our `main` program wait for goroutines. We have seen another strategy to make our `main` program wait in [Channel Synchronization](channel-synchronization.md) chapter. we have gone through [Select](channel-select.md) chapter. Today we will focus on providing robustness to our previous chapters by using semaphores from [sync](http://golang.org/pkg/sync/#WaitGroup) package, specially `sync.WaitGroup`

In Go, [sync.WaitGroup](https://golang.org/pkg/sync/#WaitGroup) implements three methods, `Add`, `Done` and `Wait` . We will discuss them at length. But before we jump for an example, in brief, goroutine with wait will wait for other goroutines \(number of which are incremented by Add\) to finish and call Done on WaitGroup before exiting.

Here is redone example from our previous chapter

```go
package main 

import(
  "fmt"
  "time"
  "math/rand"
  "sync"
)

var wait sync.WaitGroup // This creates a WaitGroup, to be used later

func Printer(a int){
  defer wait.Done() // Done signals that this gorutine is done doing work, decrementing semaphore counter
  time.Sleep(time.Millisecond * time.Duration(rand.Intn(100)))
  fmt.Println("a is: ", a)
}

func main(){
  max_routine := 10
  wait.Add(max_routine) // This adds maximum counter to waithgroup should wait before terminating main program
  fmt.Println("At start")
  for i := 0; i < max_routine; i++ {
    fmt.Println("Sending to routine: ", i)
    go Printer(i)
  }
  wait.Wait() // This waits for semaphore counter to be 0 and then terminates current program
  fmt.Println("At end!")
}

// time.Duration(rand.Intn(100)) will make goroutine sleep for varying time
//At the start
//Sending to routine:  0
//Sending to routine:  1
//Sending to routine:  2
//Sending to routine:  3
//Sending to routine:  4
//Sending to routine:  5
//Sending to routine:  6
//Sending to routine:  7
//Sending to routine:  8
//Sending to routine:  9
//a is:  9
//a is:  5
//a is:  6
//a is:  7
//a is:  2
//a is:  8
//a is:  3
//a is:  0
//a is:  4
//a is:  1
//
//At the end!
```

Results may vary from machines to machines and specific to implementation. The message is that how one can leverage `sync.WaitGroup` api to synchronize goroutines. Believe me, illustration above is very basic example of what can be achieved with WaithGroup. But in essence what we did is, we imported `sync` package. `sync` package contains `WaitGroup` type, we declared variable `wait` to be of WaitGroup type. `Waitgroup` provides three methods namely `Add`, `Done` and `Wait`.

1.\) `Add` method takes integer as a parameter delta to the counter, and once counter becomes zero, all blocking goroutines, waiting onto counter would be released. We provided no of goroutines we are going to wait upon

{% hint style="warning" %}
Note, that in illustration above, we provided our goroutine count at once to be 10. But in practical scenario, calling `wait.Add(1)` will increment counter by one. 
{% endhint %}

2.\) `Wait` methods waits for semaphore counter to become zero, before releasing goroutines, waiting onto other goroutines to terminate/finish. In illustration above, we are making our main program to wait for other goroutines to finish.

3.\) `Done` method basically indicates that current goroutine, in which this is being called is done/finished, while decrementing semaphore counter. Our goroutines calls to `Done` method indicating that goroutine is done executing its task.

