## Introduction
This program reads report data from an API host with bearer auth, then compose a message and post to Slack channel 
- The structs are just examples. You can craft your own structs or generate them via tools such as https://mholt.github.io/json-to-go/  

Two versions:
- a Lambda function to be called by AWS EventBridge Rules (previously known as CloudWatch Schedule)
- a local executable program

## Build
### install dependencies
- go get github.com/joho/godotenv
- go get github.com/aws/aws-lambda-go/lambda  

### define vars in .env file
```shell
API_HOST=
API_TOKEN=
SLACK_CHANNEL=
```  

### build for Lambda 
- don't forget to include the .env in zip package; it's not there by default
```shell
cd http-w-lambda
GOOS=linux GOARCH=amd64 go build -o main main.go                                  
zip <function-name>.zip main .env
```

### on Mac: run 
- go run main.go  