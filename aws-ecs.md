# ECS

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/837806bf-f112-41f4-ba04-8cfcba98cf3c)

REF LINK : https://github.com/Tech-With-Helen/containers-aws-ecs

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/0dbc8712-a09b-4303-8317-25d2b3366062)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/b553d785-0768-44a4-b1bf-9fb32a755822)

Create and deploy the application in ECS with custom domain using Route 53
--
Step 1:
--
- EC2 instace -- Application local check --> Docker --> Docker build and image

ECR
--
- Create ECR repository to store the docker image
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/14b1420b-ec27-4cca-a709-e785701cb941)
- Create repo ( Bydefault AWS create or prefers private repo only )
- Select the repo and click on push commands
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/086380b1-e6fb-4556-b1e1-d008449e36a2)
- We don't do step 2 here be'coz we already have the docker image
- We will push created docker image to ECR
- WE NEED TO HAVE AWS CLI BEFORE DOING THIS.
```
[root@ip-172-31-33-4 ec2-user]# aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 794982227033.dkr.ecr.us-east-1.amazonaws.com
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
[root@ip-172-31-33-4 ec2-user]# docker images;
REPOSITORY      TAG       IMAGE ID       CREATED          SIZE
project-image   latest    6f77fe1745cb   33 minutes ago   68.7MB
[root@ip-172-31-33-4 ec2-user]# docker tag project-image:latest 794982227033.dkr.ecr.us-east-1.amazonaws.com/myecr-repo:latest[root@ip-172-31-33-4 ec2-user]# sudo docker images;
REPOSITORY                                                TAG       IMAGE ID       CREATED          SIZE
794982227033.dkr.ecr.us-east-1.amazonaws.com/myecr-repo   latest    6f77fe1745cb   34 minutes ago   68.7MB
project-image                                             latest    6f77fe1745cb   34 minutes ago   68.7MB
[root@ip-172-31-33-4 ec2-user]# docker push 794982227033.dkr.ecr.us-east-1.amazonaws.com/myecr-repo:latest
The push refers to repository [794982227033.dkr.ecr.us-east-1.amazonaws.com/myecr-repo]
3a4d3307ab21: Pushed
5f70bf18a086: Pushed
3d6cccfefbd5: Pushed
86967bf6ee1c: Pushed
6631526847a0: Pushed
0ccb8a57c4a5: Pushed
ec4d864ac810: Pushed
5af4f8f59b76: Pushed
latest: digest: sha256:ff57d5dbec354051a4829e325a07147f28e13cb80029e4ca91b7911269f39df4 size: 1994
```
- Create it is push or not

ECS
--
## Create cluster
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/95ccd30b-f93b-4363-9884-28f1c3b96a31)

## Create Task Definitions
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/6fb598cd-ad14-4b97-8083-ebe6e05f3375)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/8e9e23bc-dc07-4df9-b75b-482a117bfaf9)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/27055fda-b113-4820-b042-584b988b6b56)
- Click on Create

## Create Service
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fc67113a-12f6-43b7-bb81-aca5289f9752)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/2b811a96-e681-4b12-8d8a-5ec0de535811)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/9a1eeabd-9b63-45e2-b77f-46fd6d1a9b29)
- Click on create.

## Test the application
- EC2 - INSTANCE - PUBLIC IP
- Edit inboud rules as per requirement
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/6a384968-275e-4c77-a0ca-c25ac8c06834)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1410d16a-d97e-4986-8573-95b70cb5725b)


# THIS IS NOT PART OF THIS APPLICATION TAKS =======
Route 53
--
## Domain Register
- Click on Route 53
- Click on Register Domain
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/6dc94015-a434-48a8-b98a-a8884e3df744)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fb7ca752-698a-4a4b-a2c1-a5f22d52e420)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/cf005e73-6fa2-4469-9ada-42cdea04cdbb)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/ef0db37f-9174-4a91-813f-fb89606b07ee)
- Some times we don't need to have Hosted Zone at this moment, So we can create it in later point as well.

```
 In Amazon Web Services (AWS), a hosted zone is a group of managed DNS records that are associated with a domain name. It is a type of container that allows you to store and manage multiple domain name records, such as A, MX, CNAME, and NS, in a single place. Using a hosted zone in AWS lets you easily manage DNS changes for your domain, and also gives you the flexibility to add, update, or delete records as needed.
```
- Submit (After T & C )

## Create Hosted Zone
- Click on Hosted Zones
- Create Hosted Zone
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/446e249f-d5e1-436e-a254-5c92a8470df5)
- Enter the domain that you have registered (newly created)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/46668ff6-f4be-4e59-ba17-0e72c6e9ead3)
- Here NS - Name Server
- SOA - Start of Authority

## Create RECORD
- Click on create RECORD
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/09363b70-4afe-4899-8f0d-74db340c87b4)
- Here RECORD TYPE - A .. Means which we are pointing to EC2 instance and Give the Ip address of EC2 instance
- Or click on Alias and choose the endpoint (Like S3 static website endpoint.)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/05c72af3-b8b1-416e-9288-8c69b7052857)
- Click on Create records.

## Sub Domain of our Domain
- blog -- binarytobox.com (custom domain name) to well route to traffic to particular service.
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/89809edd-29ab-4c57-ab7d-6ae2c776e4e3)
# THIS IS NOT PART OF THIS APPLICATION TAKS ======

## Adding record 

Adding to records with custom domain
--
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/299394f2-a286-4f5e-be89-6ad6b09f4f36)
- Click on Reccord
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f352bbc3-0c20-4d21-a85d-fa4e44750beb)
- Click on next
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/567c59d5-7ec7-495d-a523-2c4da2bbe6f2)
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1a54f267-3ac6-4d3c-9897-4b91e49513ae)
- Select the record name -- click on create records

Testing with register domain
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/897d195b-4a9c-4f47-a6fa-4e4ab9f82f4c)






