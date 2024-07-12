Serverless Web Application with AWS Lambda, API Gateway, DynamoDB, and S3
This project demonstrates how to build a serverless web application using AWS services like Lambda, API Gateway, DynamoDB, and S3. The application allows users to interact with a web interface hosted on S3 and perform CRUD operations on a DynamoDB table through API Gateway and Lambda.

Table of Contents
Prerequisites
Architecture
Setup Instructions
Step 1: Clone the Repository
Step 2: Deploy the CloudFormation Stack
Step 3: Upload Static Files to S3
Step 4: Configure S3 Bucket for Public Access
Step 5: Update index.html to Call API
Step 6: Verify the Application
Cleanup
License
Prerequisites
Before you begin, ensure you have the following prerequisites:

An AWS account with appropriate permissions to create and manage resources such as S3, Lambda, API Gateway, DynamoDB, and IAM.
AWS CLI installed and configured with your AWS credentials.
Basic knowledge of AWS services and serverless architecture.
Architecture
The architecture of this serverless web application consists of the following components:

Amazon S3: Hosts the static website files (HTML, CSS, JavaScript).
AWS Lambda: Contains the backend logic to interact with DynamoDB.
Amazon API Gateway: Exposes the Lambda functions as RESTful APIs.
Amazon DynamoDB: Stores the application data.
Setup Instructions
Step 1: Clone the Repository
Clone the repository to your local machine:

git clone https://github.com/cloudsolutionstech/serverless-web-app.git
cd serverless-web-app
After you cd, you should see a yaml file "serverless-app.yml" The file contains AWS CloudFormation Template to create a serverless web application.

Step 2: Deploy the CloudFormation Stack
Open the AWS Management Console and navigate to the CloudFormation service.
Click "Create stack" and select "With new resources (standard)".
Upload the serverless-app.yml file by selecting "Upload a template file" and then choosing the file from your local system.
Follow the prompts to configure stack options such as stack name and parameters. Click "Next" to proceed through the setup.
Review your settings and click "Create stack" to launch the stack creation process.
Step 3: Upload Static Files to S3
After the CloudFormation stack is created, upload your static files to the S3 bucket created by CloudFormation.

Open the AWS S3 console.
Select the bucket created by CloudFormation (it should have a name like my-serverless-webapp-bucket-).
Click the "Upload" button and upload your index.html and any other static files (e.g., styles.css).
You can use this example below.
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Serverless App Automation</title>
</head>
<body>
    <h1>Welcome to Cloud Solutions Tech Serverless App Project</h1>
    <div id="content"></div>
    <script src="app.js"></script>
</body>
</html>
Step 4: Configure S3 Bucket for Public Access
Go to the S3 Console:
Open the AWS Management Console.
Navigate to the S3 service.
Select Your Bucket:
Find and select the bucket created by CloudFormation.
Go to the Permissions Tab:
Click on the "Permissions" tab.
Edit the Bucket Policy:
Under "Bucket Policy," click "Edit."
Add a Bucket Policy:
Add the following bucket policy to allow public read access to your bucket:
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::my-serverless-webapp-bucket-<account-id>/*"
    }
  ]
}
Replace my-serverless-webapp-bucket- with your actual bucket name.
Click "Save changes."
Public Access Settings:
Still in the "Permissions" tab, go to "Block public access (bucket settings)" and click "Edit."
Uncheck the "Block all public access" option.
Confirm by clicking "Save."
Set Public Permissions for Objects:
Navigate to the "Objects" tab in your S3 bucket.
Select the files (e.g., index.html, styles.css).
Click on the "Actions" button and select "Make public."
Confirm the action.
Step 5: Update index.html to Call API
Update your index.html file to use the API Invoke URL from the CloudFormation output. Here's an example index.html:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Serverless Web App</title>
</head>
<body>
    <h1>Serverless Web App</h1>
    <div id="content"></div>
    <script>
        const apiUrl = 'https://YOUR_API_ID.execute-api.YOUR_REGION.amazonaws.com/prod/items'; // Replace with the actual URL from CloudFormation output

        async function fetchItems() {
            const response = await fetch(apiUrl);
            const items = await response.json();
            const contentDiv = document.getElementById('content');
            items.forEach(item => {
                const itemDiv = document.createElement('div');
                itemDiv.textContent = JSON.stringify(item);
                contentDiv.appendChild(itemDiv);
            });
        }

        fetchItems();
    </script>
</body>
</html>
Step 6: Verify the Application
Access the S3 Bucket URL:
Go to the CloudFormation console.
Select your stack and go to the "Outputs" tab.
Find the WebsiteURL output and click on the URL to open your web application.
Verify Functionality:
Ensure that the web application loads correctly.
Verify that the API calls to DynamoDB work as expected by interacting with the web application.
By following these steps, you will have successfully automated the deployment of your serverless web application using AWS CloudFormation, Lambda, API Gateway, DynamoDB, and S3.

Cleanup
To clean up the resources created by this project, delete the CloudFormation stack:

Open the AWS Management Console and navigate to the CloudFormation service.
Select your stack and click "Delete".
Confirm the deletion to clean up all the resources created by the stack.
License
This project is licensed under the MIT License. See the LICENSE file for details.

This README.md provides a clear and detailed guide for setting up, verifying, and cleaning up the serverless web application. Make sure to replace placeholders such as YOUR_API_ID and YOUR_REGION with the actual values from your CloudFormation outputs.

Additional Resources
AWS Lambda Documentation API Gateway Documentation DynamoDB Documentation S3 Documentation CloudFormation Documentation
