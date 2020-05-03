# Branching: If/Else

Go provides conditionals/branching via If/Else and Switch statements. These works mostly as they are intended to work, or one have seen them working in other programming languages. Here is very basic If statement in Go

```go
package main
import "fmt"
func main() {
    if 10%2 == 0 {
      fmt.Println("10 is even")
    }
}
// 10 is even
```

In Go, if statement returns true, block assigned to it will be evaluated, otherwise not. A `If` statement can be combined with `else` to give an option when statement evaluates to false. Lets change our example we used before

```go
package main
import "fmt"
func main() {
    var value = 9
    if value%2 == 0 {
      fmt.Printf("%d is even", value)
    } else {
      fmt.Printf("%d is odd", value)
    }
}
// 9 is odd
```

Simple, right. If/else can have multiple if else combined together making it more realistic to real world problems, like following

```go
package main
import "fmt"
func main() {
    var bmi = 9
    if value%2 == 0 {
      fmt.Printf("%d is even", value)
    } else {
      fmt.Printf("%d is odd", value)
    }
}
```

Here is BMI categories as available on [wikipedia](https://en.wikipedia.org/wiki/Body_mass_index). Lets create a simple Go program that would tell one, which category does one falls into

| Category | From | To |
| :--- | :--- | :--- |
| Very severely underweight |  | 15 |
| Severely underweight | 15 | 16 |
| Underweight | 16 | 18.5 |
| Normal \(healthy weight\) | 18.5 | 25 |
| Overweight | 25 | 30 |
| Obese Class I \(Moderately obese\) | 30 | 35 |
| Obese Class II \(Severely obese\) | 35 | 40 |
| Obese Class III \(Very severely obese\) | 40 |  |

```go
package main
import "fmt"
func main() {
    var bmi = 19.0
    if bmi <= 15.0 {
      fmt.Printf("Very severely underweight")
    } else if bmi > 15.0 && bmi <= 16.0 {
      fmt.Println("Severely underweight")
    } else if bmi > 16.0 && bmi <= 18.5 {
      fmt.Println("Underweight")
    } else if bmi > 18.5 && bmi <= 25.0 {
      fmt.Println("Normal (healthy weight)")
    } else if bmi > 25.0 && bmi <= 30.0 {
      fmt.Println("Obese Class I (Moderately obese)")
    } else if bmi > 30.0 && bmi <= 35.0 {
      fmt.Println("Obese Class II (Severely obese)")
    } else {
      fmt.Println("Obese Class III (Very Severely obese)")
    }
}
// Normal (healthy weight)
```

Change bmi value and see what would be program output

### If with short statement

In Go, If statement allows a short statement just before the condition; seperated by `;` and it would executed before conditional statement. For illustration consider following example

```go
package main
import "fmt"
func main() {
    if value := 7; value%2 == 0 {
      fmt.Printf("%d is even", value)
    } else {
      fmt.Printf("%d is odd", value)
    }
}
// 7 is odd
```

