# Dockerized robot deployment into AWS using CloudFormation templates

Basic UiPath robot in a Docker container

## Prerequisites

* AWS account with appropriate Role
* A Key pair for accessing the provisioned instance is needed

## Deployment

Deploying the server contains 2 steps:
1. Deploy the prerequisites (the VPC with all components and the username/password combination)
```cmd
aws cloudformation create-stack --stack-name docker-build --template-body file://prereq.yaml --parameters file://prereq-params.json
```


Update the stack using: 
```cmd
aws cloudformation update-stack --stack-name node-red --template-body file://linux-node-red.yaml --parameters file://node-red-params.json
```

## Configuration

`node-red` is configured using a `settings.js` file. The default file can be found [here](https://github.com/node-red/node-red/blob/master/packages/node_modules/node-red/settings.js)

