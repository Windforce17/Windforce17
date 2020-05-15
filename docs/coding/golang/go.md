## 交叉编译

```bash
#linux x64
CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build
# win x64
CGO_ENABLED=0 GOOS=windows GOARCH=amd64 go build
# mac x64
CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build
# 32bit GOARCH=386
```

## vscode 需要的包

go get -u -v github.com/rogpeppe/godef
go get -u -v github.com/sqs/goreturns
go get -u -v golang.org/x/lint/golint

## 常用包

1. https://github.com/urfave/cli
   A simple, fast, and fun package for building command line apps in Go
2. gopkg.in/yaml.v2
   yaml decoder
