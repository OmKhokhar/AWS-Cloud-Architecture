# AWS Infrastructure Project

## Overview

This project encompasses a comprehensive setup and deployment of various AWS services including VPC setup, EC2 instances, Lambda functions, and database setups following the stringent guidelines provided in the project specifications. Each setup is carefully designed to adhere to the required configurations and settings to ensure a secure, scalable, and functional AWS infrastructure.

## Project Architecture

### **Task A: VPC**

#### **VPC s3886577**
- **Region**: `us-east-1`
- **Network Address**: `xx.xx.0.0/16`
- **Subnets**:
  - Public and private subnets configured in two different availability zones, each housing 512 IPv4 addresses.
- **Route Tables**:
  - Associated public subnets with a route table and private subnets with a different route table.
- **Security Group** (s3886577-public):
  - Allows HTTP, HTTPS, and SSH access from the internet.

#### **VPC s3886577-1**
- **Region**: `us-west-2`
- **Network Address**: `xx.xx.0.0/16`
- **Subnets**:
  - Public and private subnets structured similarly to VPC `s3886577`.
- **Connection**:
  - Established VPC peering connection between `s3886577` and `s3886577-1`.

### **Task B: EC2**
- **Instance** (s3886577-Web Server 1):
  - **AMI**: Amazon Linux 2023.
  - **Instance Type**: t2.small.
  - **Security Group**: s3886577-public.
  - **Public IP**: Static (unchanged upon reboot).
- **Server**:
  - Configured with a web server, database, and PHP libraries.

### **Task C: S3, IAM & Lambda**
- **Bucket 1** (s3886577-s3):
  - **Region**: `us-east-1`.
  - **Hosting**: Set up to host a webpage displaying the student ID.
- **Lambda Function**:
  - Logs bucket object creation events to CloudWatch.
- **Bucket 2** (s3886577-iam):
  - **Region**: `us-east-1`.
  - **Connection**: Configured private connection between public subnets of VPC and this bucket without requiring authentication.

### **Task D: EBS & EFS**
- **EBS Volume**:
  - **Type**: GP3.
  - **Size**: 10GB.
  - Set up with a file system and a snapshot created for backup and recovery.
- **EFS** (s3886577-efs):
  - Mounted to the EC2 instance.

### **Task E: RDS & DynamoDB**
- **Security Group** (s3886577-DB Access):
  - Allows MySQL connections from the instance associated with the security group created in Task A.
- **RDS**:
  - **Database**: MySQL.
  - **Instance Type**: db.t3.micro.
  - **Storage**: 20GB SSD (GP2).
  - **Deployment**: Multi-AZ with replica.
- **DynamoDB**:
  - Table configured with the required attributes and entries. 
  - Query created to fetch all records including "coke".

### **Task F: ELB & Auto Scaling**
- **ELB** (s3886577-ELB):
  - Configured to distribute traffic across instances in private subnets.
- **Auto Scaling Group** (s3886577-Auto Scaling):
  - **Configuration**:
    - Desired capacity: 2.
    - Min capacity: 1.
    - Max capacity: 3.
  - **Scaling Policy**: Scales when average CPU utilization exceeds 60%.

### **Task G: System Architecture**
- **Diagram**:
  - Illustrated all components including CIDRs, IP addresses, route tables, etc., showcasing the complete system architecture.

## Screenshots

Screenshots evidencing the completion of each task are uploaded in this repository. The naming convention followed is: `Task[Task Letter]_[Detail]-[Specific Item].png`.

## Contact

For any queries regarding this project, contact:
- **Om Khokhar**
  - **Student ID**: s3886577
  - **Email**: s3886577@student.rmit.edu.au

Thank you for reviewing our meticulously built AWS infrastructure project. We look forward to your feedback.
