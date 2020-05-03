# Pointers

Go includes pointers concept from C. But go limit these to enables programmers to pass by reference than by value. Go restrict on what can be done with pointers, like one can not manipulate pointers to point to some other address.\`

A basic pointer construct in Go looks like this

```go
package main
import "fmt"
func main() {
  i, j := 42, 2701
  // var p *int        // Holds pointer to int value
  p := &i              // Address of i
  fmt.Println(*p)      // read i through the pointer
  *p = 21              // set i through the pointer
  fmt.Println(i)       // see the new value of i

  p = &j               // point to j
  *p = *p / 37         // divide j through the pointer
  fmt.Println(j)       // see the new value of j
}
```

In illustration above, we can clearly infer that its mostly looks like how the construct is implemented in C, though with some restriction. To get the address of space \(heap or stack\) where the value hold by variable is stored, can be known by `&` operator.

While to get/set value stored at the address \(considering the variable holds the address instead of value\), one can use `*` operator. Confusing right? To simplify to get the address pointer for a variable use `&` operator, while when you have a pointer, then use `*` operator to manipulate the value at the address

* `p := &v` will return address of variable `v` and store it in var `p` 
* `*p = *p + 1` will manipulate v directly by reference, so prior statement will increment value of v by 1 \(considering v is an int\)

Since pointers can be confusing to many programmers out there, most specifically to programmers who have never written a piece of code in `C` So lets simplify this more.

We will define two methods, one will be getting a parameter by value and other one will be getting parameters by reference and they will try to change the value and then we will see, who has changed the value of actual variable that's been passed. For that lets define two function first

```go
func passByVal(val int){
 val += 1 // increment value by one 
}
func passByRef(val *int){
 *val += 1 // increment value by one at this address
}
```

So in example illustrated above, `passByVal` takes an int parameter and increase its value by one, similarly `passByRef` takes an int pointer parameter and increment value at that address by one. Now lets write a program to test hypothesis as explained above

```go
func main() {
    value = 1
    fmt.Println("Initial value:", value)
    passByVal(value)
    fmt.Println("Value after passByVal:", value)
    passByRef(&value)
    fmt.Println("Value after passByRef:", value)
}
// Initial value: 1
// Value after passByVal: 1
// Value after passByRef: 2
```

Did you see the output? When we passed value to `passByVal`, it assigned value of var `value` to local parameter `val` and then it has increased `val` by one, but this did not affect the original variable `value`. Why? because it has been passed by value and that duplicated/cloned it to some other variable holding some other space in heap, while the value of cloned variable did increment by one but not of the original parameter `value` 

In contrast to this, when we passed address of variable `value` instead of value itself to `passByRef` and passByRef changed value by manipulating value at pointer, it did change value of original parameter `value` . That's why we see value of variable `value` being increased by 1

{% hint style="info" %}
**Note:** The only caution to be taken is that to make sure that when a variable holds pointer to another variable, we manipulate it by referencing value at that pointer, instead of pointer itself
{% endhint %}

