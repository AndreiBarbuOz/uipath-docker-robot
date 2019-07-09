# Dockerized robot build CFN template

CFN template used to build an UiPath robot in a Docker container
![docker-robot-build](img/dockerized-robot-build.png)

## Prerequisites

* AWS account with appropriate Role
* A Key pair for accessing the provisioned instance is needed

## Purpose

The stack described in the CFN template provisions the necessary infrastructure to build a `Docker` image containing the UiPath robot and PowerShell module needed to communicate with Orchestrator

For this, an EC2 instance is launched and during its launch script, the [dockerized-robot repository](https://github.com/AndreiBarbuOz/dockerized-robot) is downloaded and the script is run

## Deployment

To build the docker image, there are 2 steps involved:
1. Create the Docker Repo stack from command line:

```cmd
aws cloudformation create-stack --stack-name docker-image-repo --template-body file://docker-repo.yaml 
```
2. Create the Docker image build stack: 

```cmd
aws cloudformation create-stack --stack-name docker-build --template-body file://docker-build.yaml --parameters file://docker-build-params.json --capabilities CAPABILITY_IAM
```

*The total time it takes to build the Docker image is around 30 minutes.*

