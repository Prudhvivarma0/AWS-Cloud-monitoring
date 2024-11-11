# AWS-Cloud-monitoring
This repository contains a two-part project designed to establish a secure, monitored AWS environment with alerts for sensitive actions and security configurations for AWS EC2 instances.

# Prerequisites
AWS Free Tier account with basic setup completed

AWS CLI installed and configured


# Part 1: AWS Monitoring using CloudTrail & Eventbridge
In Part 1, we implement an alerting system to monitor critical root user actions, ensuring visibility into sensitive API calls.

#### Features:
- **SNS for Email Notifications**: Configured SNS to send email alerts for specific events.
- **CloudTrail Logging**: Enabled CloudTrail to log all management events across regions.
- **EventBridge Rule**: Created a rule to trigger alerts on GetCallerIdentity API calls made by the root user.
- **API Call Alert Testing**: Tested the setup by simulating root API calls and verifying email notifications.

### Part 2: EC2 Instance Setup and CloudWatch Monitoring

In Part 2, we focus on securely configuring an EC2 instance and implementing monitoring to ensure performance and security compliance.

#### Features:
- **EC2 Instance Setup**: Launched and configured an EC2 instance with Amazon Linux 2, secured with a customized security group and SSH access restrictions.
- **User Access Control**: Created a new user with sudo privileges, disabled root login, and enforced key-based SSH authentication.
- **CloudWatch Monitoring**: Configured CloudWatch alarms to monitor CPU utilization, sending alerts when utilization exceeds defined thresholds.
- **Alarm Testing**: Simulated high CPU usage to test the CloudWatch alarm setup and verified SNS email notifications for efficient monitoring.

This configuration helps ensure secure access and ongoing monitoring, enhancing instance stability and performance visibility.

📄 **Note:** A detailed report highlighting the setup process and screenshots of testing will be added soon. Stay tuned!
