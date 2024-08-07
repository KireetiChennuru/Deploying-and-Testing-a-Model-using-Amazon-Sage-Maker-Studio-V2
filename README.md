# Deploying and Testing a Model using Amazon SageMaker Studio V2

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

#### **Using AWS CLI and SageMaker Notebook for deployment**
AWS CLI (Command Line Interface) can be used to interact with AWS services from the command line. Below are the steps and commands used to deploy the model using AWS CLI:

![Using AWS CLI for deployment](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/AWS%20CLI.jpg?raw=true)

1. **List S3 Buckets:**
   - First, verify that the S3 bucket containing your model artifacts exists by listing all buckets:
   ```bash
   aws s3 ls
2. **Upload Model Artifacts to S3:**
   - If your model artifacts are stored locally, upload them to your S3 bucket:
   ```bash
   aws s3 cp /path/to/your/model.tar.gz s3://your-bucket-name/

3. **Sync Local Directory to S3 Bucket:**
   - Use aws s3 sync to synchronize files from your local directory to the S3 bucket:
   ```bash
   aws s3 sync local-directory/ s3://your-bucket-name/
   
4. **Create a SageMaker Model:**
   - Create a model in SageMaker by specifying the S3 path to your model artifacts:
    ```bash  
   aws sagemaker create-model \
    
   --model-name my-model \
     
   --primary-container Image=your-docker-image-url,ModelDataUrl=s3://your-bucket-name/model.tar.gz \
     
   --execution-role-arn arn:aws:iam::your-account-id:role/your-sagemaker-role

6. **Create an Endpoint Configuration:**
   - Set up an endpoint configuration that will be used to deploy the model:
   ```bash  
   aws sagemaker create-model \
    
   --aws sagemaker create-endpoint-config \
     
   --endpoint-config-name my-endpoint-config \
     
   --production-variants VariantName=AllTraffic,ModelName=my-model,InitialInstanceCount=1,InstanceType=ml.m4.xlarge


6. **Deploy the Model:**
   - Finally, deploy the model by creating an endpoint:
     
   ```bash  
   aws sagemaker create-model \
    
   --aws sagemaker create-endpoint \
     
   --endpoint-name my-endpoint \
     
   --endpoint-config-name my-endpoint-config


7. **Check the Status of the Endpoint:**
   - Check the status of the endpoint deployment:
     
   ```bash  
   aws sagemaker describe-endpoint --endpoint-name my-endpoint


### 2. Deploy the Model in Amazon SageMaker Inference Endpoint

Once the model is defined and trained, it's deployed to an Amazon SageMaker Inference Endpoint. This service allows for real-time predictions and can scale based on demand.

![Deploy the Model](https://raw.githubusercontent.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/main/projectimages/Deploy%20the%20model%20in%20Amazon%20SageMaker%20Inference%20Endpoint.jpg "Deploying the Model in Amazon SageMaker Inference Endpoint")

### 3. Test the Deployed Model

After deployment, the model is tested to ensure it performs as expected. Testing involves invoking the endpoint and reviewing the predictions to validate accuracy and performance.

![Test the Deployed Model](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/Test%20Code%20Generation%20and%20Sentence%20Completion.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")
<br>
![Test Sentiment Analysis](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/Test%20Sentiment%20Analysis.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")

### 4. Creating Endpoint Test Functions in AWS Lambda

AWS Lambda functions are created to interact with the deployed model. These functions handle the logic for invoking the SageMaker Endpoint and processing the responses.

![Creating Endpoint Test Functions in AWS Lambda](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/Lambda%20-%20End_Point_TestFunction.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")

### 5. Updating General Configuration and Environment Variables

Configurations and environment variables are updated across the services to ensure seamless integration and communication between AWS resources.

![Updating General Configuration and Environment Variables](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/Updated%20Configuration%20and%20Environment%20variables.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")

### 6. Creating S3 Buckets

Amazon S3 buckets are created to store various assets, such as model artifacts, input data, and output results. These buckets are also configured for access by other services in the architecture.

![Creating S3 Buckets](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/S3-Bucket.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")


### 7. Creating API Gateway and Reviewing Resources and Stages to Invoke URL

An API Gateway is created to serve as the entry point for the web application to interact with the deployed model via the Lambda functions and SageMaker endpoint.

![Creating API Gateway and Reviewing Resources and Stages to Invoke URL](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/API%20Gateway%20-%20POST%20-%20Method%20Execution.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")
<br>

### 8. Use Sample Web Application Using Distribution Domain Name and API Gateway URL and Generate Output by Giving Prompts

A sample web application is deployed using the CloudFront distribution domain name and API Gateway URL. The application generates output by interacting with the deployed model based on user-provided prompts.

![Use Sample Web Application Using Distribution Domain Name and API Gateway URL and Generate Output by Giving Prompts](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/AI%20Generated%20Output.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")
<br>
![Use Sample Web Application Using Distribution Domain Name and API Gateway URL and Generate Output by Giving Prompts](https://github.com/KireetiChennuru/Deploying-and-Testing-a-Model-using-Amazon-Sage-Maker-Studio-/blob/main/projectimages/AI%20model%20output%20using%202nd%20Sagemaker%20Endpoint%20.jpg?raw=true "Deploying the Model in Amazon SageMaker Inference Endpoint")


## Conclusion

This project demonstrates the power of integrating various AWS services to deploy, test, and serve a machine learning model. The architecture ensures scalability, security, and efficiency, making it a solid foundation for deploying production-level AI solutions.


## Author

- Kireeti Chennuru | www.linkedin.com/in/kireeti-chennuru
