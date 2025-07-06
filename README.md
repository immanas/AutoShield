# 🛡️ AutoShield – Real-Time AWS Resource Exposure Monitor & Alert System

AutoShield is a **serverless cloud security monitoring system** built on core AWS services. It detects critical misconfigurations like public S3 buckets, open EC2 ports, or overly permissive IAM policies in **real time**, alerts administrators via email using SNS, and logs violations into DynamoDB for future analysis and dashboarding.

Designed for **DevSecOps**, **Cloud Engineers**, and **Security Teams**, AutoShield helps prevent accidental data leaks and compliance violations in dynamic cloud environments.

---

## 🚨 Real-World Risks Addressed

| ⚠️ Misconfiguration      | 🔍 What Can Go Wrong                                                   |
|--------------------------|------------------------------------------------------------------------|
| **Public S3 Bucket**     | Customer data or proprietary code exposed to the internet              |
| **Open EC2 Port (22/3389)** | Remote server access, brute-force attacks, and lateral movement       |
| **Unrestricted IAM Policy** | Privilege escalation and full-account compromise                     |
| **Unencrypted RDS/EBS**  | Sensitive database content exposed without encryption at rest          |

---

## 🏗️ Architecture Overview

![AutoShield Architecture](architecture.png.png)

> **Detection Flow**:  
`AWS Config → EventBridge → Lambda → SNS & DynamoDB`

- **AWS Config** evaluates resource compliance using managed rules  
- **EventBridge** routes non-compliance events  
- **Lambda** logs violations & triggers alerts  
- **SNS** notifies security teams (via email)  
- **DynamoDB** stores violations for dashboarding (DynbDashboard coming soon)

---

## ⚙️ Tech Stack

| AWS Service      | Role in the System                              |
|------------------|--------------------------------------------------|
| **AWS Lambda**    | Event processing & alert logic (Python)         |
| **AWS Config**    | Detects violations in AWS resources             |
| **Amazon EventBridge** | Routes violation events to Lambda         |
| **Amazon SNS**    | Sends email alerts                              |
| **Amazon DynamoDB** | Stores violation logs                         |
| **IAM Roles**     | Provides least-privilege access to services     |

---

## 🛠 Features

- ✅ **Real-Time Misconfiguration Detection**
- 🔁 **Event-driven architecture**
- 📬 **Immediate SNS Alerts via Email**
- 🗂️ **Logs every violation in DynamoDB**
- 🧱 **Modular & Scalable Lambda structure**
- 💡 **Infrastructure-as-Code** via AWS SAM (`template.yaml`)
- 🚫 **No third-party dependencies** – all AWS-native

---

## 🔐 Detection Coverage

| AWS Service      | Detected Misconfigurations                            |
|------------------|--------------------------------------------------------|
| **S3**           | Public buckets, missing encryption                     |
| **EC2**          | Open ports like SSH/RDP                                |
| **IAM**          | Policies with wildcard access, missing MFA            |
| **RDS / EBS**    | Not encrypted at rest, publicly accessible instances   |
| **CloudTrail**   | Disabled or misconfigured logging                      |

---

## 🧪 Sample Violation Event (JSON)

```json
{
  "detail": {
    "configRuleName": "s3-bucket-public-read-prohibited",
    "resourceId": "test-bucket",
    "newEvaluationResult": {
      "complianceType": "NON_COMPLIANT"
    },
    "resourceType": "AWS::S3::Bucket"
  },
  "region": "ap-south-1"
}

