# Automated Infrastructure Deployment with AWS CloudFormation and CodePipeline

## Objective

This project sets up an automated CI/CD pipeline using AWS CodePipeline that provisions AWS resources using CloudFormation. The pipeline will deploy an S3 bucket as part of the infrastructure automation process.

## Lab Requirements

### 1. Create a Simple CloudFormation Template
- Define a CloudFormation template in **YAML** or **JSON** format.
- The template will create an **S3 bucket** with parameters for:
  - **Bucket name**
  - **Versioning (enabled/disabled)**
- **Test the Template** locally using the AWS CLI command:  
  ```bash
  aws cloudformation validate-template --template-body file://s3_cloudformtemp.yaml