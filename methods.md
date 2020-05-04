# Methods

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

