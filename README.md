# Three-Tier Architecture on AWS

## 📌 Introduction

Three-tier architecture is a software design pattern that separates an application into three logical layers: the presentation layer, application layer, and data layer. This separation improves scalability, security, and maintainability by isolating responsibilities across different components of the system.

In modern cloud environments, especially using Amazon Web Services (AWS), this architecture is widely used to design scalable and highly available applications.

---

## 🧱 Architecture Overview

The three layers are:

1. **Presentation Layer (Frontend)**
2. **Application Layer (Backend)**
3. **Data Layer (Database)**

Each layer performs a specific role and communicates with the adjacent layer.

---

## 🖥️ Presentation Layer (Frontend)

The presentation layer is responsible for handling user interaction. It displays content to users and collects input such as form submissions or button clicks.

In AWS, this layer is typically hosted using static hosting services.

### AWS Components:
- **Amazon S3**: Stores static files such as HTML, CSS, and JavaScript.
- **Amazon CloudFront**: A Content Delivery Network (CDN) that caches content closer to users for faster delivery.
- **Amazon Route 53**: Provides DNS resolution to map domain names to resources.

### How it works:
When a user accesses the website, the request is first resolved by Route 53. The request is then routed through CloudFront, which either serves cached content or fetches it from the S3 bucket.

---

## ⚙️ Application Layer (Backend)

The application layer contains the business logic of the system. It processes user requests, performs operations, and communicates with the database.

### AWS Components:
- **Amazon EC2**: Hosts the backend application (e.g., APIs).
- **Application Load Balancer (ALB)**: Distributes incoming traffic across multiple EC2 instances.
- **Auto Scaling Group**: Automatically adjusts the number of EC2 instances based on traffic.

### How it works:
Requests from the frontend are sent to the Load Balancer, which distributes them across available EC2 instances. These instances process the logic (e.g., authentication, order processing) and may interact with the database.

---

## 🗄️ Data Layer (Database)

The data layer is responsible for storing and managing application data securely and efficiently.

### AWS Components:
- **Amazon RDS**: Managed relational database service (e.g., MySQL, PostgreSQL).
- **Amazon DynamoDB (optional)**: NoSQL database for high-performance applications.

### How it works:
The backend communicates with the database to store and retrieve data. Direct access from the frontend to the database is not allowed for security reasons.

---

## 🔄 Request Flow

1. A user enters a URL in the browser.
2. Route 53 resolves the domain name.
3. CloudFront delivers cached content or forwards the request to S3.
4. The frontend sends API requests to the backend.
5. The Load Balancer routes requests to EC2 instances.
6. The backend processes the request and interacts with the database.
7. The database returns data to the backend.
8. The backend sends a response back to the frontend.
9. The user sees the result in the browser.

---

## 📊 Architecture Diagram

![Three Tier Architecture](architecture.png)<img width="1047" height="671" alt="pYjCx72bW-ts3s5lR_htGOkQGcSTla_BmINekf5hH-xTr4JsWFFjyO8VaXGjDEKmUbyM2qcIBqZbRdYIkcx7pIyoVeWb6qkZeQ4OhtowcNel0JmfuMAXNY2dIsNqLwvIRQOlndr0im4o0lveJp_23fFoLqxxEiaIg36Aat41F9UWUczYUSrfoEd0SJKdMY83" src="https://github.com/user-attachments/assets/9d968ad0-5a37-488c-ba2c-5c20f2edeb2e" />

---

## 🔐 Security Considerations

- Use Security Groups to restrict access:
  - Allow HTTP/HTTPS only to the Load Balancer.
  - Allow database access only from backend servers.
- Use IAM roles instead of hardcoded credentials.
- Enable HTTPS using SSL/TLS certificates.
- Keep the database in a private subnet.

---

## ⚡ Scalability and Availability

- **Auto Scaling** ensures the system handles traffic spikes.
- **CloudFront** improves performance through caching.
- **Multi-AZ RDS deployment** improves database availability.
- **Load Balancer** prevents a single point of failure.

---

## ✅ Advantages

- Clear separation of concerns
- Improved scalability and flexibility
- Enhanced security
- Easier maintenance and updates

---

## ⚠️ Disadvantages

- More complex to design and manage
- Higher cost compared to simpler architectures
- Requires knowledge of multiple services

---

## 🧠 Conclusion

Three-tier architecture is a fundamental design pattern in modern cloud-based applications. By separating the frontend, backend, and database layers, developers can build systems that are scalable, secure, and easier to manage.

AWS provides a wide range of services that make implementing this architecture efficient and reliable in real-world scenarios.


