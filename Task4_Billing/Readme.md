# Task 4 — AWS Billing Alarm & Free Tier Usage Alerts

## 1. Explanation of Billing & Cost Monitoring
### a) Why cost monitoring is important
Beginners often leave resources running accidentally, which can lead to unexpected charges. Billing alerts help track monthly spending and prevent going beyond the Free Tier. Monitoring provides visibility into cost spikes and builds good cloud budgeting practices.

### b) Common reasons for sudden AWS bill increases
- Running EC2, RDS, or NAT Gateway longer than intended  
- High S3 usage or API request charges  
- Data transfer fees  
- Elastic IP charges when not attached  
- ALB, EKS, or paid-tier services left enabled  

---

## 2. Required Screenshots
- CloudWatch Billing Alarm at ₹100  
- Free Tier usage alerts enabled in Billing Console  

---

## 3. Notes
Billing alerts are global and do not require Terraform.  
