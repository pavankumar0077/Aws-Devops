## AWS E2E Architecture for Web App

![Uploading image.png…]()

CloudFront 
--
- CDN  - content delivery network
- Differnet content based on the Geo-location
- Offline cache

WAF (Web application Firewall)
--
- Protects your web application from web exploits,
- Has the OWASP Code rule set
- We can customzie the traffic

AWS Shield
--
- We good for DDOS protection

Guard Duty
--
- In case your server is compromised for XYZ reason
- It will monitor and notifity you.

S3 Bucket
--
- Backup of the instances and the DB

RDS
--
- Database

Cloudwatch
--
- Monitoring and SNS for notification

Lambda
--
- To do some action based on requirement





