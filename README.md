# Serverless Web Application with AWS Lambda, API Gateway, DynamoDB, and S3

This project  build a serverless web application using AWS services like Lambda, API Gateway, DynamoDB, and S3. The application allows users to interact with a web interface hosted on S3 and perform CRUD operations on a DynamoDB table through API Gateway and Lambda.

## Table of Contents
- [Architecture]
- [Setup Instructions]
  - [Step 1: Clone the Repository]
  - [Step 2: Deploy the CloudFormation Stack]
  - [Step 3: Upload Static Files to S3]
  - [Step 4: Configure S3 Bucket for Public Access]
  - [Step 5: Update `index.html` to Call API]
  - [Step 6: Verify the Application]
- [Cleanup](#cleanup)
- [License](#license)


## Architecture

The architecture of this serverless web application consists of the following components:
- **Amazon S3**: Hosts the static website files (HTML, CSS, JavaScript).
- **AWS Lambda**: Contains the backend logic to interact with DynamoDB.
- **Amazon API Gateway**: Exposes the Lambda functions as RESTful APIs.
- **Amazon DynamoDB**: Stores the application data.


