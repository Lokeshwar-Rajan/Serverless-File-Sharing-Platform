# Building-A-Serverless-File-Sharing-Platform

### Description:

I built a Serverless File Sharing Platform that enables users to securely upload and download files through a straightforward HTTP API. This platform uses AWS Lambda for serverless compute, API Gateway for managing RESTful APIs, and Amazon S3 for scalable and durable object storage.

Uses:

- File Sharing
- Collaborative Work

### Architecture:

<img width="1132" alt="Architecture" src="https://github.com/Lokeshwar-Rajan/Serverless-File-Sharing-Platform/blob/ff6b80b4c43406ebb9ae4cc89737fd029f6f7e93/ServerLess%20File%20Sharing%20Platform.png">

### Here's Step by Step Guide:

* Step 1: Create an S3 bucket to store uploaded files
* Step 2 : Create Upload and Download Lambda Functions with required execution role with necessary IAM Role for S3.
* Step 3 : Create an API Gateway with POST and GET Methods and integrate it with the lambda functions.
* Step 4 : Configure GET Method

  ```bash
  {
    "queryStringParameters": {
        "fileName": "$input.params('fileName')"
    }
  }
  ```
  
* Step 5 : Configure POST Method

  ```bash
  {
    "body" : "$input.body",
    "queryStringParameters" : {
        "fileName" : "$input.params('fileName')"
    }
  }
  ```

* Step 6 : Now Deploy the API Gateway.
* Step 7 : Test the application using a third party client such as Postman

    --> Upload  File  --> POST to https://.execute-api..amazonaws.com/dev/files?fileName=test.txt

    --> Download  File -> GET to https://.execute-api..amazonaws.com/dev/files?fileName=test.txt
