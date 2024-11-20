# CloudFormation Project for AWS

This CloudFormation template sets up a simple AWS infrastructure that integrates **S3**, **Lambda**, and **EventBridge**. The resources created can be used for a variety of purposes such as automating file creation in an S3 bucket and running Lambda functions on a scheduled basis. ⚙️

## What This Template Creates

### 🪣 **S3 Bucket**
- A **private** S3 bucket is created to store files.
- Public access is blocked for security, and the bucket is encrypted with **AES-256**.
- **Versioning** is enabled to keep track of file changes.

### 🧑‍💻 **Lambda Function**
- A **Python Lambda function** that creates a new file in the S3 bucket every time it runs.
- The Lambda function is set to trigger at a regular interval (every 5 minutes) using **EventBridge**.

### 🔑 **IAM Roles and Policies**
- **IAM Role for Lambda**: Grants the Lambda function permission to write logs and interact with other AWS services.
- **IAM Role for EventBridge**: Allows EventBridge to invoke the Lambda function.
- **IAM Policy for Lambda**: Ensures the Lambda function can access the S3 bucket.

### 🕰️ **EventBridge**
- An **EventBridge rule** that triggers the Lambda function every 5 minutes based on a cron schedule.
- This enables automation of the file creation process without manual intervention.

### 📑 **CloudWatch Logs**
- A **CloudWatch Log Group** is created to capture the logs from the Lambda function, which will be kept for 7 days. 
## Outputs

After the CloudFormation stack is deployed, the following resources will be available:

- **S3 Bucket**: The S3 bucket where files are stored.
- **Lambda Execution Role**: The IAM role for Lambda to interact with AWS services.
- **Lambda Access Policy**: The IAM policy granting Lambda access to the S3 bucket.
- **Lambda Log Group**: The location where Lambda logs are stored in CloudWatch.
- **Lambda Function**: The Lambda function that runs periodically to create files in S3.
- **EventBridge Role**: The IAM role allowing EventBridge to invoke the Lambda function.
- **Lambda Function Schedule**: The EventBridge rule that triggers the Lambda function every 5 minutes.
- **Lambda CloudWatch Permission**: The permission allowing EventBridge to invoke the Lambda function.

## 🌟 Key Features
- **Automation**: Lambda runs automatically based on a schedule, creating files in S3 every 5 minutes.
- **Security**: The S3 bucket is private, and access is securely managed through IAM roles and policies.
- **Monitoring**: Logs from the Lambda function are stored in CloudWatch for easy monitoring and troubleshooting.

This setup is great for automating tasks like file uploads, logging, and periodic function invocations. It can be expanded to suit more complex workflows as needed! 🚀
