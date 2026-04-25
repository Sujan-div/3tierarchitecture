Three-tier architecture is a design pattern that separates an application into three layers:
1.	Presentation Layer (Frontend) 
2.	Application Layer (Backend) 
3.	Data Layer (Database) 
This separation improves:
•	Scalability 
•	Security 
•	Maintainability

AWS-Based Three-Tier Architecture
 1. Presentation Layer
•	Handles user interface 
•	Accessible via browser 
AWS Services:
•	Amazon S3 (Static website hosting) 
•	Amazon CloudFront (CDN) 
•	Route 53 (DNS)

2. Application Layer
•	Contains business logic 
•	Processes requests from frontend 
AWS Services:
•	EC2 (Virtual servers) 
•	Auto Scaling Group 
•	Application Load Balancer (ALB)

 3. Data Layer
•	Stores application data 
AWS Services:
•	RDS (Relational Database) 
•	DynamoDB (optional NoSQL)

 
Security Best Practices
•	Use Security Groups: 
o	Allow HTTP/HTTPS only to ALB 
o	Allow DB access only from backend 
•	Use IAM roles instead of credentials 
•	Enable HTTPS (SSL/TLS


Scalability
•	Auto Scaling Group adjusts EC2 instances 
•	CloudFront caches content globally 
•	RDS can be scaled vertically or with read replicas 

Workflow
1.	User sends request via browser 
2.	Route 53 resolves domain 
3.	CloudFront caches and forwards request 
4.	ALB distributes traffic to EC2 
5.	EC2 processes logic 
6.	Data fetched/stored in RDS 
7.	Response sent back to user

Advantages
•	High availability 
•	Better performance 
•	Easier maintenance 
•	Improved security

Disadvantages
•	More complex setup 
•	Higher cost compared to monolithic systems 

