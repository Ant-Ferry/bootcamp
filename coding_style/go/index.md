# Go Style 

## Guides

Basicly we follow the official documentation and guides.  

- [Effective Go](./effective_go.md) [[source]](https://golang.org/doc/effective_go.html)
- [Go Code Review Comments](./go_code_review_comments.md) [[source]](https://github.com/golang/go/wiki/CodeReviewComments)

__*P.S. Make sure that you go through the whole listed docs*__

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
