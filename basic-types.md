# Basic Types

Go does have wide range of built-in types as well allows programmer to define custom types. We would discuss these later in depths. Here are some basic types that one should know before proceeding forward

```go
bool // holds boolean values
string // holds string values
int  int8  int16  int32  int64 // signed integer values
uint uint8 uint16 uint32 uint64 uintptr // unsigned integer values
byte // same as uint8
rune // alias for int32, represents a Unicode code point
float32 float64
complex64 complex128
```

 Bit size of int, uint, uintptr depends on system architecture. On 32 bit system, they would assumed to be 32 bit wide, while on 64 bit system, they would be 64 bit wide.

Usually using `int` should suffice unless we have specific resaon to use signed, unsigned or other varying types of integers/floats.

### Type Conversions

Go allows type conversion from one type to another via `T(v)` where `T` is type to cast to `v` is value to be typecasted. 

{% hint style="warning" %}
In Golang, var of one type can not be assigned value of other type unless converted
{% endhint %}

```go
var age int = 23
var agef float64 = float64(age)
var ageu uint = uint(agef)
```

