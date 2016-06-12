# -1: Getting ready to Go

Github: https://github.com/dearshrewdwit/a_little_go_app

First things first. We need to get Go:
https://golang.org/dl/

Follow the instructions! (the essentials are here below)
After you've downloaded and opened the package successfully, set the environment variable GOPATH to the directory where all your fantastic Go work will be done. Here it's set for the current session first and then for all future sessions.

```
$ export GOPATH=$HOME/your_go_workspace
$ echo "export GOPATH=$HOME/your_go_workspace" >> your_shell_profile
```

Next, make the directories `src/github.com/user/hello` inside your workspace (if you use GitHub, substitute your user name for user), and inside the hello directory create a file named `hello.go` with the contents in Section 0.


Example folder structure:
```
Here's an example directory layout:

    GOPATH=/home/user/gocode

    /home/user/gocode/
        src/
            foo/
                bar/               (go code in package bar)
                    x.go
                quux/              (go code in package main)
                    y.go
        bin/
            quux                   (installed command)
        pkg/
            linux_amd64/
                foo/
                    bar.a          (installed package object)
```

# 0: Hello world

Welcome to: A Little Go App!
---
Let's test the installation of Go to make sure everything is set up!


```go
package main

import "fmt"

func   main() {
    fmt.Println(  "hello, world!"  );
    }
```

Compile it with the go tool:
```$ go install github.com/user/hello```

Note that you can run this command from anywhere on your system. The go tool finds the source code by looking for the `github.com/user/hello` package inside the workspace specified by `GOPATH`.

The go tool will only print output when an error occurs, so if these commands produce no output they have executed successfully!!

The command above will put an executable command named `hello` inside the bin directory of your workspace. Execute the command to see the greeting:

```
$ $GOPATH/bin/hello
hello, world
```

If you see "hello, world" then your Go installation is working. Awesome.
If not. Well. Whoops!

You should be able to understand every line of this program.
If you do not it's probably time to check out the [Go tour][1].

## Running your code

At this point you can paste the code above into a file named `main.go`.
This file should be anywhere in your `$GOPATH`.
I will assume it is inside of a folder with path `$GOPATH/hello/main.go`.

You can now run the code in a couple of ways. From the directory containing `main.go` run:

- `go run main.go` compiles and runs only `main.go`.

- `go build` compiles the code in the current directory and generates a binary named `hello` in the current directory.

- `go install` compiles the code in the current directory and generates a binary named `hello` in `$GOPATH/bin`.

## Formatting your code: gofmt

If you're used to seeing some Go code you might have noticed that this code is not formatted in a standard way.

Try running `gofmt main.go` and you'll see what the output should look like.
You can run `gofmt -d main.go` to see how the file differs from the formatted version.
And finally you can run `gofmt -w main.go` to simply rewrite the file with its formatted version.

## Managing import statements: goimports

The import statements at the beginning of the program are needed for the compiler to know what packages you use.
But this doesn't mean you need to write them yourself!

Try deleting the line `import "fmt"` from `main.go` and run it, you should see an error:

```
    $ go run main.go
    # command-line-arguments
    ./main.go:5: undefined: fmt in fmt.Println
```

You can fix this error by manually adding the missing import statements or using `goimports`.

If you don't have `goimports` installed in your machine you can easily install it by running:

```
    $ go get golang.org/x/tools/cmd/goimports
```

This will install the `goimports` binary in `$GOAPTH/bin`.
It is basically the equivalent to fetching the code from GitHub and then running `go install`.

You can now run `goimports` as a replacement of `gofmt`.
`goimports` formats your code *and* fixes your imported package list adding missing ones and removing those unused.

Similarly to `gofmt` you can run:

- `goimports main.go` to see what the fixed file would look like.
- `goimports -d main.go` to see the difference between the current and fixed versions.
- `goimports -w main.go` to rewrite the file with its fixed version.

## Making your life easier

`gofmt` and `goimports` are just two of the tools that you might use to make your life easier.
To have those and more invoked everytime you save your file you should consider adding a plugin to your favorite editor.
I personally love [vim][2] with [vim-go][3] and I'm also using [VS Code][4] with its Go plugin.
But there's many more editors with Go support, you can find them [here][5].

# Congratulations!

You're done with section ... zero. Well, we need to start somewhere!
But hey, at least now you're ready to tackle [section 1][6].

[1]: https://tour.golang.org
[2]: http://www.vim.org/
[3]: https://github.com/fatih/vim-go
[4]: https://www.visualstudio.com/en-us/products/code-vs.aspx
[5]: https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins
[6]: ../section01/README.md
