# Installation

### Getting Super Powers

Installing Go is easy, one can visit their [download](https://golang.org/dl/) page and download the latest version build for there respective Operating System.

Here are some popular one

#### Mac OSX

One could use homebrew distribution by running following command in terminal

```bash
brew install go
```

This would automatically take care of all the things needed for installation. Alternatively, [here](https://dl.google.com/go/go1.14.2.darwin-amd64.pkg) is a direct link for download for OSX

{% hint style="warning" %}
Note: Direct link points to Go v1.14.2 at the time of writing this book. This may be periodically updated, but one is requested not to depend on it for the latest version
{% endhint %}

#### Ubuntu 18.04 or higher

Again it is highly recommended that one should install the Golang directly from [download](https://golang.org/dl/) page,  or by a direct link [here](https://dl.google.com/go/go1.14.2.linux-amd64.tar.gz)

{% hint style="warning" %}
Note: Direct link points to Go v1.14.2 at the time of writing this book. This may be periodically updated, but one is requested not to depend on it for the latest version
{% endhint %}

Once you have downloaded the `gzip` file, extract it someplace in your home directory and then add following lines to you  `$HOME/.bashrc` or `$HOME/.bash_profile` file

```bash
export GOROOT=$HOME/bin/go1.14.2.linux-amd64/go
export PATH=$PATH:$GOROOT/bin
export GOPATH=$HOME/code/gocode
export GOBIN=$GOPATH/bin
export PATH=$PATH:$GOBIN
```

{% hint style="info" %}
Please replace path with the path you have extracted the zip file into
{% endhint %}

Here `GOROOT` points to the parent directory of bin in go folder, then the bin path is extended to `PATH` variable. `GOPATH` is where you go get or personal code lives, `GOBIN`points to go package or local code binary that gets generated when go code is compiled. We will discuss these at length, later

Or alternatively, If you're using Ubuntu 18.04 LTS or 19.10 on amd64, arm64, armhf or i386, then you can use the `longsleep/golang-backports` PPA and install Go 1.14. 

```bash
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt update
sudo apt install golang-go
```

{% hint style="warning" %}
Note ****that `golang-go` installs the latest Go as default Go. If you do not want that, install `golang-1.14` instead and use the binaries from `/usr/lib/go-1.14/bin`

These packages were not created by the Go project, and we don't support them, but they may be useful for you.
{% endhint %}

#### Windows

For Microsoft Windows, it is highly recommended that one should install from Golang [download](https://dl.google.com/go/go1.14.2.windows-amd64.msi) page

### Instructions

[Official binary distributions](https://golang.org/dl/) are available for the FreeBSD \(release 10-STABLE and above\), Linux, macOS \(10.11 and above\), and Windows operating systems and the 32-bit \(`386`\) and 64-bit \(`amd64`\) x86 processor architectures.

If a binary distribution is not available for your combination of operating system and architecture, try [installing from source](https://golang.org/doc/install/source) or [installing gccgo instead of gc](https://golang.org/doc/install/gccgo).

### System Requirements

| Operating System | Architecture | Notes |
| :--- | :--- | :--- |
| FreeBSD 10.3 or higher | amd64, i386 | Debian GNU/kFreeBSD not supported |
| Linux 2.6.23 or higher with glibc | amd64, i386, arm arm64, s390x, ppc64le | CentOS/RHEL 5.x not supported. Install from source for other libc |
| Mac OS 10.11 or higher | amd64 | use the clang or gcc† that comes with Xcode^^ for `cgo` ^ support |
| Windows 7, Server 2008 R2 or higher | amd64, i386 | use MinGW \(`386`\) or MinGW-W64 \(`amd64`\) gcc^. No need for cygwin or msys. |

{% hint style="warning" %}
^ A C compiler is required only if you plan to use [cgo](https://golang.org/cmd/cgo).  
^^ You only need to install the command-line tools for [Xcode](https://developer.apple.com/Xcode/). If you have already installed Xcode 4.3+, you can install it from the Components tab of the Downloads preferences panel.
{% endhint %}

### Testing the installation

Now since we are done with installation. Let's test if everything is fine before moving forward. Fire up a terminal on your system and run following command

```bash
go version
# OUTPUT: go version go1.14.2 linux/amd64
```

If everything is fine one should see version output correctly.  To test tooling run following command in terminal

```bash
gofmt -v
flag provided but not defined: -v
usage: gofmt [flags] [path ...]
  -cpuprofile string
        write cpu profile to this file
  -d    display diffs instead of rewriting files
  -e    report all errors (not just the first 10 on different lines)
  -l    list files whose formatting differs from gofmt's
  -r string
        rewrite rule (e.g., 'a[b:len(a)] -> a[b:]')
  -s    simplify code
  -w    write result to (source) file instead of stdout
```

If you get something similar without any error. We are good to Go

