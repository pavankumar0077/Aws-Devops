![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/aed97f5b-502b-4677-8227-74314bc632cb)

-- In Ilograph users interact with a tool either using the web application, desktop client or CLI 


DIAGRAM LINK : https://app.ilograph.com/demo.ilograph.Ilograph/Request

Architecture divided into 3 layers
--
1) Presentation Layer
2) Computer Layer
3) DataBase Layer

-- For the compute layer ilograph uses the combination of API Gateway and Lambda functions to factiliate all CRUD operations
-- For Data storage it uses S3 for the resouce content 
-- Database level it uses Dyanmo DB to store diagram metadata permissions, histroy data and etc
-- Cognito for authentication 
-- Simple email service for emial notifications 
-- Key mangement service for encryption

Let see some of the endpoints
--
1) /diagram : It invokes a single lambda functions that handles different user workflows such as CRUD operations
-- Here we are using SINGLE LAMBDA function for all the operations and services.
   -- We can use multiple as well, We have a debate like lambda will increase the latency of the application in the initial call, But Here we are using nodejs as it is very good prog language no worries
   -- In others for your specific requirement then you have to go with FORGATE

## NOTE : How to nagivate into each and every service is by clicking on the colour circles on the each diagram or click on the below names available 

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/3af78b16-5256-42ef-8d51-5f4bb33f51da)

**Here we are using Dyanamo DB in this application architecture as you can see there are quite a FEY KEY VALUE LOOKUPS 
here wherewe have the ID of the RECORD in hand and we would like to reterieveit quickly this makes Dynamo DB gret choic for this applicaiton architecture**

**If instead we're searching for user's content based on some fuzzy key or if we had many relationships in our data that we would need to query on a relational database like postgress may be a more suitable choice.**

DNS management
--
- The api managment get and update api is api.ilograph.com -- The domain itself is registered not in AWS but in a seprate domain provider called name cheap,
- Ilograph configure their name space and cname Records to point to a record set group in AWS ROUTE 53 service in effect this makes it so that anytime a machine amkes request to the api.ilograph.com endpoint
- it routed to AWS backend from there the router 53 DNS entry is wired to an API gateway endpoint which in turn triggers the hundle diagram flow we were just examining


Authentication Management
--
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/0e01aad4-ca30-4b5a-9585-38244c8d2aab)
- When new user signs up ilograp cognito user pool leverages a post signup trigger in the form of a Lambda function called confirm user, This lambda sends a welcome email to the user add their email to a mailing list and intilizes the permissions
- by wriring to  the permissions table
- After user signs in ilography triggers a generate token lambda  reads off the permission an domains table to determine which resources this user has access to it appends this information to the token so that it can be user later in get and update flows 




