
# ✅ AWS Platform Engineer – Interview Q&A

---

## 📄 AWS Architecture & Platform Questions

**Q1: How would you architect a highly available, fault-tolerant AWS service?**  
**A:**  
Design across **multiple Availability Zones (AZs)** using **Elastic Load Balancers**, **Auto Scaling Groups**, and services like **RDS Multi-AZ**, **S3**, and **Route 53**. Use **CloudFront** for distribution and **SQS/SNS** to decouple services.

**Q2: What are the differences between SQS and SNS?**  
**A:**  
- **SNS**: Pub-sub model, pushes to subscribers.  
- **SQS**: Message queue model, polled by consumers.  
Use SNS for broadcasting, SQS for decoupling services.

**Q3: How do you monitor applications using CloudWatch and Grafana?**  
**A:**  
Use **CloudWatch Logs**, **Metrics**, **Alarms**, and **Grafana dashboards** for real-time and historical insights.

**Q4: How do you manage secrets in AWS?**  
**A:**  
Use **AWS Secrets Manager** or **SSM Parameter Store** with KMS encryption and IAM roles.

**Q5: Describe your experience with AWS Lambda.**  
**A:**  
Built event-driven systems using Lambda + SQS/SNS/API Gateway. Managed concurrency, cold starts, and monitoring via CloudWatch.

---

## 🛠 Infrastructure as Code (IaC) Questions

**Q6: Which IaC tools do you use and why?**  
**A:**  
**Terraform** for its modular, cross-cloud support. Also used **CloudFormation** for native AWS automation.

**Q7: How do you manage Terraform state?**  
**A:**  
Use **S3 remote backend** with **DynamoDB** for state locking.

**Q8: Explain a Terraform module you’ve written.**  
**A:**  
Created reusable modules for VPC, EC2, IAM roles, CloudWatch alarms with input variables and outputs.

**Q9: How do you secure sensitive data in IaC?**  
**A:**  
Avoid hardcoding, use environment variables, secrets managers, and `sensitive = true` in Terraform.

---

## 🌀 DevOps & CI/CD Questions

**Q10: Describe a full CI/CD pipeline you've built.**  
**A:**  
GitHub → Lint/Test → Build (CodeBuild) → Terraform Apply → Deploy (Lambda/ECS) → Notify via Slack/SNS.

**Q11: How do you handle blue/green deployments?**  
**A:**  
Deploy new version to green, switch traffic via Route 53/ALB, test, then promote.

**Q12: What tools do you use for automation?**  
**A:**  
**Terraform**, **GitHub Actions**, **Jenkins**, **Lambda**, **Docker**.

**Q13: How do you manage rollbacks?**  
**A:**  
Use versioned artifacts, Lambda aliases, and manual/automated rollback steps in pipeline.

---

## 💻 Programming & Scripting Questions

**Q14: What languages do you use for AWS scripting?**  
**A:**  
Primarily **Python** (Boto3), Bash, and Node.js for Lambdas.

**Q15: Can you write a Lambda that processes SQS and triggers SNS?**  
**A:**  
Yes. SQS triggers Lambda → parse → publish to SNS using Boto3.

**Q16: How do you manage retries/logs in Lambda?**  
**A:**  
Use DLQs, structured logs to CloudWatch, and Lambda Destinations.

**Q17: How do you structure code for maintainability?**  
**A:**  
Modular code, separation of concerns, use of Lambda Layers, tests, and clear documentation.

---

## 📊 Monitoring & Observability Questions

**Q18: How do you integrate Grafana with AWS?**  
**A:**  
Add CloudWatch as data source → build dashboards → use IAM roles for access.

**Q19: What metrics/alerts do you monitor?**  
**A:**  
Lambda errors/throttles, API latency, EC2 CPU, queue depth, custom KPIs.

**Q20: How do you approach observability in microservices?**  
**A:**  
Structured logs, X-Ray for tracing, Grafana dashboards, alerting, and central log aggregation.

---

## 🌐 Cisco ThousandEyes Questions

**Q21: What is ThousandEyes and how do you use it?**  
**A:**  
Network visibility tool to monitor internet paths, cloud services. Use for diagnostics and performance.

**Q22: How does it support monitoring?**  
**A:**  
Agent-based tests simulate user paths; detect ISP, DNS, or latency issues.

**Q23: What insights has it helped uncover?**  
**A:**  
CDN delays, BGP misroutes, regional service outages.

---

## 📄 Behavioral & Soft Skills Questions

**Q24: Describe a challenging AWS project.**  
**A:**  
Migrated monolith to microservices using Lambda/API Gateway, Terraform, and CI/CD.

**Q25: How do you handle production incidents?**  
**A:**  
Follow runbooks, rollback, RCA postmortem, and document learnings.

**Q26: How do you collaborate in teams?**  
**A:**  
Agile ceremonies, good documentation, shared design sessions.

**Q27: How do you document cloud infra?**  
**A:**  
Terraform-docs, Lucidchart diagrams, internal Confluence pages.

---

## 🏆 Bonus Points

- AWS Certified Architect / DevOps Engineer  
- Docker, ECS, Kubernetes experience  
- Strong focus on automation, observability, and secure architecture
