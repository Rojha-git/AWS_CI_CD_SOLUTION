# AWS_CI_CD_SOLUTION
it's an common solution for Applications/Microservices on AWS Cloud

## Introduction
This repository provides a step-by-step guide for building and deploying a Simple application using Node JS. The guide covers setting up infrastructure on AWS, configuring AWS-Codepipeline for CI/CD, deploying application on ECS cluster and exposing the application by ALB to the external world.

## Prerequisites
Before you begin, make sure you have the following prerequisites:
- AWS account
- GitHub account

## step-by-step guide :

1. Launch an EC2 instance on AWS and install docker and AWS-CLI on instance.

    ```bash

    sudo apt-get update
    sudo apt install awscli
    sudo apt install docker.io

    ```
2. Create an user under IAM and provide the policy for ec2ContainterRegistryFullAccess, ec2FullAccess etc like below, after that generate Access key and authenticate EC2 using
    "aws configure"
   ![IAM-IMAGE](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/aws_iam_policy.PNG)



4. Clone the git repo on your ec2 instance and after that you need to run the command to authenticate ECR, build and push the docker image to ECR registery.

   ![ECR-IMAGE](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/ECR_image.PNG)
   ![ECR-IMAGE](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/Capture1.PNG)

6. Need to create an ecs cluster, task defination using above ECR where we already pushed the docker image, after that we need to create service to expose the application in load balancer mode, which will provide an dns to us and we can expose the application by that url.

   ![ECS_IMAGE](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/Capture2.PNG)

   ![ECS_IMAGE](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/Capture3.PNG)


7. Create AWS-CodeCommit repo and connect this repo using ec2 instance and push the content to codecommit repo so that we can use it in AWS-Codepipeline, for pushing the content you have to authenticate the aws-codecommit by ec2 using access token which you have to genearte from IAM section.

   ![CODE_COMMIT](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/Capture5.PNG)
   

9. need to create an project under code-bulid which will use buildsec.yml file for building the application.

   ![Code_Build](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/Capture8.PNG)

11. We have to create an code-pipeline which will contain all the stages like it will use code-commit, code-build and code-deploy to this CI-CD solution, here code deploy will deploy your application to provided target like ECS cluster.
  ![nnfff](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/Capture6.PNG)
  ![f](https://github.com/Rojha-git/AWS_CI_CD_SOLUTION/blob/main/images/Capture7.PNG)

   
     
   




    

    
