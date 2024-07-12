# Serverless Web Application with AWS Lambda, API Gateway, DynamoDB, and S3

This project  build a serverless web application using AWS services like Lambda, API Gateway, DynamoDB, and S3. The application allows users to interact with a web interface hosted on S3 and perform CRUD operations on a DynamoDB table through API Gateway and Lambda.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Architecture](#architecture)
- [Setup Instructions](#setup-instructions)
  - [Step 1: Clone the Repository](#step-1-clone-the-repository)
  - [Step 2: Deploy the CloudFormation Stack](#step-2-deploy-the-cloudformation-stack)
  - [Step 3: Upload Static Files to S3](#step-3-upload-static-files-to-s3)
  - [Step 4: Configure S3 Bucket for Public Access](#step-4-configure-s3-bucket-for-public-access)
  - [Step 5: Update `index.html` to Call API](#step-5-update-indexhtml-to-call-api)
  - [Step 6: Verify the Application](#step-6-verify-the-application)
- [Cleanup](#cleanup)
- [License](#license)


## Architecture

The architecture of this serverless web application consists of the following components:
- **Amazon S3**: Hosts the static website files (HTML, CSS, JavaScript).
- **AWS Lambda**: Contains the backend logic to interact with DynamoDB.
- **Amazon API Gateway**: Exposes the Lambda functions as RESTful APIs.
- **Amazon DynamoDB**: Stores the application data.


