![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/6d31c189-2a3b-4d4f-a8ff-ac64d87b1f10)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/69f4846b-434b-4533-b24b-ae8ff428af1e)


![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/6a12537d-08e6-4850-81f5-1b8c70484cc1)

Create a VPC
--
- Region
- AZ's
- Scope is only REGION level
- VPC comes with private IP Range called CIDR
- It comes with default local ROUTER. Route the traffic within VPC.
- ROUTE TABLE takes the control of the traffic
- VPC has lot of address space, we have to cut down the network by creating SUBNET's
- If you want to leverage multiple availability zones then you have should create subnets across multiple AZ
- One subnet can be only at one AZ at any moment of time that means one subnet cannot be in two AZs at the same time.
- One AZ can have multple subnets.
- IGW is requried to connect interet.
- Better to create a dedicated route table for your subnets and then these subnets. And do not follow
this main route table and you add and entry into this saying that if the traffic is gng to 0.0.0.0/0 then target is internet gateway
- DB or Backend's are should be in privaet subnet. In private subnets we don't have route to go to the internet directly, So we will have route table and it will also have same entry like route table.
if we don't create separate route table it will follow the main route table.
- Load balancer was a public facing entity and that's where it will reside into my public subnets and it will be across two subnets for high availability.
- Private subnets and they would only have the private IP address that means these instances cannot really talk to INTENRET DIRECTLY. Only the way they receive a traffic is from Load Balancer.
- DB. Now DB will Master DB will be in one AZ. DB and Standby will be in other AZ

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/17c34693-7448-45b8-ad48-9805da519c28)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fd29f3e1-d0d0-4333-95cb-9e3489c682ea)

- EC2 are in Private Subnets. That means they are not getting INTERNET directly. But sometimes we need INTERNET for patching and installing any softwares.
- SO WE NEED OUTBOUND CONNECTION. That means you can go to the INTERNET. But others not able to form the internet will be accessing you.
- This can be done using NAT (network address translation). NAT are the devices which sits in the public subnet and now they can talk to internet on behalf of these EC2 instances.
- From EC2 traffic will route to the intenet and it will send the pacckets back to EC2 instance.
- And 1st we need to add the ROUTE ENTRY for NAT in the Private Subnet Route Table.
 
Senario 1:
--
- We have On-Perm DB, or Servers and Instances are in EC2 in AWS. And we need direct connectivity but these 2. They we want to do over a private network.
We have 2 options.-
- AWS supports a SITE TO SITE VPN. We have Virtual Private Gateway (VGW) and in the On-Perm we have ROUTER. WITH CUSTOMER GATEWAY. (CGW). Now we can create a IPSec VPC tunnel between these 2
- For High availablility AWS supports 2 tunnels.
- Here traffic still flows through INTERNET.
- To Get a REABILE network in AWS, We can use AWS DIRECT CONNECT.
- AWS can multiple regions as well know. These locations are not really owned by AWS but they are owned by a KOREAN NEUTRAL ENTITIES like in India there are i think 6 to 7  Direct Connect locations.
- These direct correct locations are already connected to AWS corresponding region data center.
- Now we need  connect the ROUTER (ON-PERM) to VPC DIRECT CONNECT. Now we need to connect on-premise network to thsi DIRECT CONNECT location in order to get that bandwidth.

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/5ae2e28a-dbe6-480c-b415-ba5670e14785)
 
Senario 2 :
--
- Other way to connect is like we can use Client VPC to connect their network.
- AWS provides CLIENT VPN ENDPOINT to connect with REMOTE PC or CLIENT, WE need to create SUBNET of our network to the CLIENT POINT ENDPOINT for REMOTE NETWORK.

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/8d178c6f-7ed1-483e-af3e-7ff0c13b7946)


VPC TO VPC Connectivity
--
- Considering a situation where we have multiple VPCs but sitll you want to talk to each other other using a dedicated and a private network between this two.
- AWS Provides VPC PEERING. Other VPC may or may not be same account or different region anything will works.
- This is working fine and good. But if we want to talk to hundreds of VPC then it may be defficult.
- Let's say we need 3 VPC to different and communicate with which other then we need 3 connections like A - B, B-C and A-C and This is called NON-TRANSITIVE ROUTING.
- If it only few VPC's then it is completely fine to go with VPC PEERING. TO Overcome this we got TRANSIT GATEWAY.

TRANSIT GATEWAY
--
- It will simplifies this where all the VPC's which we call typically a SPOKE VPCs connect to a TRANSIT GATEWAY and then TRANSIT GATEWAY can connect to your VPC again in a similar fashion now this acts a HUB.
-  Every VPC can talk to your corporate (on-prem) data center so we can connect on-prem using vpc direct or vpn

VPC ENDPOINT SERVICES
--
- In our senario the web services need to upload and download data from the S3. As we know S3 buckets aer within the region or differnet region but can be accessed over the internet.
- Even our EC2 Machines are in VPC. If you eant to access S3 the traffic actually needs to go through the internet that means it will go to the NAT from NAT it will go to IGW and there it will go to S3. We are depending on the intenet traffic which is not considered as safe if you are not encrypting the taffic.
- We also depend on NAT device bandwidth for example if sometimes NAT goes down then we can't really access the S3.
- AWS did. Example if you have S3 bucket or DYNAMODB in the same AWS region as your VPC. You can rather use something called VPC ENDPOINT SERVICE.
- We can actually reach to S3 or DynamoDB through that VPC endpoint and that means you don't have to really go the internet route and it is automatically this is a device which is manged by AWS and event there is not bandwidth constraint.
- For all this communicate we need to modify the ROUTE TABLES.

VPC EndPoint Gateway & VPC Endpoint Interfaces
--
- Gateway is used to reach S3 or DyanamoDB if you wanna reach any other AWS services, For example you want to access SQS, Cloudwatch ....Your machine would go over internet right to reach to these endpoints. But with **VPC endpoint Interface** you can again reach to this services privately from your but the way it differs from the GATEWAY is that in case of VPC endpint it creates something called ENI ( ELASTIC NETWORK INTERFACE ) into your subnet and then the traffic is routed throught that ENI to this VPC endpoint services and there are around 60 VPC endpoint services. We can reach privately without going over the internet.

VPC Endpoint - PRIVATE LINK
--
- You might have some SAAS Services you might have subscribed to some SAAS services where the end where the software provider provides you access to their software.
- The provider also be running their workloads in AWS ans they want to privately expose their service to your VPC. with in VPC. Of course one of the option is they expose this services through the INTERNET ans you access over the internet but as both VPCs are in AWS you have better options to have network connecitivity.
- Saas provider don't want to expose all the services present he want to provider access  to NETWORK LOAD BALANCER using PRIVATE LINK
- Private Link privately exposes only this network LOAD BALANCER Service to your VPC, So any EC2 want to access this SAAS service can go through the VPC Endpoint interface throught private link to the network load balancer


![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/8f6c366f-caed-425e-addd-a1c04a3d65c6)
