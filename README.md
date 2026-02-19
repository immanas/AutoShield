# 🛡️ AutoShield – Real Time AWS Resource Exposure Monitor & Alert System

AutoShield is like a digital security guard for your AWS cloud . AutoShield is a **serverless cloud security monitoring system** built on core AWS services. It detects critical misconfigurations like public S3 buckets, open EC2 ports, or overly permissive IAM policies in **real time**, alerts administrators via email using SNS, and logs violations into DynamoDB for future analysis and dashboarding.

## 🎯 Why This Project Exists
Modern cloud environments fail not because of lack of tools — but because of **lack of enforcement**.

- Alerts are generated → ignored  
- Dashboards show issues → no action taken  
- Manual remediation → too slow  

AutoShield solves this by **closing the gap between detection and action**.
It ensures:
> If something becomes insecure → it is fixed automatically.

## ⚖️ Problem vs Solution :

| Real-World Problem (What actually happens in cloud teams)              | AutoShield Approach (What this system enforces)                     |
|----------------------------------------------------------------------|--------------------------------------------------------------------|
| Misconfigured resources (e.g., public S3, open security groups) stay unnoticed for hours or days | Detects changes instantly via EventBridge and evaluates in real time |
| Security alerts are generated but ignored due to alert fatigue        | Eliminates alert dependency by triggering automatic remediation     |
| Manual remediation depends on engineers’ availability and response time | Executes fixes automatically using Lambda (no human dependency)     |
| Different engineers fix issues differently → inconsistent security posture | Enforces standardized, policy-driven remediation logic              |
| Periodic scans (cron jobs, audits) miss real-time exposure windows    | Event-driven model ensures zero-delay detection and response        |
| Scaling security checks across hundreds of resources is operationally expensive | Serverless architecture scales automatically per event load         |
| Lack of audit clarity on who fixed what and when                      | Logs every action in DynamoDB + CloudWatch for traceability         |


### 🛡️ Why AutoShield? — Core Features :

| 🚀 Feature | 📝 Description | 🎯 Why It Matters |
|-----------|----------------|------------------|
| **Real-Time Security Auditing** | AutoShield continuously listens for misconfiguration events (like public S3 buckets) via EventBridge. | Enables proactive detection instead of manual, delayed audits — increasing security posture. |
| **Serverless Architecture** | Built entirely on AWS Lambda, EventBridge, and DynamoDB with no servers to manage. | Ensures scalability, cost-efficiency, and minimal maintenance for continuous monitoring. |
| **DynamoDB-Powered Log Storage** | Misconfiguration findings are stored in a DynamoDB table. | Offers fast, scalable, and queryable access to historical security logs for audit/troubleshooting. |
| **DynbDashboard (Live Insights)** | A frontend dashboard displays logged events in real-time. | Provides immediate visibility and context for security teams or developers — no need to check logs manually. |
| **IAM + X-Ray + CloudWatch Integration** | IAM roles ensure least-privilege access, X-Ray helps trace execution, and CloudWatch tracks logs and alerts. | Guarantees end-to-end observability, traceability, and secure operations in production. |
| **S3 Misconfiguration Detection** | Specifically targets one of the most common AWS security risks: public S3 buckets. | Solves a real-world cloud security problem that leads to data leaks and compliance failures. |
| **EventBridge-Based Triggering** | Uses AWS EventBridge rules to trigger Lambda when relevant AWS events occur (e.g., S3 policy change). | Ensures instant response to misconfigurations — no delay or batch processing. |



## 🏗️ Architecture Diagram :


![AutoShield Architecture](architecture.png.png)

## 🧰 Tech Stack

- **Cloud:** AWS  
- **Compute:** AWS Lambda (stateless execution)  
- **Event Bus:** Amazon EventBridge  
- **Storage:** DynamoDB (rules + audit logs)  
- **Monitoring:** CloudWatch  
- **Language:** Python  
- **IaC:** Terraform (optional but recommended)

---

## ⚡ Quickstart (30-Second Run)

```bash
# Clone repository
git clone https://github.com/your-username/autoshield.git

# Deploy infrastructure
cd infra
terraform init && terraform apply

# Deploy Lambda
cd ../services
zip function.zip lambda_function.py
aws lambda update-function-code \
  --function-name autoshield \
  --zip-file fileb://function.zip

# Send test event
aws events put-events --entries file://event.json

```

## 🛡️ AutoShield – Contributions Welcome!

AutoShield is an open-source, serverless security auditing platform for AWS. We welcome contributions from cloud engineers, security enthusiasts, and DevSecOps professionals!

---

### 💡 Ideas You Can Work On

| 🔧 Feature Idea            | 📝 Description                                                                 |
|---------------------------|--------------------------------------------------------------------------------|
| 🔍 Multi-Resource Auditing | Extend AutoShield to audit EC2, IAM policies, and Security Groups along with S3 |
| 🧠 AI-based Risk Scoring   | Use ML to prioritize misconfigurations based on severity and historical trends  |
| 📊 Alert Dashboard Enhancements | Add sorting, filtering, and graph visualizations for easier insights    |
| 🔐 Role-Based Access       | Add authentication for different dashboard users (Admin vs Viewer)            |
| 📨 SNS/Slack Alerts        | Send real-time notifications to teams when critical issues are detected       |
| 📦 Archive to S3           | Automatically back up old logs to S3 Glacier for cost-efficient storage        |


### 🔍 About AutoShield

- 🌩️ Serverless AWS Monitoring  
- 🔐 Real-Time Misconfiguration Detection  
- 📚 DynamoDB-backed Security Logs  
- 📈 Live DynbDashboard Visualization  
- 🔁 EventBridge + Lambda Driven  
- 📦 Open Source – Fully Extendable  
- 🧭 Cloud-Native, DevOps-Ready  
- 🛠️ Built for Scale and Observability


### 🛠️ How to Contribute

- 🍴 Fork the repo  
- 📦 Create a new feature branch: `git checkout -b feature-name`  
- ✅ Make your changes and test them  
- 📬 Submit a pull request describing your enhancement  

### 🤝 Let’s Make Cloud Safer Together!
Made with ❤️ by **Manas Gantait**


