# Go 

<p align="center">
<img src="./img/gopher.png" width="15%" align="right">

- [Guides](#guides)
- [Vendor](#vendor)
- [Go Meta Linter](#go-meta-linter)
- [IDE & TextEditorPlugin](#ide-texteditorplugin)
</p>

## Guides

Basicly we follow the official documentation and guides.  

- [Official Go Wiki [source]](https://github.com/golang/go/wiki)
- [Effective Go](./effective_go.md) [[source]](https://golang.org/doc/effective_go.html)
- [Go Code Review Comments](./go_code_review_comments.md) [[source]](https://github.com/golang/go/wiki/CodeReviewComments)

__*P.S. Make sure that you go through the whole listed docs*__

## Vendor

Go manages dependencies by using [Vendor Directories](https://golang.org/cmd/go/#hdr-Vendor_Directories):

> Go 1.6 includes support for using local copies of external dependencies to satisfy imports of those dependencies, often referred to as vendoring.
> 
> Code below a directory named "vendor" is importable only by code in the directory tree rooted at the parent of "vendor", and only using an import path that omits the prefix up to and including the vendor element.
> 
> Here's the example from the previous section, but with the "internal" directory renamed to "vendor" and a new foo/vendor/crash/bang directory added:
> 
> ```
> /home/user/go/
>     src/
>         crash/
>             bang/              (go code in package bang)
>                 b.go
>         foo/                   (go code in package foo)
>             f.go
>             bar/               (go code in package bar)
>                 x.go
>             vendor/
>                 crash/
>                     bang/      (go code in package bang)
>                         b.go
>                 baz/           (go code in package baz)
>                     z.go
>             quux/              (go code in package main)
>                 y.go
> ```
> 
> The same visibility rules apply as for internal, but the code in z.go is imported as "baz", not as "foo/vendor/baz".
> 
> Code in vendor directories deeper in the source tree shadows code in higher directories. Within the subtree rooted at foo, an import of "crash/bang" resolves to "foo/vendor/crash/bang", not the top-level "crash/bang".
> 
> Code in vendor directories is not subject to import path checking (see 'go help importpath').
> 
> When 'go get' checks out or updates a git repository, it now also updates submodules.
> 
> Vendor directories do not affect the placement of new repositories being checked out for the first time by 'go get': those are always placed in the main GOPATH, never in a vendor subtree.
> 
> See [https://golang.org/s/go15vendor](https://golang.org/s/go15vendor) for details.

We handle vendor by using [govendor](github.com/kardianos/govendor). 

## Go Meta Linter 

[Go Meta Linter](https://github.com/alecthomas/gometalinter) is a Go integration static check tool, which can concurrently run Go lint tools and normalise their output.

Following are the normal parameters we specify:

```bash
gometalinter \
    --cyclo-over=15 \
    --json \
    --deadline=5m \
    --vendor \
    --disable=gotype \
    --linter='gas:gas -exclude=G101 -fmt=csv  {path}/*.go:^(?P<path>.*?\.go),(?P<line>\d+),(?P<message>[^,]+,[^,]+,[^,]+)' \
```

- cyclo-over 

    The upper threshold cyclomatic complexities checking of functions in Go source code. Learn more in [gocyclo](https://github.com/alecthomas/gocyclo). Keep it under 15 please.

- deadline

    Some linter may take a long time to run so make sure the deadline is long enough.

- disable

    Normally we disable [gotype](https://godoc.org/golang.org/x/tools/cmd/gotype), which will cause the type check missing in vendor. 

- linter

    In some special cases we will customize some linter like [GAS](https://github.com/GoASTScanner/gas). __*Make sure you know exactly what you're doing before apply your customization*__

__*All pull request to major branches shall pass the Go Meta Linter validation before being pushed to the remote repository, otherwise it will fail the static validation in our Continous Integration, which means the PR will be rejected.*__

## IDE & TextEditorPlugin

Coding tools vary between developers in team and the listed are mostly used:


* **[Gogland](https://www.jetbrains.com/go/)**: Jetbrains Golang IDE

* **[Intellij IDEA](http://www.jetbrains.com/idea/)**: Commercial cross-platform IDE, [free Community Edition available](http://www.jetbrains.com/idea/download/index.html). [Open-Source plugin for Go](https://plugins.jetbrains.com/plugin/?id=5047) support available. All derivative platforms of IntelliJ (PyCharm, PhpStorm et al.) are supported. Nightly / alpha builds available at [plugin repository](https://github.com/go-lang-plugin-org/go-lang-idea-plugin)

* **[Visual Studio Code](https://code.visualstudio.com/)**: Free & open source IDE by Microsoft. Visual Studio Code supports Go syntax highlighting out of the box. Additional features are provided by the [vscode-go](https://github.com/Microsoft/vscode-go) plugin.

* **[Atom](http://www.atom.io)**: JavaScript-based editor from GitHub. Go support at [go-plus](https://github.com/joefitzgerald/go-plus)

* **[Emacs](https://www.gnu.org/software/emacs/)**: Extensible and customizable text editor.
    * Mode file maintained at https://github.com/dominikh/go-mode.el.
    * [GoFlyMake](https://github.com/dougm/goflymake) Flymake-style syntax checking for Go
    * [go-errcheck.el](https://github.com/dominikh/go-errcheck.el) Errcheck integration for Emacs

* **[Vim](http://www.vim.org/)** & **[Neovim](https://neovim.io/)**: Vi Improved. There are a number of plugins available that make editing Go code easier.
    * The [vim-go](https://github.com/fatih/vim-go) plugin includes misc/vim and has many other new improvements.
    * The [Syntastic](https://github.com/scrooloose/syntastic) plugin gives instant feedback on compile errors
    * The [tagbar](https://github.com/majutsushi/tagbar) plugin uses Gotags, above, to show an outline of the current file
    * A [vim compiler plugin](https://github.com/rjohnsondev/vim-compiler-go) for syntax checking
    * A [vim-godef](https://github.com/dgryski/vim-godef) plugin integrates with the 'godef' tool, above
    * A [vim-go-extra](https://github.com/vim-jp/vim-go-extra) is vim plugin based on misc/vim in go repository. This works fine on windows too!

Check [this](https://github.com/golang/go/wiki/IDEsAndTextEditorPlugins) out for more alternates.

## More

Go get the gopher!

<img src="./img/spiderbunnys.jpg" width="50%">

by [Renee French](http://reneefrench.blogspot.com/)