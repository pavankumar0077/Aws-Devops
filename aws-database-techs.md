


Database Scaling – Horizontal vs. Vertical
--
- Designing data-intensive applications presents challenges in scaling databases and meeting SLAs under high loads.
- Database calls are costly, and minimizing trips is crucial for optimal performance. Cloud architecture's strength lies in dynamic scaling,
- adjusting resources based on workloads, optimizing resource usage, and controlling expenditures efficiently.

![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/53b30ee4-2ab6-43d7-bc0a-a7b893f0a659)

Vertical Scaling
--
- Vertical scaling adds resources (CPU, memory, storage) for immediate database performance improvement.
- In a cloud environment, adjusting the database instance size is straightforward, requiring minimal code changes.
- Performance tests are essential to determine the optimal instance size aligned with SLAs.
- Overprovisioning is a risk with vertical scaling, impacting costs.
- Major cloud providers like Azure and AWS simplify scaling, enabling quick adjustments without waiting for new hardware.
- Users can scale up for performance issues and down when resources are not needed, managing costs dynamically.

Horizontal Scaling
--
- Horizontal scaling is used to handle increased user requests or workloads beyond the capabilities of a single database instance.
- Ways to implement horizontal scaling include adding read replicas, utilizing caching, and sharding the database into multiple servers.
- In a cloud environment, you can dynamically scale database instances based on load, avoiding being stuck with unnecessary resources during low traffic.
- Auto-scaling costs are proportional to traffic and workload, allowing flexibility in adjusting resources based on demand.
- Rightsizing the database instance involves running performance load tests to find optimal read-write performance metrics aligned with business requirements and SLAs.
- Horizontal scaling is particularly beneficial for handling spiky workloads, providing a preferred approach compared to vertical scaling for such scenarios.

Database Read Replicas
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/dd5b9586-8856-4800-8633-978ea7086d49)

- A read replica is a read-only copy of the database, providing scalability by offloading read operations from the primary instance.
- It enhances performance by routing database queries to read replicas, especially beneficial for read-heavy workloads.
- Updates to the primary database instance are automatically replicated to associated read replicas, ensuring consistency.
- In case of read replica failure, user traffic is redirected to other available replicas; if the primary instance fails, a read replica can be promoted to handle both read and write traffic.
- Multi-AZ deployments offer high availability by synchronously replicating updates to another instance in a different availability zone.
- Combining read replicas with Multi-AZ deployments provides increased database availability, allowing for read scaling.
- Read replicas have the same price as the standard primary DB instance; autoscaling policies help manage costs by adjusting resources based on load.
- Read replicas enhance read throughput, but write speed improvement is limited, as writes are directed only to the primary master DB instance.

Database Caching 
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/ab4c6d78-2028-400c-858a-406be1ad830f)

- Improving database performance is crucial for distributed systems, requiring fast performance to meet SLA requirements.
- Effective caching strategies enhance application performance and reliability by reducing database overhead and optimizing costs.
- Frequently accessed data stored in an in-memory cache avoids roundtrips to the database, providing sub-millisecond latency.
- In microservice architectures, a well-designed caching strategy decreases network costs and improves overall application performance.
- Checking the cache first for data retrieval saves roundtrips to the database, reducing latency associated with database calls.
- Advanced query optimization techniques can improve database performance, but caching is particularly effective for frequently accessed data.
- Designing a caching strategy involves considerations such as what data to cache, duration of storage in the cache, and more based on performance requirements and data access patterns.

Database Sharding
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/1af6afba-6415-4079-922a-8ebdbbea518f)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/26d2f925-a781-4919-911f-7ab64792497d)

- Sharding is a solution for optimizing database performance as your application grows, allowing you to scale out write transactions.
- Sharding involves partitioning data across servers based on a shard key, improving both read and write performance by distributing data volumes efficiently.
- Each shard functions as an individual database, and queries are executed in parallel across all shards for horizontal scalability.
- Real-life use cases include sharding a customer database based on customer ID for processing isolation.
- Choosing the shard key is critical; options include customer ID, last name alphabetical filter, or a hash strategy to avoid imbalance in shard sizes.
- Implementing sharding requires significant application-level changes, and optimal sharding techniques are crucial.
- Complex querying involving multiple shards introduces complexity; queries without leveraging the shard key are executed across all shards.
- Maintaining shard allocation balance is essential to ensure even data distribution among existing shards.


Database Design in a Microservice Architecture 
--
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/85150c17-3330-4ea7-8f42-9a1802a4ddf8)
![image](https://github.com/pavankumar0077/Aws-Devops/assets/40380941/04d47871-c480-45fe-af14-3894bd23fc2b)

- In a microservice architecture, handling database changes is challenging.
- Designing cloud-native services involves having each microservice with its own separate database, enabling independent deployment and scaling.
- Decentralized data management architecture, where each service has a separate data store, is common for highly scalable distributed systems.
- Having a single monolithic shared database in services hinders scalability during traffic spikes.
- Traditional applications often use shared databases, but tight coupling between services makes independent deployment difficult.
- Scaling options are limited in a monolithic database, as you can only scale the entire database, not individual components.










