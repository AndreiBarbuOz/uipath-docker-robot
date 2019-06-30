# Dockerized robot deployment into AWS using CloudFormation templates

Basic UiPath robot in a Docker container

## Prerequisites

* AWS account with appropriate Role
* A Key pair for accessing the provisioned instance is needed

## Deployment

Deploying the server contains 2 steps:
1. Deploy the prerequisites (the VPC with all components and the username/password combination)
```cmd
aws cloudformation create-stack --stack-name docker-build --template-body file://docker-build.yaml --parameters file://docker-build-params.json --capabilities CAPABILITY_IAM
```

