SNS
--
- Amazon SNS (Simple Notification Service) is a highly available, durable,
secure, fully managed pub/sub messaging service
- We can send specific message to sub1,2,3 as well using KMS KEYS
- Same message can be consumed by any no. of consumer
- **SNS by default after number of retries the messages can get discarded** 

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/92dc8b13-c173-4c1d-844e-0fa142e0502a)

Advantages of SNS
--
• Automatically scale
• Keep messages secure using AWS KMS Keys
• Messages can go to different subscribers based on fields in message
(Message Filtering)
• Fan Out Architecture - Same message can be consumed by multiple
consumers

SQS
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/b3b25885-58b6-452a-92d5-a7f0bc3b84d0)

- Amazon SQS (Simple Queue Service) is a fully managed message queuing service
- System A -- Puts a message in the QUEUE ( Amazon SQS ) --> We can trigger a lambda for this SQS and process the messages
- **SQS is reliable even after certain number of delivery failure it can go to a dead letter Queue and you can retrieve messages from there**.

Types of Queues 
--
1) Standard Queue
2) FIFO Queue

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/a005845b-f465-45bf-8ca4-525d075caf9b)

Advantages of SQS
--
• Reliable, Dead Letter Queues can be enabled
• Scales automatically
• Keep messages secure using KMS
• Convert synchronous patterns to asynchronous.
• One message can't have multiple consumers. Once message is processed by consumer, it gets deleted from SQS

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/6aabb37c-a2bc-4829-83a2-20b454027ea0)

1) Here system a puting the messages in SQS queue and you configured lambda with that SQS
2) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/8484ec42-e593-4a1d-b963-81a748944823)
3) Lambda has 2 components 1 is AWS Lambda Service -- This is not your lambda code this is acutally AWS lambda service, Then you have your lambda function
4) this lambda service keeps pulling the queue to look for any messages when this lambda service pulling find messages the lambda service invokes your lambda functions
5) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1311807f-7541-45ae-b0b4-2301dbea15fc)
6) Funtions reads in batches. So we have our sqs queue it has bunch of messages and on the right we have lambda components and 1 lambda service and lambda function
7) AWS lambda service -- polling for messages and here batch is a collection of messages and each batch can have up to 10 messages and the total  size cannot exceed 256 KiloBytes
8) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/9022a268-7086-459d-b57f-29ccd1451ddd)
9) 5 BATCHES and each batch is 6, There is polling limit so depending on what have you said the on concurrency limit for your a lambda funcion the lambda service will invoke
10) tha many lambdas approperiately polling limit is greater than equal to 5 and less than equal to lambda concurrency limit so in this case
11) let's say we have set concurrency limit of lambda to five corresponing to the five batches so what's going to happen is lambda service is invoke 5 copies of your lambda functions
12) And each copy is gonna get one batch  of 6 messages and while these five copies after your lambda is processing this messages the messages in the SQS is invisible to others for a certain period of time it is called visibility timeout  

Sunny Day Scenaio
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/a1dcc797-c625-4de4-8ca3-ef95a7a88456)
1) 5 Copies of your lambda got invoked all the messages got processed fine, Your lamba services okay everthing is fine
2) So it's gonna go and delete all the messsages from SQS, no problem at all but
3) What if lets say the copy of your lambda function the first copy of your lambda function failed to process all of the messages in one batch
4) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f6997f55-af06-4e7c-923d-78d18c6d2108)
5) and more intertingly this copy of lambda function could process for 4 message and failed to process reaminig two in the same batch
6) If all the messages in the batch are failed then aws lambda service will revert it back and another copy of lambda invoke will pick it up
7) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/03caded0-b33c-4177-aa64-1f492276854a)
8) Let say only 4 messages are send and 2 failed at this time, rollback entrie batch if 1 or more messaages failed, some messages get reprocesssed
9) To avoid the above 6th point, We can delete the sucessfully send message are deleted by using our Lambda function code (Boto 3 SDK)
10) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/e6c027a9-6eaf-4063-accf-d88bc4b8c50e)
11) Only un-successful message can be reverted back 

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/52b2f9b1-6c7f-4982-abf8-81aee42af95f)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fe001e9c-e841-4af0-91e1-24d73733c578)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/609e2d50-8ed9-4869-9dd0-3081e10708b7)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f30ea016-3f10-4c51-aa42-bdfae52cdd96)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/91c0d95d-4c95-4060-be2d-7891b4dc386c)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/b135dbc8-8b40-4eb9-bcb9-e7981c3e865e)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/97b056b0-d187-4878-ac28-3d834596523a)












