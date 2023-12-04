# AWS LAMBDA

REF LINK : https://techieandtravel.com/aws-lambda-function-to-backup-s3-bucket/

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/af49ccd7-0baf-4162-9405-61c51c992274)

### Supported Languages
- node.js
- Python
- java
- C#
- Ruby

### Why to use Lambda ?
1) Serverless Computing - It eliminates the need to manage the infrastructure, So you can just create a function and let amazon handle the rest.
2) Function as a service - We can develop the functionality without the complexity of building and managing the infrastructure
3) Scalable capacity - It can dynamically scale capacity in response to the increased traffic.
4) Pay per use - Pas as you go, pay only for what you use unlick in ec2 instances which will cost you even if it is idle.
5) Event Driven workflows - For example you can say that when i upload a file -- execute this function
6) Integration with other aws products - We can use api gateway to provide a secure and scalable gateway for web api's that routes http request to lambda functions.
- or we can define amazon s3 events that invoke a lambda function, We can also use lambda function to process the amazon SQS messages or SNS

### Aws Lambda Cost
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/a50c828c-24d9-494b-8260-ed46b1c6512e)

### Aws Lambda Limits
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/1dc92e69-1b21-460c-b8ea-4c8593b8a8b3)
- Maximum Execution Duration < 15 min
- Memory Allocation 128MB - 3008 MB
- We can not allocate CPU to your lambda functions unlike in ec2 instance, But instead the available CPU for your lambda function is directly correlated to to the amount of memory allocated
- The more memory you use the more performant your lamba function will be.
- There is the limit on the number of concurrent lambda functions that is executing in the same region but can contact amazon to increase this number.

### How lambda works ?
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/0feb2c4b-edb3-43b0-9b65-5fbe75422a9a)
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/803a0939-2cc5-4240-8486-7770d1f38859)
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/ea5a7baf-46cc-4a7b-99c0-598c00f1bcd0)
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/8cb76dcc-1c93-4d2c-a384-0510e9841d55)
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/613ba303-b17c-4963-bd86-a803af2ae852)

- First upload your AWS lambda code in any AWS supported language
- Lambda can run your functions when triggered by events form different services
- lambda executes the code when it's triggered
- Lambda runs instances of your function to process the events, Executes it in a container each lambda funtions runs its own container and when a function is create lambda packages it into  a new container and then executes the container
- You will get charged only when the code executed unlikc EC2

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/582b3055-ea68-4ccf-b411-f1dd72bd911b)

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/ded6fa8f-e5ff-4e7b-b383-8246e13ea4a4)

### Lambda Function Structure 

Step 1: Write the lambda function
```
Handler - entry point, accepts JSON-formatted input

def handler_name (event, context)
#### your code
return result;

- Events has details of the event
- Context provides runtime information to handler
```
Step 2: Function Trigger or invoke
```
Trigger
-------
Invocation in response to an event like $3 file upload, DynamoDB table change
Respond to requests to AWS API Gateway or based on AWS cloudwatch trigger
```
```
def lambda_handler (event, context):
  print( event)
  return 'Hello from TechieandTravel'
```
- These lambda functions they need to be packaged and sent to AWS, This is usually a process of compressing the available function and all it's dependencies and uploading it to a bucket
- And then letting AWS know that we want to use this package when a specific event takes place.

### Create Lambda Function
1) From Scratch
2) Use existing Blueprint - Examples of some working lambda functions which can be quickly configured and used
3) AWS serverless application repository -- It is a collection of serverles applications that are published by developers, companies and partners in the serverless community.
4) Container images -- Aws supports container packaging of lambda function as well so you can package your lambda function code and dependencies as a container image rather than updating it as a zip.

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/3342adb0-ff92-455c-9b5c-24045bb97bd6)

Step 1 :
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/940e0583-a224-410c-8f38-ac5706a026fb)

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/42217100-b577-4359-8f25-c63f13796715)

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/a21ab280-aeda-4612-b96f-88b20ded5e11)

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/03441a7e-7447-4605-a9e0-e00a962644c1)

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/adbefef2-bba3-498a-b251-63a1c770cbf7)

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/afd9486e-0ffd-4ef7-8382-737026d47fbc)

- Click on CREATE

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/b14a2ddc-24c4-446f-9839-9ca9f16ce219)


## ==================
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/3342adb0-ff92-455c-9b5c-24045bb97bd6)

Step 1 : Create 2 buckets
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/72b43acf-afe7-4a5a-9871-ea775eccf18d)

Step 2 : Create role and policy
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/f64a063b-db25-44df-8cf1-3d3f202dbac9)
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/04b4f196-808b-4613-aec0-df08a32a9cf3)
- Click on next
- Give role and and descripton -- and create role

Step 3 : Create Lambda function
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/e6998b04-b9ea-4b41-a89a-300b39ff8883)

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/4ef822e7-c583-4966-8fe7-b1e8f70d9406)

- Create Function

![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/638cc511-9d91-434e-964b-76e7b7623db8)

Step 4 : Add a Trigger
- Click on Tigger
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/ff2f033f-c316-4c0c-abd6-19901f125d6d)
- Select Primary bucket here
- Add a Tigger
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/7acb8868-2ae9-4f2f-a8ba-28e38b92147e)

Step 5 : Code 
- Add this code
```
from __future__ import print_function
import boto3
import urllib.parse
import time, urllib
import json
print ("Loading Function..")
s3 = boto3.client('s3')
def lambda_handler(event, context):
    # TODO implement
    source_bucket = event['Records'][0]['s3']['bucket']['name']
    object_key = urllib.parse.unquote_plus(event['Records'][0]['s3']['object']['key'], encoding='utf-8')
    target_bucket = 'mysecondarybucket1'
    copy_source = {'Bucket': source_bucket, 'Key': object_key}
    try:
        response = s3.copy_object(Bucket=target_bucket, Key=object_key, CopySource=copy_source)
        return response['ContentType']
    except Exception as e:
        print(e)
        print('Error getting object {} from bucket {}. Make sure they exist and your bucket is in the same region as this function.'.format(key, bucket))
        raise e
```

Step 6 : Test the code
- Add anything in the primary S3 bucket and Lambda will be triggered
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/4ec9fe23-70fb-4690-b455-fcc2c3e2f47f)
- The above image is primary bucket file is uploaded
![image](https://github.com/pavankumar0077/Complete-DevOps/assets/40380941/ffd2b7a8-4aa7-436d-bd75-f553159f492c)
- In the above image the primary bucket content is backup to secondary bucket.
