# VPC COMPONENTS

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/23b5878a-c309-498c-85df-fdb81b7966cb)

Subnet Mask
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/ff0fe271-d6a1-41ef-b897-85031b4a4e0c)

- /32 == Only 1 IP == 32-32 = 2 power 0 = 0
- /31 == 32-31 = 2 power 1 == 2

- /32 - no octet can change
- /24 - last octet can change
- /16 - last 2 octets can change
- /8 - last 3 octets can change
- /0 - all octets can change == Whole internet

Public vs Private IP (IPv4)
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/b7696ef3-3709-42ee-83fa-d363bcdb3dd9)

REF LINK : https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/9e4705a0-6e45-4874-8f1f-ac68d59c86b2)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/0f91b567-236b-4352-aee5-9c2be1cb8ba5)

- Min ip address -- 2 power 4 == 16 ip's
- Max ip address -- 2 power 16 == 65536
- While we are creating vpc we have to reminder this

VPC - Subnet (Ipv4)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/eba37904-5a75-4904-92ac-764842029762)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/746642a3-05f9-47f3-8ca6-77a14f867ce8)

CIDR RANGE : https://www.ipaddressguide.com/cidr

IGW
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/992dd7ff-7ae0-4f95-b1ca-f21ee9bff87b)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1d6a2a72-ac00-4647-a410-13e513630265)

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/11d9fc33-459f-441a-8b89-4aa64a0122c2)


Public Subnet 
--
- If you create something in the public subnet
- If you assign public ip address the device will get public ip address
- And it should be enabled in public subnet be'coz public subnet is public facing devices it will contains all the web-servers
- WE DON'T DO THIS IN PRIVATE SUBNET, Be'coz PRIVATE SUBNET DO NOT NEED TO HAVE ANY PUBLIC IP ADDRESS.








