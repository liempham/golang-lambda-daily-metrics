## Introduction
This program reads data from an API, then compose a message and post to Slack channel  

## Build
### install dependencies
- go get github.com/joho/godotenv
- go get github.com/aws/aws-lambda-go/lambda  

### build for Lambda 
- don't forget to include the .env in zip package; it's not there by default
```shell
GOOS=linux GOARCH=amd64 go build -o main main.go                                  
zip <function-nam>.zip main .env
```

### on Mac: run 
- go run main.go  
- or build with: GOOS=darwin GOARCH=amd64 go build -o main main.go
  
  
### other notes
#note: inside main.go - define the package "main"
- go mod init main.go
- go mod tidy