# Code Organisation

So before we move forward and start writing other code, lets first look deeper into how Go organizes code.

Go programs are organized into packages. A package is a collection of source files in the same directory and is compiled together. Functions, types, variables, and constants defined in one source file are visible to all other source files within the same package.

In Go, each file has to belong to a package. Remember our first program, we did mention `package main`  in very first line, that means our code is packaged as main, though in Go `package main` means entry point for that program, we will discuss that later

A repository contains one or more modules. A module is a collection of related Go packages that are released together. A Go repository typically contains only one module, located at the root of the repository. A file named `go.mod` there declares the module path: the import path prefix for all packages within the module. The module contains the packages in the directory containing its `go.mod` file as well as subdirectories of that directory, up to the next subdirectory containing another `go.mod` file \(if any\).

Note that one doesn't need to publish your code to a remote repository before you can build it. A module can be defined locally without belonging to a repository. However, it's a good habit to organize your code as if you will publish it someday.

Each module's path not only serves as an import path prefix for its packages but also indicates where the `go` command should look to download it. For example, to download the module `golang.org/x/tools`, the `go` command would consult the repository indicated by `golang.org/x/tools`, first, it would look into $GOPATH variable directory for directory structure `golang.org/x/tools` if not then it would resolve it from `https://golang.org/x/tools`

An import path is a string used to import a package. A package's import path is its module path joined with its subdirectory within the module. For example, the module `github.com/google/go-cmp` contains a package in the directory `cmp/`. That package's import path is `github.com/google/go-cmp/cmp`. 

{% hint style="info" %}
Packages in the standard library do not have a module path prefix.
{% endhint %}

`$GOPATH` is path where go will look to resolve your packages first, if not then tries to download it. `$GOBIN` is a path to a folder where when a package, module or program build will produce binaries

{% hint style="info" %}
One should already have $GOPATH and $GOBIN variable saved and pointing to directories where you would like go binaries to be saved. It would best practice to also make $GOBIN to append to $PATH so that those binaries are resolved
{% endhint %}

Let's go ahead and create our first program again, to do that let's create a directory structure that would make it easy to publish our programs

```bash
cd $GOPATH
mkdir -p src/github.com/bagwanpankaj/hello_go
cd src/github.com/bagwanpankaj/hello_go
go mod init github.com/bagwanpankaj/hello_go
#=> go: creating new go.mod: module github.com/bagwanpankaj/hello_go
```

That's it we created a go module having a module path. Now let's see what Go did

```bash
ls
#=> go.mod
cat go.mod 
module github.com/bagwanpankaj/hello_go

go 1.14
```

So now we see what go did, it just created a file `go.mod` defining import path for module and version used to create it. That's good. Now let's create a file named `hello_go.go` and copy over content from our first program

```bash
package main
import "fmt"
func main(){
  fmt.Println("Hello World")
}
```

Save an done. Now let's see with $GOPATH and $GOBIN set, what go tools can do for us. In the terminal, run following command

```bash
cd $GOPATH
go install github.com/bagwanpankaj/hello_go
```

That command gave no output, how is that :\(. Okay, let's see if we have the program installed. In terminal run

```bash
hello_go
# Hello World
```

{% hint style="warning" %}
Do not panic if you do not get output, it may be because your $GOBIN is not part of the $PATH so set that up and it should work, as long as `go install` is creating bin under $GOBIN
{% endhint %}

Well where did that come from and how? Let's dive deep, so when we ran `go install`, it did compile and created a binary file, that we should find in our $GOBIN folder, let see

{% hint style="info" %}
**Note**: if $GOBIN is not set, Go will install binaries under $GOPATH/bin folder always
{% endhint %}

```bash
ls $GOBIN
hello_go 
```

Well, we have it there. To our, amusement Go provides a way to set GOBIN and can be achieved via

```bash
go env -w GOBIN=/some/other/directory
```

To undo this setup one can use

```bash
go env -u GOBIN
```

{% hint style="info" %}
Windows user should read [this](https://github.com/golang/go/wiki/SettingGOPATH) to see how to set GOPATH
{% endhint %}
