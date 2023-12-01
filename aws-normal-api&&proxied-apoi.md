**Normal API**:
Backend Management:

Approach: Traditional API involves manual management of backend servers, load balancing, and scaling.
Control: You have more control over the infrastructure but are responsible for its maintenance.
Responsibilities:

Configuration: You need to configure and manage various aspects like authentication, authorization, request/response transformation, caching, and traffic throttling.
Infrastructure Maintenance:

Maintenance: Infrastructure maintenance tasks are typically manual and require more attention from developers or DevOps teams.



**Proxied API with API Gateway**:
Backend Management:

Approach: API Gateway acts as a proxy, handling tasks like authentication, authorization, request/response transformation, caching, and traffic throttling.
Simplification: Simplifies API management, allowing developers to focus more on application logic.
Responsibilities:

Outsourcing: API Gateway takes care of many responsibilities, reducing the need for manual configuration of various aspects.
Infrastructure Maintenance:

Automation: API Gateway automates many aspects of infrastructure maintenance, making it easier for developers to deploy and manage APIs.
Commonalities:
Scalability: Both normal APIs and proxied APIs can scale, but proxied APIs benefit from the automation and scalability features provided by API Gateway.

Security: Both types of APIs can be secured, but proxied APIs benefit from built-in security features provided by API Gateway, such as API key management, OAuth, and IAM roles.

Monitoring and Analytics: Both types can be monitored, but API Gateway offers detailed monitoring and analytics for APIs, making it easier to track usage, errors, and latency.

Use Cases:
Normal API Use Cases:

More control over the infrastructure.
Specific requirements for backend server management.
Proxied API Use Cases:

Simplified API management.
Focus on application logic rather than infrastructure details.
Automation of common tasks.
