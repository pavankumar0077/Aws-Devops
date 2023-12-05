DESIGN 1 : Instances should get INTERNET
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/b0ff9ab8-ab08-46a0-b17c-2a37c3d9727e)
- Here both the ec2 instances are connected to IGW and both will get INTERNET
- Be'czo they are in same network they can communicate with each other.

DESGIN 2 : Only one instance should get the internet, The other instance is DB so we don't want to expose to internet for security reasons.
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/e8d1220e-c7ba-4019-a959-6931f583c2d3)
- Creating local route tables for each instance
- We are not using main route table

Step 1 : 
Cretae VPC -- Name -- virtual-private-cloud IPv4 CIDR
host address range -- 10.0.0.1 - 10.0.255.254

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/fd272432-43d8-4704-9310-af30096d3ca9)

Step 2:
create 2 subnets (Public & Private)
public-Subnet-A--10.0.0.0/24
host address range -- 10.0.0.1 - 10.0.0.254

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/0d97d280-45a1-4551-856b-214fac1a3551)

private-subnet-B--10.0.1.0/24
Host address range -- 10.0.1.1 - 10.0.1.254

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f6e11cbf-e88d-404f-96aa-36e7e8a36e7b)

Step 3 :
- Check the default route table -- you will see the above 2 subnets have not been explicitly associated with any route tables and are therefore associated with the main route table.
- ![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/02e8c1eb-c962-4fe7-8f05-9e5d358a76e0)
- Here it is connected subnets are connected to main route table
- But we need to create separate route table for the ec2 instances.

Step 4 :
- Create a IGW and Connet with VPC.

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/34ef5bfa-6cc2-414f-8949-e61bbd1c16ff)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/cfcfff3e-f64f-4054-9701-3e75fc7b1df5)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/19f35dba-0888-422e-a2a5-a1555c7ee739)

Step 5 :
- Create 2 route tables -- one with public IGW, one private (only local)
- Public-route--add IGW in route table and associate with public subnet
- private-route -- associate the private subnet

Step 6 :
- Create one EC2 instance in Public Subnet (autoassign public ip enable)
- Create one EC2 instance in Private subnet ( ssh and ICMP from public subnet )


NOTE : ICMP -- Internet Control Message Protocal -- used to perfrom network diagonstics

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/e99bf20e-5cc9-4a68-addb-cb09c8f74860)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/bcca9d86-949f-4ee5-b079-294d42c9a4d3)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/04c4f872-915e-4f8a-8f79-411ea7f55aca)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/3d699d90-5877-4e32-9ce9-f636c7a9e26d)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/c43754cc-c5e2-406b-b43e-1449643bc7c9)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1631dfa8-f7b6-4d77-936b-2095484e2655)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/47be19a4-4e47-4df9-8b8d-33c16c7d723e)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/725a27da-edde-4f9a-9673-376db38b3a88)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/7636e8a4-79f1-4be1-a2b3-2dfb709506fd)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/f4fd750e-054b-4472-b069-b66815eb68bc)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/4d572c3e-7937-44cc-8521-cc93541ebc3d)


