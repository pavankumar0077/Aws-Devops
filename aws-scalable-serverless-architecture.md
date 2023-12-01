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

NOTE : NOW YOUR API GATEWAY AND LAMBDA CAN PROCESS TENS TO HUNDRED THOUSAND OF REQUESTS PER SECOND.

DATABASE
--
- Each of your Lambda function invocation may open and close relational database connnections at a very high rate, and this may exhaust your database connections.
- Amazon RBS proxy allow application to pool and reuse established with the database.
- It will make the connections more effecient and make your application more scalable.

Relational database connections
--
- Amazon RDS Proxy instance
- maintains a pool of established
- connections to your RDS database


Cache repeated database read queries
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/97ce6524-5984-431a-ba9d-7142d0a6e357)

Cache static and slow-changing dynamic content
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/3fb0c104-7cc5-4370-a425-76bb7da26a16)

Non-time-critical requests
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/598a01b1-ffea-4e8a-9bed-9cd10399a3b1)

Async Messaging
--
- Asynchronous messaging is here to rescue, instead of reallly sending out those emails and notifications right away,
- We can drop them in SQS queues for the worker lambda function to pick up from there and send them in batches in its own time.
- Onece the request is in the SQS queue, we can return to the app user and saying, " your messaga is with us".Rest assured we will send them shortly.
- These solves the API gateway's 29 seconds timeout limit and improve the throughput of your system.

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/78a983ca-d4c6-4632-9a39-9b0d0339805c)

- API gateway got native integration with SQS, So you don't need a Lambda function to enqueue the requests.
- This further reduced the lambda concurrency needed to execute asynchronous requests.

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/2a3d700c-0756-41ce-8c6c-5b6bf7d0b9a6)

Async Friends
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/2d48d232-d920-4056-a03c-d5d6545adc01)

Scale with multiple AWS Accounts
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/e855b669-f161-4a7d-b1f6-549f26a448f1)

- As your application becomes more complex with many  microservices and your engineering teams grow, It may become more complex to manage account level quota
- and control the blast radius of your microservices.

CONCULSION: SO IN THE REAL WORLD, TRY TO DESIGN YOUR MULTI-ACCOUNT STRUCTURE TO FIT YOUR BSINESS NEEDS AND EVOLVE YOUR DESIGN AS YOUR BUSINESS EVOLVES.
WE APPLIED CACHING ON DIFFERENT LAYERS TO IMPROVE THE PERFORMANCE AND THE SCALABILITY OF YOUR APPLICATION.
WE TURNED NON TIME-SENSITIVE REQUESTS TO ASYNCHRONOUS REQUESTS.
WE EXPLORED A MULTI-ACCOUNT STRUCTURE TO ALLOW YOUR MICROSERVICES AND YOUR TEAMS TO OPERATE MORE INDEPENDENTLY AT SCALE.

PALYVOX
==
## BUILD HIGHLY SCALABLE SERVERLESS APPLICATIONS ON AWS
# full workforce engagement management solution

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/5ffa7769-d7fc-48cc-848e-b897e023491e)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/21b52228-70a2-45e9-8166-1679343e4f95)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/97111bb2-0dfd-4e97-883b-e74e0134e546)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/98588ff8-799b-480c-91ec-7796b8860e32)

Cache earlier
--
- Caching at api gateway can save on lambda invocations and save your database.

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/10c33455-8534-4047-83c0-955ff6a102cf)


