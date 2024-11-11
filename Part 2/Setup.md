# EC2 Instance Setup and CloudWatch Monitoring Guide

This guide outlines the steps to set up an EC2 instance with SSH access, firewall rules, CloudWatch monitoring, and testing.

---

## Step 1: Launch an EC2 Instance

1. Log in to the **AWS Management Console** and navigate to the **EC2 Dashboard**.
2. Click **Launch Instance**, choose **Amazon Linux 2 AMI**.
3. Select **t2.micro** (free tier eligible) as the instance type.
4. Configure instance details and add storage (default settings).
5. **Create a new security group** to manage inbound/outbound rules.

## Step 2: Configure Security Group (Firewall)

1. Go to the **Security** tab for your EC2 instance.
2. Edit **Inbound Rules** in the security group:
   - Remove any SSH rule allowing access from anywhere.
   - Add an SSH rule allowing access only from your IP.
3. (Optional) Adjust **Outbound Rules** if necessary.

## Step 3: Connect to Your EC2 Instance

1. Open a terminal or SSH client.
2. Navigate to your key pair file and update permissions:
   ```bash
   chmod 400 your-key-pair.pem
3.ssh -i "your-key-pair.pem" ec2-user@your-instance-public-dns




## Step 4: Update and Secure Your Instance

Update packages:

1.sudo yum update -y

Install security updates:

1. sudo yum upgrade -y

Create a new user and grant sudo privileges:

1.sudo adduser newuser

2. sudo usermod -aG wheel newuser

Edit SSH config to disable root login and allow only key-based authentication:

Open the config file:

1.sudo vi /etc/ssh/sshd_config

2.Set PermitRootLogin no and PasswordAuthentication no.

Restart SSH:

1. sudo systemctl restart sshd


## Step 5: Set Up CloudWatch for Monitoring

1.Go to CloudWatch in the AWS Console.

2.In Alarms, click Create Alarm.

3.Choose the CPUUtilization metric for your instance.

4.Set the threshold to trigger when CPU utilization > 80% for 5 minutes.

5.Add notifications via an SNS topic with your email.

6.Review and create the alarm.



Conclusion
By following this guide, you've successfully set up a secure EC2 instance with restricted SSH access, basic firewall rules, and a monitored environment using CloudWatch. 
These steps ensure that your instance is not only accessible in a secure manner but also capable of alerting you to potential performance issues. Regular updates, 
limited access, and monitoring are crucial for maintaining a safe and efficient cloud environment.

## Step 6: Testing
1. Test SSH Access: Attempt to SSH into your instance from your IP to ensure connection, and confirm that SSH access from unauthorized IPs is denied.
   
2.Monitor CloudWatch Alarm:

Temporarily increase CPU utilization on the instance to test the CloudWatch alarm. Run the following command to create CPU load:

yes > /dev/null &

Wait 5 minutes to see if the alarm triggers an alert.

Once the alarm has been tested, terminate the CPU load process with:

killall yes

Email Notification: Check your email for the SNS notification to confirm it’s configured correctly.

Testing these steps ensures that the EC2 instance, security configurations, and CloudWatch monitoring are all set up and functioning as intended.
