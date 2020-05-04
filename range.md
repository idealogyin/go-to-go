# Range

In Go, `range` is an iterator and can iterate over wide range of iteratable data types, including arrays, slices and maps. When iterated, range produces two variable for every iteration, first is index and second is value \(in case of maps, first would be the key\)

{% hint style="info" %}
In case of `maps` first variable produced would be the key and other one would be value assigned to that key
{% endhint %}

Simplest construct for `range` in Go would look like

```go
numbers := []int{1,2,3,4,5,6,7,8,9}
sum := 0
for i, number := range numbers {
    fmt.Printf("%d has %d", i, number)
    fmt.Println("\n")
    sum += number
}
fmt.Println("sum: ", sum)
```

Here `range` when iterating over variable `numbers` would assign index to i and value to number. One can ignore the index when not being used by assigning it to `_` . Just like we have seen in maps

Similarly `range` can be used to iterate over a slice and maps as well. Iterating over slice would be similar to arrays. Lets look at how it can iterate over maps

```go
myMap := map[string] string {"a": "apple", "b": "banana", "c": "cherry"}
for k, v := range myMap {
    fmt.Println(k, " has ", v)
}
// a  has  apple
// b  has  banana
// c  has  cherry
```

Go, in range allows us to skip first variable index or key by assigning it to `_` Like following

```go
myMap := map[string] string {"a": "apple", "b": "banana", "c": "cherry"}
for _, v := range myMap {
    fmt.Println(v)
}
// apple
// banana
// cherry
```

In Go, we can skip value altogether by not declaring variable for it. For illustration

```go
myMap := map[string] string {"a": "apple", "b": "banana", "c": "cherry"}
for k := range myMap {
    fmt.Println(k)
}
// a
// b
// c
```

