# AWS-Cloud-monitoring
This repository contains a two-part project designed to establish a secure, monitored AWS environment with alerts for sensitive actions and security configurations for AWS EC2 instances.

# Prerequisites
AWS Free Tier account with basic setup completed

AWS CLI installed and configured


# Part 1: AWS Monitoring using CloudTrail & Eventbridge
In Part 1, we implement an alerting system to monitor critical root user actions, ensuring visibility into sensitive API calls.

## Features:
SNS for Email Notifications: Configured SNS to send email alerts for specific events.

CloudTrail Logging: Enabled CloudTrail to log all management events across regions.

EventBridge Rule: Created a rule to trigger alerts on GetCallerIdentity API calls made by the root user.

API Call Alert Testing: Tested the setup by simulating root API calls and verifying email notifications.
