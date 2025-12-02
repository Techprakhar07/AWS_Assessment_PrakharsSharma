# AWS Assessment – Prakhar Sharma

This repository contains solutions for all 5 AWS tasks assigned in the assessment.  
Each task includes:
- Explanation (4–8 lines as required)
- AWS screenshots
- CloudFormation Templates (IaC)
- Architecture Diagram (Task 5)

All AWS resources are created with prefix: **Prakhar_Sharma_**  
All resources were deleted after testing to stay within Free Tier.

---

# 🔹 Task 1 — Networking & Subnetting (VPC Setup)

### **Brief Explanation**
I designed a custom VPC with CIDR `10.0.0.0/16` to allow plenty of room for future subnets.  
Two public subnets (`10.0.1.0/24` & `10.0.2.0/24`) were created for Internet-facing components, and two private subnets (`10.0.3.0/24` & `10.0.4.0/24`) were created for backend services.  
An Internet Gateway was attached to enable public connectivity.  
A NAT Gateway was placed in a public subnet to allow private EC2 instances outbound internet access for updates.  
Separate route tables were configured for public and private subnets.

### **CIDR Ranges Used**
- VPC: `10.0.0.0/16`
- Public Subnet A: `10.0.1.0/24`
- Public Subnet B: `10.0.2.0/24`
- Private Subnet A: `10.0.3.0/24`
- Private Subnet B: `10.0.4.0/24`

### **Files**
- CloudFormation: `vpc-setup.yaml`
- Screenshots inside `/screenshots`

---

# 🔹 Task 2 — EC2 Static Website Hosting

### **Brief Explanation**
I launched a t2.micro EC2 instance inside the public subnet created in Task 1.  
Using UserData, Nginx was installed automatically and my resume HTML file was placed in `/var/www/html/index.html`.  
Port 80 was opened in a Security Group to allow public web access.  
Basic hardening steps included disabling password SSH login, using a key pair, and restricting SSH access to my IP.

### **Files**
- CloudFormation: `ec2-static-website.yaml`
- UserData Script: `user-data.sh`
- Screenshots: EC2, SG, Running Website

---

# 🔹 Task 3 — High Availability with ALB + ASG + Private EC2

### **Brief Explanation**
To achieve high availability, I migrated the EC2 workload from public to private subnets.  
An Internet-facing ALB distributes traffic across multiple Availability Zones.  
An Auto Scaling Group maintains healthy EC2 instances and scales based on demand.  
Instances access the internet via NAT Gateway.  
Traffic flow: **Client → ALB (Public Subnet) → Target Group → EC2 ASG (Private Subnets)**.

### **Files**
- CloudFormation: `alb-asg-private.yaml`
- Screenshots: ALB, Target Group, ASG, Private Instances

---

# 🔹 Task 4 — Billing & Free Tier Cost Monitoring

### **Brief Explanation**
Cost monitoring is important for beginners because AWS resources can accumulate charges quickly if not properly managed.  
Sudden bill increases usually occur due to unused EC2 volumes, NAT Gateway charges, load balancers, data transfer, or accidentally running non-Free Tier instances.  
A CloudWatch billing alarm was set at ₹100, and Free Tier usage alerts were enabled to avoid unexpected billing.

### **Files**
- Screenshots: Billing Alarm & Free Tier Alerts

---

# 🔹 Task 5 — AWS Architecture Diagram (draw.io)

### **Brief Explanation**
The architecture uses an Internet-facing ALB connected to an Auto Scaling Group running in private subnets for high scalability.  
A Multi-AZ RDS/Aurora database provides durability and strong consistency.  
ElastiCache (Redis) is used for caching frequently accessed data to improve performance.  
Security is enforced using Security Groups, NACLs, and optional WAF.  
CloudWatch is used for logging, metrics, and alarms.  
This architecture easily handles 10,000+ concurrent users with horizontal scaling.

### **Files**
- `aws_architecture_diagram.png`
- `aws_architecture_diagram_clean.svg`

---

# ✅ End of Repository
All tasks completed and verified.
All AWS resources deleted after testing.
