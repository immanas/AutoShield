# 🛡️ AutoShield – Real-Time AWS Resource Exposure Monitor & Alert System

AutoShield is a **serverless security automation system** that continuously monitors AWS resource configurations (like S3 buckets, security groups, etc.) for misconfigurations. It detects, logs, and alerts on publicly exposed resources in **real time**, giving teams immediate visibility into risky cloud changes — all without requiring expensive 3rd-party tools.

> Built with **AWS Lambda**, **EventBridge**, **AWS Config**, **SNS**, and **DynamoDB** — AutoShield is lightweight, modular, and production-ready.

---

## 🚀 Features

- ✅ **Real-Time Misconfiguration Detection** (e.g., public S3 buckets, open security group ports)
- 🔄 **Event-Driven** via Amazon EventBridge & AWS Config Rule triggers
- 📬 **SNS Alerts** via Email (or extendable to SMS / Slack)
- 🧠 **Modular Lambda Architecture** for scalable alert handling
- 🗃️ **Violation Logging to DynamoDB** for audit and dashboarding (DynbDashboard)
- 📦 Ready for **Infrastructure-as-Code** deployment (SAM/CDK support)

---

## 📁 Project Structure

