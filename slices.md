# Slices

So to solve the problem we had at hand in previous chapter, Slices are Go's response to have array of dynamic length. But there is gotcha, one need to define length of slice at the time of declaration, but more data of same type could be appended to slices in future. For example

```go
slice := make([]string, 3)    // make is similar to new
fmt.Println("Empty:", slice)
```

So what we have done? We have defined a slice of type string having length 3. We can dynamically assign values to slices similar to array. In example above `make` is similar to new keyword. Like

```go
slice[0] = "apple",
slice[1] = "orange"
slice[2] = "banana"
```

To get the length of slices, we have similar `len` function as array

```go
len(slice) //=> 3
```

Go provides a special method called `append` for `slices`. this method actally creates a new slice with new lenght, assigning old and new element to it and returning a new slice. That returned slice should be saved in a variable to have access to it.

```go
slice := make([]string, 3)    // make is similar to new
fmt.Println("Empty:", slice)
slice[0] = "apple"
slice[1] = "orange"
slice[2] = "banana"
slice = append(slice, "peach")
slice = append(slice, "mango", "strawberry")
fmt.Println("Append:", slice)
```



