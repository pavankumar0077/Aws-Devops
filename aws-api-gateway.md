![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/ca9967fe-9c7b-4e20-90de-da723973fe4c)

- Lambda to handle api requests
- Dynamodb to perform opertaions CRUD
- Swagger -- api documentation

**Code ref link : https://github.com/listentolearn/aws-api-gateway-rest-api/tree/main**
Other ref link : https://medium.com/everything-cloud/building-a-serverless-api-with-aws-api-gateway-and-lambda-functions-bb6d6595d3df

Step 1: Dyanano DB
--
1) Create dyanamo db table
2) Dyanamo db --> table -- name -- books, partiation key -- isbn
3) Rest all the settings same
4) Create table

Step 2: IAM role for the lambda function
--
1) IAM -- Roles -- New role
2) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f3e328e3-71cd-42de-88df-690cfc884441)
3) Next
4) Create policy -- lambda,  dyanamo, aws full, cloud watch (only for demo)

Step 3: Create Lambda function
--
1) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/14dda205-ce7c-4e04-88e2-3843f9858193)
2) Upload the code from github : https://github.com/listentolearn/aws-api-gateway-rest-api/tree/main
3) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/36baf48e-59d8-4dfa-9665-6f1d8b697136)
4) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/446776d5-da61-428a-a469-bd290a1a0d5c)

Step 4: Create API GATEWAY
--
1) Create API --> Create Rest api --> Import Swagger dock
2) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/5ba47250-4cdd-4934-861a-96436f81bba2)
3) After creating we will get the apis --> click on lambda integreation requried
4) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/c8d10c86-5516-499f-9487-95eb287620e0)
5) for each and every method there should be integration 
6) edit method request and add request validator -- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fdad7956-74a2-41bf-8b1a-cd59f60186a3)
7) Left side -- Go to resources and -- Click on DEPLOY API
8) It will ask to create new stage -- like dev or stage or test -- we will get URL
9) ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fac059d6-3bda-44dc-8c55-9f7f899c272b)
10) We can set route53 as well for custom domain
11) Cache capacity 
12) Canary -- option for percentage testing

Step 5: Test the application
--
1) We can test the application in 2 ways 1. Is using ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1dcb911b-0423-4b39-bc08-4af6d6ba0dc9)
2) Post man

```
https://nf134cq0e2.execute-api.us-east-1.amazonaws.com/dev/books

{
    "data": [
        {
            "bookName": "Pavan-Testing-Book",
            "isbn": "1",
            "authorName": "IDRBT",
            "rating": 5
        }
    ],
    "count": 1
}

https://nf134cq0e2.execute-api.us-east-1.amazonaws.com/dev/books

{
    "isbn": "1",
    "bookName": "Pavan-Testing-Book",
    "authorName": "IDRBT",
    "rating": 5
}

https://nf134cq0e2.execute-api.us-east-1.amazonaws.com/dev/books/1

{
    "bookName": "Pavan-Testing-Book",
    "authorName": "IDRBT",
    "rating": 10
}

https://nf134cq0e2.execute-api.us-east-1.amazonaws.com/dev/books/1

-- No content --

```




