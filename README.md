# ecr-swarm-ci
Deploy on Docker swarm from ECR via CircleCI (Example Project)

## Description

This is  an example of how to build and test a Dockerized web application on CircleCI, push to an AWS EC2 Container Registry, and then deploy on Docker swarm.


## Prerequisites

* Configure a few CircleCI environment variables before the deploy script will work
```
AWS_ACCOUNT_ID  *your aws account id
AWS_ACCESS_KEY_ID *your aws access key id
AWS_SECRET_ACCESS_KEY *your aws secret access key
AWS_DEFAULT_REGION *aws default region
CA_PEM *Trust certs signed only by this CA (s3 bucket path  (ex. s3://mybucket/myca)) 
CERT_PEM *TLS certificate (s3 bucket path (ex. s3://mybucket/mycert))
KEY_PEM *TLS key (s3 bucket path (ex. s3://mybucket/mykey))
DOCKER_DIRECTORY *directory path which contains php code
SERVER_IP *ip or hostname of the server that docker swarm running
```
*Create a CA, server and client keys with OpenSSL
https://docs.docker.com/engine/security/https/ 

* EC2 Container Registry must already be set up on AWS
* Docker swarm cluster must already be created on your server
* php code must already be created on your server
* put certificate files in s3 bucket

## Usage
CircleCI automatically runs your build and test processes, and push image to ECR, deploy on Docker swarm from ECR when you update docker-compose*.yml or Dockerfile.
