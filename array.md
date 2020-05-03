# Array

In Go, array has to have its length declared at the time of declaration, limiting its users where length can not be determined. For example responses from third party api's etc. Array in Go can be declared with `[n]T` where n is length of array and T would be type of elements its going to hold.

Simplest array construct would look like this

```go
var array [3]int
fmt.Println("Empty Array: ", array)
// Empty Array: [0 0 0]
```

So we do see that we declared an integer array of size 3, since we did not specify elements, Go has initialized it with zeros of int, that are 0

Go allows one to assign values to an array by its index, for example to assign value 6 to array declared in previous example at index 2, one would write

```go
var array [3]int
array[2] = 6
fmt.Println("Array: ", array)
// Array: [0 0 6]
```

In Go, we can also initialize an array at the time of declaration with default values. See following example

```go
declared := [5]int{1, 2, 3, 4, 5}
```

In this, declared variable contains an array of lenth 5, holding values from one to five, in that order. Go also enables programmers to have two dimentional array, like following

```go
var vector [2][3]int
for i := 0; i < 2; i++ {
    for j := 0; j < 3; j++ {
        vector[i][j] = i + j
    }
}
```

In example illustrated above, vector variable hold array of lenth 2 that holds another array of lenth 3 holding integers.

