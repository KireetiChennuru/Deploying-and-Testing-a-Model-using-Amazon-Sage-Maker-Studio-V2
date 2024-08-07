
### Explanation:
- **AWS CLI Section**: Added a detailed section under the "Deploy the Model in Amazon SageMaker Inference Endpoint" step that explains how to use AWS CLI commands for deployment.
- **Commands Included**:
  - `aws s3 ls` to list S3 buckets.
  - Commands for uploading artifacts, creating the model, endpoint configuration, deploying the endpoint, and checking the status.

This addition will provide a comprehensive guide for users who prefer or need to use AWS CLI for model deployment on SageMaker.




https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/Cloud%20Architecture.jpeg?raw=true

Add a section after project overview and name that as Architecture Diagram and add the above image
ChatGPT
Here’s the updated project report with the new "Architecture Diagram" section, including the specified image:

Updated Markdown Code:
markdown
Copy code
# Deploying and Testing a Model using Amazon SageMaker Studio

## Project Overview

This project focuses on deploying and testing a machine learning model using Amazon SageMaker Studio, integrating multiple AWS services to create a robust and scalable architecture. The project guides you through the entire process, from defining the model to testing it using a web application.

## Architecture Diagram

Below is the architecture diagram that illustrates the various AWS services involved in this project:

![Cloud Architecture](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/Cloud%20Architecture.jpeg?raw=true)

## Services Used

- **Amazon CloudFront**
- **Amazon S3**
- **Amazon API Gateway**
- **AWS Lambda**
- **Amazon SageMaker Endpoint**
- **Amazon SageMaker Notebook**
- **SageMaker Model**
- **Web App**
- **AWS CLI**

## Project Structure

### 1. Define the Model

In this initial step, we define a machine learning model using Amazon SageMaker Notebook. The model is trained and prepared for deployment.

### 2. Deploy the Model in Amazon SageMaker Inference Endpoint

Once the model is defined and trained, it's deployed to an Amazon SageMaker Inference Endpoint. This service allows for real-time predictions and can scale based on demand.

#### **Using AWS CLI for Deployment**

AWS CLI (Command Line Interface) can be used to interact with AWS services from the command line. Below are the steps and commands used to deploy the model using AWS CLI:

1. **List S3 Buckets:**
   - First, verify that the S3 bucket containing your model artifacts exists by listing all buckets:
   ```bash
   aws s3 ls
   
2. 

![Deploy the Model](https://raw.githubusercontent.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/main/projectimages/Deploy%20the%20model%20in%20Amazon%20SageMaker%20Inference%20Endpoint.jpg "Deploying the Model in Amazon SageMaker Inference Endpoint")

### 3. Test the Deployed Model

After deployment, the model is tested to ensure it performs as expected. Testing involves invoking the endpoint and reviewing the predictions to validate accuracy and performance.

### 4. Creating Endpoint Test Functions in AWS Lambda

AWS Lambda functions are created to interact with the deployed model. These functions handle the logic for invoking the SageMaker Endpoint and processing the responses.

### 5. Updating General Configuration and Environment Variables

Configurations and environment variables are updated across the services to ensure seamless integration and communication between AWS resources.

### 6. Creating S3 Buckets

Amazon S3 buckets are created to store various assets, such as model artifacts, input data, and output results. These buckets are also configured for access by other services in the architecture.

### 7. Creating CloudFront Distributions

Amazon CloudFront distributions are set up to serve the content securely and quickly, leveraging the global edge network.

### 8. Creating API Gateway and Reviewing Resources and Stages to Invoke URL

An API Gateway is created to serve as the entry point for the web application to interact with the deployed model via the Lambda functions and SageMaker endpoint.

### 9. Use Sample Web Application Using Distribution Domain Name and API Gateway URL and Generate Output by Giving Prompts

A sample web application is deployed using the CloudFront distribution domain name and API Gateway URL. The application generates output by interacting with the deployed model based on user-provided prompts.

## Conclusion

This project demonstrates the power of integrating various AWS services to deploy, test, and serve a machine learning model. The architecture ensures scalability, security, and efficiency, making it a solid foundation for deploying production-level AI solutions.
