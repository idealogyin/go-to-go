# Errors

{% hint style="warning" %}
This page is under active revision, content may be updated without notice
{% endhint %}

In Go it is idiomatic to communicate errors explicitly, as separate return value. This contrasts with the exceptions used in languages like Java and Ruby.

```go
func testError(a int) (int, error) {
  if a < 0 {
    return -1, errors.New("Negative number")
  }
  return a + 1, nil
}
```

`errors.New` constructs a basic error with a message, nil as second argument means no errors. Make a thumb rule to return error as last return value

Go allows one to define custom error type, by implementing `Error()` method on them

```go
type MyError struct{
  stamp time.Time
  msg    string
}
func (e *MyError) Error() string{
  return fmt.Sprintf("At %v - %s", e.stamp, e.msg)
}
func testError(a int) (int, error) {
  if a < 0 {
    return -1, &MyError{ time.Now(), "Cant process negative integers" }
  }
  return a + 1, nil
}
func main() {
  if _, err := testError(-1); err != nil {
    fmt.Println(err)
  }
}
```

