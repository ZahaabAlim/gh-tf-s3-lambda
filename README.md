
# Deploy Terraform

This repository contains a GitHub Actions workflow to deploy infrastructure using Terraform. The workflow automates the process of setting up AWS resources, specifically an AWS Lambda function, using Terraform configurations.

## Workflow Overview

The GitHub Actions workflow is triggered on every push to the `main` branch. It performs the following steps:

1. **Checkout Code**: Checks out the repository code.
2. **Set up Terraform**: Sets up Terraform with the specified version.
3. **Configure AWS Credentials**: Configures AWS credentials using secrets stored in GitHub.
4. **Initialize Terraform**: Initializes the Terraform configuration.
5. **Generate Terraform Plan**: Generates a Terraform execution plan.
6. **Apply Terraform**: Applies the Terraform configuration to create or update the infrastructure.

## Terraform Configuration

### main.tf

Defines the AWS provider, backend configuration, and resources to be created:

- **AWS Provider**: Specifies the AWS region.
- **Backend Configuration**: Configures the S3 bucket for storing the Terraform state file.
- **AWS Lambda Function**: Creates an AWS Lambda function with the specified S3 bucket, S3 key, handler, runtime, and IAM role.
- **IAM Role**: Creates an IAM role for the Lambda function with the necessary assume role policy.

### terraform.tfvars

Specifies the values for the variables used in the Terraform configuration:

- `s3_bucket`: The name of the S3 bucket for deployment.
- `s3_key`: The name of the ZIP file in the S3 bucket.
- `lambda_handler`: The Lambda function handler name.

### variables.tf

Defines the variables used in the Terraform configuration:

- `s3_bucket`: Description and type of the S3 bucket variable.
- `s3_key`: Description and type of the S3 key variable.
- `lambda_handler`: Description and type of the Lambda handler variable.

## Usage

1. **Set up Secrets**: Add your AWS credentials (`AWS_ACCESS_KEY` and `AWS_SECRET_ACCESS_KEY`) as secrets in your GitHub repository.
2. **Push to Main Branch**: Push your changes to the `main` branch to trigger the workflow.
3. **Monitor Workflow**: Monitor the GitHub Actions workflow to ensure successful deployment.

## Summary

This repository automates the deployment of an AWS Lambda function using Terraform and GitHub Actions. By following the steps outlined in this `README.md`, you can easily set up and manage your infrastructure as code.
