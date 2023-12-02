REF LINK 1 : https://medium.com/@elifnurber/amazon-managed-streaming-for-apache-kafka-5714bec42623

REF LINK 2 : https://medium.com/gargee-bhatnagar/aws-managed-streaming-for-apache-kafka-streaming-messages-from-producer-to-consumer-using-amazon-e6b082e382f6

REF LINK 3 : https://medium.com/softrock-io/migrating-to-aws-managed-streaming-kafka-msk-9b29d0137287

REF LINK 4 : https://medium.com/datamindedbe/simplifying-kafka-cluster-deployment-step-by-step-guide-with-amazon-msk-and-terraform-a3643eaf903a

Amazon MSK
--
Amazon MSK Overview:

Operates Apache Kafka-based applications on AWS.
Facilitates the handling of real-time streaming data.
Kafka Advantages:

Publisher/subscriber model for persistent messaging.
Exceptional fault tolerance.
Processes continuous streams of data.
Open-Source Platform:

Apache Kafka is open-source.
Supports various community-developed tools and extensions.
Amazon MSK Applications:

Construct datalakes using MSK.
Stream data to multiple sources.
Power data analysis applications with native Kafka APIs.
Key Features:

Captures, stores, and analyzes real-time streaming data.
Leverages the robust capabilities of Apache Kafka.
Use Cases:

Building datalakes.
Streaming data to diverse destinations.
Supporting data analysis applications.

## What is Amazon MSK?
Amazon Managed Streaming for Apache Kafka (Amazon MSK) is an AWS streaming data service that manages Apache Kafka infrastructure and operations, 
allowing developers and DevOps managers to operate Apache Kafka apps and Kafka Connect connectors on AWS without having to become Apache Kafka specialists.
Amazon MSK manages, grows, and maintains Apache Kafka clusters, as well as providing enterprise-grade security features out of the box and 
AWS interfaces that help developers build streaming data applications faster.

## Amazon MSK Features
Server Management:

Amazon MSK eliminates the need to manage Kafka clusters and ZooKeeper nodes manually.
All management is done through the Amazon MSK console.
High Availability:

Automatic component replacement in case of failure.
Software patches are deployed automatically, ensuring continuous operation.
Security Features:

Full control over network setup and IP addresses.
Clusters are accessible based on user-defined VPCs, subnets, and security groups.
Deep Integration:

Integrated with various AWS services and tools.
Includes AWS IAM, Amazon Kinesis, Apache Flink, and more.
Open Source Compatibility:

Utilizes native Apache Kafka versions.
Seamless compatibility with Kafka applications and tools without code modifications.
Cost-Effective:

Starts at less than $2.50 per day.
Customers typically pay between $0.05 and $0.07 per GB consumed, offering cost savings compared to other managed providers.

## Patterns of Ideal Utilization
• Capture large amounts of log files from applications.
• Analyze the clickstreams on a website.
• Database event streams are processed.
• Keep track of your financial transactions.
• A collection of social media feeds.
• Collect IT log files.
• Deliver data to a data lake on a regular basis.
