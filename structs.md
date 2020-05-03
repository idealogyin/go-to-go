# Structs

Go has a speciel type `struct` to define custome type with named fields. Struct act like collection of attributes/properties similar to classes in OOPS languages out there, but not exactly.

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

Note when we initialize it without providing any value, go assign default value to each attributes, depending on there types, like `first_name`, `last_name` will be assigned a blank string “” and age will be assigned 0.

This can also be in initialized using `new` function that allocates memory and return pointer.

```go
p := new(Person)
```

But most used way is to initialize while passing values to it, here is how

```go
p := Person{first_name: "John", last_name: "Lego", age: "32"}
//or we can leave off attribute names if we know order
p := Person{"John", "Lego", "32"}
```

**Methods**

In Go, Methods are similar to `func` except that they have a receiver to operate on. To get full\_name of a person we would love to define a method to `Person` struct like

```go
func(p Person) full_name() {
  fmt.Println(p.first_name, p.last_name)
}
p.full_name()
//=> "John Lego"
```

Well done Jack! But problem with this method is, it is printing `full_name` to standard output. But in real world we would need our `full_name` to return full name of a person. Here is how

```go
func(p Person) full_name() string {
  s := p.first_name + " " + p.last_name
  return s
}
fmt.Println(p.full_name())
//=> "John Lego"
```

Just FYI Jack, struct can also have embedded types, not just legacy types. Here is an example of struct `Employee`

```go
type Employee struct{
  Person
  employee_id string
}
```

Now to initilize it we need to follow same way, but first argument should be of type person, like

```go
e :=  Employee{Person{"Pankaj", "Bagwan", 26}, "emp101"}
fmt.Println(e.Person.full_name())
fmt.Println(e.full_name())
fmt.Println(e.employee_id)
```

Note that method defined on struct `Person` is alo available directly and indirectly to employee.

