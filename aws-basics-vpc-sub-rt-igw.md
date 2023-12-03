# PS : Your company hosts its public-facing website in a local data center. Soham, the chief technology officer (CTO), 
**wants to migrate the website to the Elastic Compute Cloud (EC2) service in AWS.**

**Soham asks you to develop a basic, working proof of
concept (POC) to show how the company could host the
website in AWS.**

### CLOUD - AWS

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/017c93b4-743d-444c-9495-a6c26dba541d)

VPC 
--
- Amazon Virtual Private Cloud (VPC) is a service that lets you launch AWS resources in a
- logically isolated virtual network that you define.
- a vpc spans across the entire region
- It will be having IP RANGES
- Even though a VPC spans across the entire region, every subnet can only be associated with only one AVAILABILITY ZONE.

Subnet
--
- A subnet is a range of IP addresees in your VPC
- You can only specific services in subnets

Route-Table
--
-A route table contains a set of rules, called routes, that are used to determine 
- where network traffic from your VPC is directed.

Internet Gateway
--
- An internet gateway enables your instances to connect to the internet


Stpe 1: VPC
-
- Create VPC -- Name -- Virtual-private-cloud IPv4 CIDR -- 10.0.0.0/16 (only last 2 digits we can change)
- Host address range -- 10.0.0.1 - 10.0.255.254
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/108ebe90-72a3-490a-88fb-b8d9055fbd6b)

Step 2: SUBNET
-
- Create subnet -- 10.0.1.0/24 (only last we can change)
- Host address range -- 10.0.1.1 - 10.0.1.254
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/e76f7758-d9fe-4dee-a186-6be14a86e4cb)

Step 3: Route Table
-
- It will automatically created with VPC
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/21777f98-95b0-49fd-909d-b4ba3f24c939)

Step 4 : Internet Gateway
-
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/933db712-3234-4611-b5e4-ec205b556905)
- To connect to internet
- We need to attach with our VPC
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/78f569ad-69b2-4b7c-ac92-bbbc64a722f1)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/09f7a1df-7407-4256-b2c2-ca0c2f328983)

Step 5 : Route Table
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/95eb31a8-3def-43b5-a551-2abce09adc09)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/3007ef86-2341-41d6-8a6f-ca884efeeda1)

Step 6 : EC2
--
- Connect to instance
- ping google.com




