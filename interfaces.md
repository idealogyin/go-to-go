# Interfaces

{% hint style="warning" %}
This page is under active revision, content may be updated without notice
{% endhint %}

Golang implements interfaces as types and as collection of methods\(specs for what should be considered of that type\). Let’s first talk about collection of methods \(specs that other types could implement\)

```go
type Vehicle interface {
  Run() string
  Speed() int
  Stop() string
  Start() string
}
```

So what we did, is define a blueprint for Vehicle type, any type would be considered a vehicle that implements all methods listed in vehicle.

Let’s start defining some vehicles

```go
type Car struct { Odometer int }

func (c Car) Run() string{
  return "Running"  
}
func (c Car) Speed() int {
  return c.Odometer
}
func (c Car) Stop() string{
  return "Stopping"
}
func (c Car) Start() string{
  return "Starting"
}

type Truck struct { Odometer int }

func (t Truck) Run() string{
  return "Running"  
}
func (t Truck) Speed() int {
  return t.Odometer
}
func (t Truck) Stop() string{
  return "Stopping"
}
func (t Truck) Start() string{
  return "Starting"
}

type Bike struct { Odometer int }

func (b Bike) Run() string{
  return "Running"  
}
func (b Bike) Speed() int {
  return b.Odometer
}
func (b Bike) Stop() string{
  return "Stopping"
}
func (b Bike) Start() string{
  return "Starting"
}
```

Okay, so we defined three structs that implements out `Vehicle` interface. Now lets looks it in action

```go
func main(){
  vehicles := []Vehicle{ Car{ 100 }, Car{ 110 }, Bike{ 70 }, Truck{ 60 } }
  for _, vehicle := range vehicles {
    fmt.Println(vehicle.Start())
    fmt.Println(vehicle.Speed())
    fmt.Println(vehicle.Stop())
  }
}
// Starting
// 100
// Stopping
// Starting
// 110
// Stopping
// Starting
// 70
// Stopping
// Starting
// 60
// Stopping
```

SO here we creted a slice of type `Vehicle` and stuffed our structs implementing `Vehicle`, ieterating over them easily. If we assign type that does not implements, methods in `Vehicle` interface it can not be included in slice, let’s look at it

```go
type Jumbo struct {}

func main(){
  vehicles := []Vehicle{ Car{ 100 }, Car{ 110 }, Bike{ 70 }, Truck{ 60 }, Jumbo{} }
  for _, vehicle := range vehicles {
    fmt.Println(vehicle.Start())
    fmt.Println(vehicle.Speed())
    fmt.Println(vehicle.Stop())
  }
}
// cannot use Jumbo literal (type Jumbo) as type Vehicle in array element: 
// Jumbo does not implement Vehicle (missing Run method)
```

So this clearly not going to accept `Jumbo` in `Vehicle` slice as it does not implement `Vehicle`

Now we come to the next use of `interface`, that is type. In function’s argument signature can accept an interface type, meaning it could accept any type of value as those can be converted/casted to `interface`

```go
func PrintInterface( value interface{} ){
  fmt.Println(value)
}

func main(){
  PrintInterface( 80 )
  PrintInterface( "apple" )
  PrintInterface( 90.10 )
  PrintInterface( []string{"a", "b", "c", "d"} )
}
// 80
// apple
// 90.1
// [a b c d]
```

