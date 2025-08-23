# Campus Automation System  

## 📌 Project Overview  
The **Campus Automation System** is a serverless, cloud-based solution designed to automate key campus operations, making it easier for **students, placement faculty, and visiting companies** to interact on a single digital platform.  

The system leverages **AWS Cloud Services** to ensure scalability, security, and high availability. It provides a centralized platform for managing student data, company visits, placement processes, and real-time information sharing.  

---

## 🚀 Features  
- Student registration and management.  
- Placement drive management for faculty.  
- Company portal for recruitment coordination.  
- Secure and scalable architecture using AWS serverless stack.  
- Automatic conversion from **HTTP → HTTPS** via **Amazon CloudFront** for secure communication.  
- Fully managed backend with serverless compute and NoSQL database.  

---

## 🛠️ Tech Stack (AWS Services Used)  

- **Amazon S3 (Storage Only)**  
  - Used as storage for static files and application assets.  
  - Configured as the origin for CloudFront distribution.  

- **Amazon CloudFront**  
  - Distributes content globally with low latency.  
  - Connects directly to the **S3 bucket** as origin.  
  - Configured with **SSL/TLS** certificates to enforce **secure HTTPS** communication.  

- **Amazon API Gateway**  
  - Serves as the entry point for all backend requests.  
  - Exposes REST APIs securely to interact with the system.  

- **AWS Lambda**  
  - Serverless compute used for executing business logic.  
  - Handles operations like student registration, placement tracking, and company data processing.  

- **Amazon DynamoDB**  
  - A fully managed NoSQL database used to store student, faculty, and company data.  
  - Offers scalability, low latency, and high availability for real-time access.  

- **IAM Roles & Policies**  
  - Provides fine-grained access control across services.  
  - Ensures only authorized entities can perform operations (e.g., Lambda accessing DynamoDB).  

---

## ⚙️ System Workflow  

1. **Static Assets Storage**: Application files are stored in **Amazon S3**.  
2. **Secure Distribution**: **CloudFront** distributes content globally and enforces **HTTPS**.  
3. **API Requests**: Users interact with the system via **API Gateway**.  
4. **Business Logic**: API Gateway triggers **Lambda functions** to process requests.  
5. **Data Storage**: Student, company, and placement records are stored in **DynamoDB**.  
6. **Access Control**: All services are secured with **IAM Roles & Policies**.  

---

## 📂 Project Structure  

```
/campus-automation-system
│── s3-storage/            # Files stored in S3
│── backend/
│   ├── lambdas/           # AWS Lambda functions
│   ├── api-gateway/       # API Gateway configurations
│   └── dynamodb/          # Table definitions
│── cloudfront/            # CloudFront distribution settings
│── README.md              # Project documentation
```

---

## 🔐 Security Implementation  
- Enforced **HTTPS** using **CloudFront** with SSL certificates.  
- Configured **IAM Roles** to restrict unnecessary access between services.  
- Used **API Gateway** authorization mechanisms for secure API calls.  

---

## ⚡ Deployment Instructions  

Follow these steps to deploy the **Campus Automation System** on AWS:  

### 1️⃣ Setup S3 and CloudFront  
- Create an **S3 bucket** and upload your static website files or assets.  
- Make sure the bucket is **private** (only CloudFront should access it).  
- Create a **CloudFront Distribution** with the S3 bucket as the **origin**.  
- Attach an **SSL/TLS certificate** (via AWS Certificate Manager) to enable **HTTPS**.  
- Update your domain’s DNS (Route 53 or other provider) to point to the CloudFront distribution.  

### 2️⃣ Configure API Gateway  
- Create a **REST API** using **Amazon API Gateway**.  
- Define endpoints for different operations (e.g., student registration, placement management, company portal).  
- Enable **CORS** if the frontend interacts with the APIs.  

### 3️⃣ Deploy Lambda Functions  
- Write your business logic inside **AWS Lambda functions**.  
- Attach necessary **IAM roles** to allow Lambda to interact with **DynamoDB**.  
- Connect Lambda functions to API Gateway methods as integrations.  

### 4️⃣ Setup DynamoDB  
- Create **DynamoDB tables** for:  
  - Students  
  - Companies   
- Define **primary keys** and configure indexes if needed for faster queries.  

### 5️⃣ Security & IAM Roles  
- Create **IAM Roles & Policies** to grant minimum required permissions:  
  - Lambda → DynamoDB (Read/Write)  
  - API Gateway → Lambda (Invoke)  
  - CloudFront → S3 (Read)  

### 6️⃣ Test the System  
- Access the frontend using the **CloudFront distribution domain**.  
- Verify that:  
  - Static assets load over **HTTPS**.  
  - API calls are routed through **API Gateway** and executed by **Lambda**.  
  - Data is stored and retrieved correctly from **DynamoDB**.  

---

## 📈 Future Enhancements  
- Add authentication and authorization using **Amazon Cognito**.  
- Enable real-time notifications using **Amazon SNS** or **EventBridge**.  
- Integrate analytics dashboard for placement statistics.  
- Multi-language frontend support for better accessibility.  


