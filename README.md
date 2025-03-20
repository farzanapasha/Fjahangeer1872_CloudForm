# Automated Infrastructure Deployment with AWS CloudFormation and CodePipeline

## Objective

Automated Infrastructure Deployment with AWS CloudFormation and CodePipeline

## Lab Requirement

### 1. Create a Simple CloudFormation Template
- Define a CloudFormation template in **YAML** or **JSON** format
- Test the Template locally using the AWS CLI command:  
  ```bash
  aws cloudformation validate-template --template-body file://s3_cloudformtemp.yaml

  ## **Step 2: Set Up GitHub Repository**
1. Create a **new GitHub repository**.
2. Clone the repository and push the CloudFormation template:
   ```sh
   git clone https://github.com/your-username/aws-cloudformation-pipeline.git
   cd aws-cloudformation-pipeline
   git init
   git add s3_cloudformtemp.yaml
   git commit -m "Initial commit - CloudFormation template for S3 bucket"
   git branch -M main
   git remote add origin https://github.com/your-username/aws-cloudformation-pipeline.git
   git push -u origin main
   ```

---

## **Step 3: Configure AWS CodePipeline**
1. **Go to AWS Console → CodePipeline**.
2. **Create a new pipeline**:
   - Source: **GitHub repository** (monitor `main` branch)
   - Deploy: **AWS CloudFormation** (use `s3_cloudformtemp.yaml` as the template)
3. **Enable automatic triggers** for each push to the repository.

---

## **Step 4: Automate Deployment Trigger & Testing**
### **Make a change to trigger the pipeline**
Edit the CloudFormation template to add a **new AWS resource**, default parameter

```yaml
   BucketName:
    Type: String
    default: s3-nk-bt1-fjahangeer1872
    Description: The name of the S3 bucket 1
```

Push the changes to GitHub:
```sh
git add s3_cloudformtemp.yaml
git commit -m "Added"
git push origin main
```

The pipeline should trigger automatically and deploy the updated stack.

---

## **Step 5: Verify & Cleanup**
- Check AWS **CloudFormation Console** and verify S3 bucket
- To avoid extra costs, delete stack
  ```sh
  aws cloudformation delete-stack --stack-name YourStackName
  ```

  
