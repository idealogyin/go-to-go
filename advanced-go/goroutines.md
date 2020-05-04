# Goroutines

Go came to existance to solve problems being faced by today’s software, one of them is concurrency. Sol lets first understand what is concurrency? 

{% hint style="info" %}
In [computer science](https://en.wikipedia.org/wiki/Computer_science), **concurrency** is the ability of different parts or units of a program, algorithm, or problem to be executed out-of-order or in partial order, without affecting the final outcome. This allows for parallel execution of the concurrent units, which can significantly improve overall speed of the execution in multi-processor and multi-core systems. In more technical terms, concurrency refers to the decomposability property of a program, algorithm, or problem into order-independent or partially-ordered components or units.[\[1\]](https://en.wikipedia.org/wiki/Concurrency_%28computer_science%29#cite_note-1)
{% endhint %}

In simpler terms, Concurrency in computer programs is ability to execute pieces of program in parellel while providing control and communication among them. The execution of said pieces of programs can be in out of order or in partial order. To solve this Go has special construct called goroutines to execute pieces of programs in parallel.

Let see a how a goroutine can be defined in Go

```go
go someFunc(a, b, c)
```

In illustration above, while variables `a` , `b` and `c` happens in current goroutine but execution of `someFunc` happens in seperate goroutine. One can imagine goroutines as lightweight threads that are scheduled and controlled by Go. Goroutines runs in same shared address space so access to shared memory should be synchronised, go provides several primitives in `sync` package

By default, main function of package in go is run concurrently, implicitly. For expliit call we pass code block\(that needs to be executed in routine\) to `go`

```go
package main 

import "fmt"

func printer(a int){
  fmt.Println("a is: ", a)
}

func main(){
  fmt.Println("At the start")
  for i := 0; i < 10; i++ {
    fmt.Println("Sending to routine: ", i)
    go printer(i)
  }
  var get string
  fmt.Scanln(&get)
  fmt.Println("At the end!")
}

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
//a is:  0
//a is:  1
//a is:  2
//a is:  3
//a is:  4
//a is:  5
//a is:  6
//a is:  7
//a is:  8
//a is:  9
//
//At the end!
```

Notice `fmt.Scanln(&get)`; this actually makes our main program to wait for inputs, otherwise it will exit before go routine actualy can print. A problem with this code is that, it looks synchronous, in order. To actually see that if goroutine are asynchronous, we need to make goroutine sleep for random time. Lets rewrite above illustration as:

```go
package main 

import(
  "fmt"
  "time"
  "math/rand"
)

func printer(a int){
  time.Sleep(time.Millisecond * time.Duration(rand.Intn(100)))
  fmt.Println("a is: ", a)
}

func main(){
  fmt.Println("At the start")
  for i := 0; i < 10; i++ {
    fmt.Println("Sending to routine: ", i)
    go printer(i)
  }
  var get string
  fmt.Scanln(&get)
  fmt.Println("At the end!")
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

Look at this, now it is random. This illustrates that go routine are independent to each other and runs separately.

Now what we showcased so far is called parallelism, we still need to make them communicate to each other and `channels` comes to our rescue. Channels provide a mechanism of communication and synchronisation among goroutines. Lets look at example.

```go
package main

import (
  "fmt"
  "time"
)

func sender(ch chan int) {
  for i := 0; ; i++ {
    ch <- i
  }
}
func receiver(ch chan int) {
  for i:= 0; i < 10; i++ {
    message := <- ch
    fmt.Println("received: ", message)
    time.Sleep(time.Millisecond * 100)
  }
}
func main() {
    var ch chan int = make(chan int)
    
    go sender(ch)
    receiver(ch)
    
    var input string
    fmt.Scanln(&input)
}
```

That’s interesting. This is just a simple example of `channels` capabilities, there is much more that we have for channels in out next chapter.

