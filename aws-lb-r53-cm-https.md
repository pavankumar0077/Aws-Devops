# AWS Load Balancer HTTPS Setup with Route 53 and Certificate Manager & HTTP Redirect to HTTPS

## Load Balancer Flow
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/178c42c6-1443-4288-9c97-8929a5728097)

## Load Balancer Custom Domain Flow (HTTP)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/17b8cdec-d3bb-415b-86e5-6ae59722ce7b)

## Load Balancer Custom Domain SSL Flow (HTTPS)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/c5822f03-faec-44f8-af3d-a75bbafb37cf)


### Load Balancer Flow
Step 1 :
--
- Create a EC2 instance and run you application

Step 2:
--
- Create Application Load Balancer
- And point to you application EC2 instance
- Create ALB
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/29f08226-7d24-4614-a3ee-0f06d51201ef)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1579bff2-ea9a-4c84-8d18-1b7cade54560)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/645e4576-161f-4153-8224-0f15a453c5a7)
- Here create target group
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/6dc02b94-9919-449c-994d-91cb356e539e)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/5db7a203-14a4-41f5-9e4b-225b6b40b83d)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/b4c1604f-a583-480c-a4df-6fcd383235a8)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/a7317943-9776-4338-93fc-6fcd9919ac32)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/459d3f61-fc6b-452b-b472-bd869408ff59)
- After creating target group -- click on create load balancer
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/5cd7af4f-0676-408b-882e-7d739e8326a3)
- After LB if the application is not working, Then check where is instance is like which AZ Zone and then re-configure the Load balancer
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/0583b8ca-9332-4886-aca2-e3a095ae0767)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/31147cc3-8cbe-4c73-b6e0-f62f10704895)

### Load Balancer Custom Domain Flow (HTTP)
- Go to Route 53
- Registered domains
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/901b8bb7-c36f-4874-921f-4dde56884df7)
- Go to Hosted Zones
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/cdadbbfc-78dc-4c49-bf82-ad868dea13be)
- NOTE : Hosted Zones and Registered Domains -- Records should be MATCHED
- NOTE : If doesn't match then Route 53 will not work.
- If doesn't match then -- GO TO REGISTERED DOMAIN -- Under Name Servers --> Add or edit name servers and Copy the Name-server of Hosted zones and paste in the registered domain and match it.

## CREATE RECORD
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/07a8f66c-e1d6-4042-9e0c-e1af056845f7)
- Click simple routing --> Define simple routing
- - record type -- A
  - Route traffic to -- Application and Classic Load Balancer
  - Choose Region -- us-east-1c
  - Choose Load Balancer -- That you have created of the application.
  - Click on Define simple record and Create records
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/86c1bce2-3a6c-4da1-b601-c8b07e72e0bb)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/3ea1988d-7ae1-4027-a0ed-7afc7bf0e42e)

## Check Domain is Registered or Not
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/d8f4d7ad-3c87-45b8-a707-accb5a24bd45)

### Load Balancer Custom Domain SSL Flow (HTTPS)
- Search for Certificate Manager
- Request Certificate
- Request a public certificate
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f4ba063b-07a0-4606-94b0-5aea5f9f68d6)
- Click on Request
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/cc672620-5061-477e-a69e-4eec60f461a1)
- Since we choosen DNS Validation -- Click on the recently creating certificate
- Click on create records in Route 53
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fec89555-d144-43b1-b815-8fb4d28ef709)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/4c8c7cec-7a4a-4769-bb6c-2ef3cf61128d)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/285903c4-12bb-4720-9436-2bd3419e0b6d)
- Here we can see a CNAME record for the validation
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/7f7e2c90-c32e-4fef-bcbe-3f6f9bb29f98)
- NOTE : This CNAME record is only for validation it doesn't do anything on the traffic flow alternatively you can also do email validation.

## Now in the Load Balancer perviosuly we added only HTTP now we have TO ADD HTTPS.
- Head over to load balancer and click on LISTNERS
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/5d5eb4b0-a597-4522-a504-79cc9875ba23)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f946e1fb-4a53-423e-ae8d-c9c3023c2309)
- Click on add listeners

### Test the application with HTTPS now
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/d5aba5b1-299e-4d4c-a7ab-70490555c422)
- As we can see lock symbol that means it is HTTPS secured network.

### Now we don't required HTTP in the LOAD BALANCER
- Go to Load Balancer and click on HTTP listener and edit it
- Delete the lister or rule
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/0ea34946-2e35-46be-8673-dcc27e86c464)
- Click on Add action and -- Redirect to HTTPS -- 443
- Even if the User hits with http then it will redirects to HTTPS
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/42572427-715e-46f1-a4d6-e7012b4d423b)
- Click on update.
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/7c0a3f7d-e920-4057-956a-ac78f8262849)

### Add WWW
**As of now if we hit with testipaddress.com it will works, but if we use www.testipaddrss.com it will not work**
- We only created record for testipaddress.com
- NOW WE HAVE TO CREATE ANOTHER A TYPE RECORD WITH WWW
- GO TO HOSTED ZONES and our registered domain.
- Click create record -- simple routing -- Define simple record
- record name -- www
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/b09a71d5-435c-4097-8dfa-37a4766d287d)
- Click on Define simple record. and Create records.
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/07abe9b2-1592-4035-aefc-47be8bb727bf)
- What if you want to crate albtestipaddress.com so similarly
- same process
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/145c4545-b878-4580-b7f7-d27de9551f78)
- create records.
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1729fd59-606c-4185-9161-c3770d4af9ca)
- It will also work.
