
# 🔥 50 AWS Platform Engineer Interview Questions and Answers with Examples

---

## 🔹 AWS Core Concepts & Architecture

**1. What is the AWS Shared Responsibility Model?**  
**A:** AWS secures the infrastructure (hardware, software, networking), while customers are responsible for securing their data, identity, and workloads.

**2. How do you design a scalable web application in AWS?**  
**A:** Use ALB with Auto Scaling EC2 or Lambda, store data in RDS/DynamoDB, use S3 for static files, and distribute via CloudFront.

**3. What is the difference between Availability Zones and Regions?**  
**A:** A Region is a geographic area, AZs are isolated data centers within a Region.

**4. When would you use EC2 over Lambda?**  
**A:** Use EC2 for long-running processes, custom OS, or legacy applications. Use Lambda for event-driven, short-running, scalable functions.

**5. How do you ensure high availability for an application hosted on EC2?**  
**A:** Deploy across multiple AZs, use ALB, configure Auto Scaling groups.

---

## 🔹 Infrastructure as Code (IaC)

**6. What’s the advantage of using Terraform over CloudFormation?**  
**A:** Terraform is multi-cloud, has a readable HCL language, modular design, and supports state management.

**7. How do you structure a large Terraform project?**  
**A:** Use modules, separate environments with workspaces or directory structure, manage variables and outputs cleanly.

**8. How do you manage Terraform state securely?**  
**A:** Store in S3 with encryption, enable DynamoDB for locking.

**9. What is a Terraform module?**  
**A:** A reusable configuration block. For example, a VPC module that provisions networking across projects.

**10. Example: Write a basic Terraform resource to create an S3 bucket.**  
```hcl
resource "aws_s3_bucket" "example" {
  bucket = "my-sample-bucket"
  acl    = "private"
}
```

---

## 🔹 Compute & Containers

**11. What’s the difference between ECS and EKS?**  
**A:** ECS is AWS-native for Docker containers, EKS is AWS-managed Kubernetes.

**12. When do you use Fargate?**  
**A:** For serverless containers where you don’t want to manage EC2 instances.

**13. How do you update a containerized app with zero downtime?**  
**A:** Use rolling updates with ECS/EKS, monitor health checks before promoting.

**14. What’s a task definition in ECS?**  
**A:** It defines how a container should run — image, resources, ports, environment.

**15. What’s the use of ALB in ECS?**  
**A:** Route traffic to services based on path/host rules, distribute load evenly.

---

## 🔹 Serverless & Event-Driven

**16. What are common Lambda use cases?**  
**A:** File processing (S3 triggers), API backends, cron jobs, stream processing.

**17. How do you handle retries in Lambda?**  
**A:** Enable DLQs (SQS/SNS), implement retry logic, use Lambda Destinations.

**18. What is the cold start problem?**  
**A:** Delay during Lambda initialization. Use provisioned concurrency to mitigate.

**19. Example: Lambda triggered by SQS to send SNS alert.**  
**A:** Use SQS as event source → Lambda → publish to SNS via SDK (Boto3/Node.js).

**20. What’s the best way to monitor Lambda?**  
**A:** Use CloudWatch metrics, logs, and set alarms for error/invocation rates.

---

## 🔹 Networking & VPC

**21. How do public and private subnets differ?**  
**A:** Public has route to IGW; private doesn’t. Use NAT Gateway for internet access from private subnets.

**22. How do you connect two VPCs?**  
**A:** VPC Peering or Transit Gateway.

**23. What is VPC Flow Logs?**  
**A:** Captures IP traffic logs for analysis and troubleshooting.

**24. What’s the role of NACL vs Security Group?**  
**A:** NACL = stateless, subnet-level; SG = stateful, instance-level.

**25. How do you restrict SSH access to EC2?**  
**A:** Use Security Groups with limited IPs, and optionally Bastion Host + SSM Session Manager.

---

## 🔹 CI/CD & DevOps

**26. How do you build a CI/CD pipeline for Lambda?**  
**A:** GitHub Actions → Lint/Test → Package → Deploy with SAM/Serverless Framework.

**27. What’s the purpose of CodeBuild?**  
**A:** Managed build service to compile, test, and create artifacts.

**28. How do you roll back a failed deployment?**  
**A:** Use Lambda aliases or ECS versioning, include rollback steps in pipeline.

**29. What’s Blue/Green Deployment?**  
**A:** Deploy new version alongside old, test, then switch traffic if healthy.

**30. How do you automate Terraform in CI/CD?**  
**A:** Run `terraform fmt`, `init`, `plan`, `apply` in pipelines, protect via manual approval.

---

## 🔹 Monitoring & Logging

**31. How do you monitor EC2 instances?**  
**A:** Use CloudWatch Agent for OS metrics, custom dashboards, and alerts.

**32. What is AWS X-Ray used for?**  
**A:** Distributed tracing to troubleshoot latency in microservices.

**33. How do you log from a Lambda function?**  
**A:** Use built-in `console.log()` (Node.js) or `print()` (Python) to CloudWatch Logs.

**34. How do you visualize metrics with Grafana?**  
**A:** Add CloudWatch as data source → build panels → secure via IAM roles.

**35. What is a CloudWatch Alarm?**  
**A:** Triggers actions (e.g., SNS) when metric thresholds are breached.

---

## 🔹 Security

**36. How do you secure S3 buckets?**  
**A:** Disable public access, use bucket policies and IAM roles, enable encryption.

**37. What’s the difference between IAM Role and IAM User?**  
**A:** Roles are assumed temporarily; users have long-term credentials.

**38. How do you enforce MFA for console users?**  
**A:** Use IAM policies with `aws:MultiFactorAuthPresent` condition.

**39. What’s a Service Control Policy (SCP)?**  
**A:** Applies org-wide restrictions in AWS Organizations.

**40. How do you audit changes to AWS resources?**  
**A:** Use AWS CloudTrail and Config to track and evaluate changes.

---

## 🔹 Real-World Scenarios & Behavioral

**41. Describe a time you debugged a failing Lambda.**  
**A:** Found a missing IAM permission by checking CloudWatch logs; updated policy and re-deployed.

**42. How did you improve cost-efficiency in a past project?**  
**A:** Replaced EC2 batch jobs with scheduled Lambda functions, saving compute cost.

**43. Have you faced an infrastructure drift?**  
**A:** Yes, fixed manually altered infra by enforcing Terraform CI checks and regular `plan` runs.

**44. Describe a time you worked with a multi-region architecture.**  
**A:** Deployed read replicas for RDS and replicated S3 for regional latency improvements.

**45. How do you ensure your team follows DevOps best practices?**  
**A:** Define IaC standards, enforce code reviews, use linters, and train developers.

---

## 🔹 Bonus Concepts

**46. What is an AWS Landing Zone?**  
**A:** Pre-configured multi-account environment using best practices for governance and security.

**47. What is AWS Control Tower?**  
**A:** Automates setup of Landing Zones and manages account provisioning and policies.

**48. How do you use Cisco ThousandEyes in AWS?**  
**A:** Monitor network paths, DNS, and HTTP endpoints across cloud regions and ISPs.

**49. What is BGP and how does it impact AWS networking?**  
**A:** BGP (Border Gateway Protocol) controls routing on the internet; impacts Direct Connect and multi-pathing.

**50. What is infrastructure immutability and why is it important?**  
**A:** Immutable infra is never modified after deployment — reduces drift, ensures consistency.

