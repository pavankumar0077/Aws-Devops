Best practices/techniques
--

- Optimise sync requests
- Caching
- Leverage async patterns
- Multi-account
- The playvox journey

A typical 3 teir web applicsation
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/341b0e58-bc9a-4181-a2ef-9c675a974efe)

A typical serverless web app
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/d81c9429-7300-4421-8d29-2f412749c863)

What a large scale may look like
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/2508b9b1-007f-4b78-8c03-7d49f4b02094)

Know your applicaiton
--
- Observability
- Load testing

Synchronous Requests
--
- Synchronous requests are for the business transactions that your application users expect the instant responses.
- In our initial architecture synchronous request are build on top of amazon api gateway, aws lambda, amazon aurora, dynamodb, 

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/102d5b8e-34cd-4cc7-b264-08ae697ea58e)

Amazon API GATEWAY
--
● Highly available
● Burst from 0 - 100s of thousands of Requests per seconds
● Default quota 10,000 RPS
- can be raised
● Request validation to fail fast

AWS Lambda
--
- Lambda is a serverless compute engine with built-in security, scalability and high availability out of the box
- To handle a large number of synchronous requests

How Lambda Concurrency works
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/88de09b9-4bf7-4850-811f-0b398bc92307)

- Each lambda invocation runs in a dedicated micro VM. and it is called as Lambda;s Execution Environment.
- A single execution environment can process one request at a time, and this is to ensure your lambda function invocation runs in a secure and isoloated env

```
AWS Lambda concurrency quota
Concurrency # RPS
Required concurrency
= (average requests per second) x
(average request duration in seconds)
Required concurrency
= (10,000 requests/second) x
(0.1 second/request) = 1,000
```
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/654c5397-0e64-4853-81b7-c61ebed30434)

- Beforing the application is moving to PROD we have test **Load testing**
- And **Monitoring and alerting**, When quota is reached we have to monitoring for this.
- Run frequent load testing and reviews to make sure your account concurrency quota fit your scaling needs.  

Optimize your lambda functions
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/9f7cf44b-b759-4cc5-9c51-63fb0bd1642c)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/2fded46b-73db-4f25-9424-65535ace1e75)

- The core principle here is to make LAMBDA FUNCTION package small so the lambda execution env can start quickly, process request quickly, and get reused quickly.
- This will improve request response time and also requests per second to your lambda function can handle
- Optimize lambda resource setting, AWS POWER TUNNING is an open source tool that can help you to optimise your lambda's resource setting for performance and cost.
- You can run power tuning to your aws account, and tool will collect all the execution and present you a graph that can help you to find the best configuration for you lambda functions.



