# Maps

Maps in Go are similar construct to `hash` or `dict` in other languages. You can assume it as a dictionary type where we can have a non integer index and corresponding values, kind of similar to JSON. A simplest example of map would be 

```go
myMap := map[string]int{"one": 1, "two": 2}
```

Simple syntax to declare map would be `make[kT]vT` , where kT is type of key and vT is type of value. In above illustration, we are declaring a map and assigning it some values. Maps can be access similar to arrays but we need to use key as an index. For example 

```go
myMap["one"]
//=> 1
```

To declare an empty map we could use something like this and then assign values at later stage.

```go
emptyMap := make(map[string]int)
// then assign values later
emptyMap["one"] = 1
emptyMap["two"] = 2
fmt.Println(len(emptyMap))
// =>  2
```

Did you notice one thing, like I did? We did not specify length of map at any stage, right? Because map in go defines the length internally and when we assign/append or delete values it keeps on defining new map with predicted length and release previous objects to be garbage collected

To delete a key from map, Go provides `delete` method. Syntax for delete is `delete(mapVar, key)` , where mapVar is variable that holds map and key is the key to be deleted. In our `myMap` example 

```go
delete(myMap, "one")
fmt.Println(myMap)
// map[two:2]
```

In Go, when querying a key returns two values, first one is value being hold against key, while second value is boolean, if that key existed or not, in first place. For illustration, consider following example

```go
myMap := map[string]int{"one": 1, "two": 2}
_, exist := myMap["three"]
fmt.Println(exist)
//=> false
```

It returned false, because there was no key `three` , Go does return zeros for type assigned for keys that does not exist



