Serverless Voting Application
A cloud-native application that leverages serverless architecture and various AWS services to provide a seamless and scalable voting experience for programming languages.

Features
Interactive Frontend: A dynamic user interface built with React for a smooth user experience.

View a list of programming languages.

See real-time vote counts.

Cast your vote with a single click.

Serverless Backend: The application's logic is powered by AWS Lambda functions, which execute only when needed, ensuring a pay-per-use pricing model and automatic scaling.

Handles API requests for getting languages and submitting votes.

No servers to provision or manage.

API Management: AWS API Gateway provides a secure and managed entry point for the frontend to interact with the Lambda functions.

Exposes backend functionality as a set of REST APIs.

Manages request routing, security, and throttling.

Data Persistence: AWS DynamoDB, a highly scalable NoSQL database, is used for storing and retrieving all application data.

Stores the list of programming languages and their vote counts.

Ensures fast and reliable data access at any scale.

Infrastructure as Code (IaC): The entire application infrastructure is defined and deployed using AWS SAM (Server Application Model).

The template.yaml file defines all AWS resources, ensuring repeatable and consistent deployments.

Simplifies development and CI/CD workflows.

Security and Monitoring:

AWS IAM roles provide secure access management, granting each service only the permissions it needs.

CORS is configured to allow secure communication between the frontend and API Gateway.

AWS CloudWatch provides comprehensive monitoring and logging for troubleshooting and performance analysis.

Technologies Used
Frontend: React

Backend: AWS Lambda, AWS API Gateway, AWS DynamoDB

IaC: AWS SAM

Security & Monitoring: AWS IAM, AWS CloudWatch

Getting Started
Follow these steps to get the application up and running on your own AWS account.

Prerequisites
An AWS Account.

The AWS CLI configured with your credentials.

Node.js and npm installed.

AWS SAM CLI installed.

1. Clone the repository
Bash

git clone <repository_url>
cd serverless-voting-app
2. Install dependencies
Navigate to the frontend and backend directories and install the required dependencies.

Bash

# Install frontend dependencies
cd frontend
npm install

# Install backend dependencies
cd ../backend
npm install
3. Deploy the application
The AWS SAM CLI automates the build and deployment process.

From the root directory of the project, run the SAM build command. This command will compile the Lambda functions and prepare the deployment package.

Bash

sam build
Deploy the application to your AWS account. You will be prompted to enter a Stack Name and AWS Region.

Bash

sam deploy --guided
Stack Name: A unique name for your CloudFormation stack (e.g., ServerlessVotingApp).

AWS Region: Choose the AWS region where you want to deploy the application (e.g., us-east-1).

Follow the on-screen prompts. SAM will handle the creation of the S3 bucket, API Gateway, Lambda functions, and DynamoDB tables.

4. Configure the frontend
After a successful deployment, the sam deploy command will output the API Gateway Endpoint URL. You need to add this URL to your React frontend so it can communicate with the backend.

Copy the ApiGatewayUrl from the deployment output.

Navigate to the frontend directory.

Create a .env file in the frontend directory.

Add the API Gateway URL to the file in the following format:

Bash

# frontend/.env
REACT_APP_API_URL=<Your_ApiGatewayUrl_Here>
5. Run the frontend application
Now you can start the React development server to view the application.

Bash

# In the frontend directory
npm start
Your web browser will automatically open a new tab with the application running at http://localhost:3000.

Clean Up
To avoid incurring future costs, you can easily delete the entire application stack using the AWS CLI.

Bash

# Replace with the stack name you chose during deployment
aws cloudformation delete-stack --stack-name <Your_Stack_Name>
This project was created as a demonstration of serverless architecture and is intended for educational purposes.

Created by R.
