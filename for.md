# For loop

In Go, we have only one looping construct `for` But that powerful and more than enough than having multiple looping construct. Go's `for` can mimic many other looping construct, that we will see in a minute

In Go, a basic `for` loop construct looks like following

```go
for i:=1; i <= 10; i++{ 
  fmt.Println(i)
}
```

If you look at that example, it has three components

* init statement: where it assigns intial value, before looping starts
* Condition expression: condition to be evaluated before every iteration
* Post statement: statement to execute after every iteration

This is classical `for` loop construct that we have been using since we dived into programming. But in Go there is more to it, as mentioned earlier that this simple construct can take many forms. Take a look at following example

```go
i := 1
for {
  fmt.Println(i)
  i++
  if i == 10{
    break
  }
}
```

In illustration above, `for` loop does not have init, condition and post statement, as they are optional. Without them `for` loop will keep on going, so it becomes prorammer's prerogative to break out of loop. And that's exactly what `break` is doing in above illustration.

Go also allows programmer to use `for` loop without init and post statement as illustrated below

```go
i := 1
for i < 10 {
  fmt.Println(i)
  i++
}
```

following code snippet is also equal to what we have written above

```go
i := 1
for ; i < 10; {
  fmt.Println(i)
  i++
}
```

