# Structs

{% hint style="warning" %}
This page is under active revision, content may be updated without notice
{% endhint %}

Go has a speciel type `struct` to define custome type with named fields. Struct act like collection of attributes/properties similar to classes in OOPs languages out there, but not exactly.

**Structs**

Struct can have named attributes of any type and methods can be defined to operate on that. Lets define a `Person` struct that will contain `first_name`, `last_name` and `age`

```go
type Person struct{
  first_name, last_name string
  age uint8
}
```

So that’s it, we just defined a person struct with some attributes. Let’s use it. There are many way to initialize an struct, here are some

```go
var p Person
```

Note when we initialize it without providing any value, go assign default value \(zeros of type assigned\) to each attributes, depending on there types, like `first_name`, `last_name` will be assigned a blank string "" and age will be assigned 0.

This can also be in initialized using `new` function that allocates memory and return pointer.

```go
p := new(Person)
```

But most used way is to initialize while passing values to it, here is how

```go
p := Person{first_name: "John", last_name: "Lego", age: 32}
//or we can leave off attribute names if we know order
p := Person{"John", "Lego", 32}
```

Attributes of a struct can be accessed by `.` operator. So to access `first_name` of `p` of type `Person` , one can use

```go
p.first_name // John
p.first_name = "Walker" // This would change first_name of object p
```

#### Struct with Pointers

Pointers with structs work in same way as they do generally in Go, but Go allows fields to be accessed without explicit de-referencing. For example

```go
package main
import "fmt"
type Person struct {
  Name string
  Age int
}
func main() {
  p := Person{"gopher", 2}
  pp := &p
  pp.Name = "Golang rocks"  // Same can be done via (*pp).Name
  (*pp).Name = "Golang rocks" // Similar to statement above
  fmt.Println(pp.Name)
  fmt.Println((*pp).Name)
}
```

