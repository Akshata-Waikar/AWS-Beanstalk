# 🚀 Project: Using AWS Elastic Beanstalk to Set Up RDS and Access It from an EC2 Instance

## 🧠 Objective

The objective of this project is to deploy a sample PHP web application using **AWS Elastic Beanstalk** with an integrated **Amazon RDS (MySQL)** database, and securely access the database from a separate **EC2 instance** within the same VPC.

This project demonstrates:
- Elastic Beanstalk for scalable app deployment
- Integrated RDS provisioning and secure networking
- EC2 connectivity to RDS for testing and administration

---

## 📘 Introduction

Modern cloud applications require reliable infrastructure that integrates application and database layers securely. AWS Elastic Beanstalk simplifies app deployment and management, while RDS handles relational data with high availability. This project sets up a PHP app using Elastic Beanstalk with a connected MySQL RDS database, and validates connectivity from an EC2 instance in the same VPC.

---

## 🧰 Technology Stack

| Component         | Tool / Service                | Purpose                                    |
|------------------|--------------------------------|--------------------------------------------|
| Application       | AWS Elastic Beanstalk (PHP)   | Deploy and manage web app                  |
| Database          | Amazon RDS (MySQL)            | Relational data management                 |
| Compute           | Amazon EC2                    | Access and test RDS connectivity           |
| Networking        | VPC, Subnets, Security Groups | Secure service-to-service communication    |

---


## 🛠️ Implementation Steps

### 🔹 Elastic Beanstalk Setup

1. Go to **AWS Elastic Beanstalk Console**
2. Click **Create application**
3. Choose **PHP Platform** and upload `index.php` zipped
4. In the **Database section**:
   - Enable RDS
   - Engine: MySQL
   - DB instance: `db.t3.micro`
   - Username: `admin`
   - Password: `YourPassword`
   - DB name: `ebdb`
5. Click **Create Environment**

### 🔹 EC2 Setup

1. Launch new EC2 instance:
   - AMI: Amazon Linux 2
   - Type: `t2.micro`
   - VPC: Same as EB
   - Public subnet with auto-assign public IP
   - Allow SSH (port 22) from your IP

### 🔹 Configure Security Groups

- Edit RDS security group:
  - Add **inbound rule**: MySQL (port 3306) from EC2 security group

---

## 🧪 Testing

### ✅ Connect from EC2


ssh -i your-key.pem ec2-user@<EC2_PUBLIC_IP>
sudo yum install -y mysql
mysql -h <RDS_ENDPOINT> -u admin -p

## Create test_db.php file
## Run test_db.php file
  - php test_db.php

## Conclusion
 This project demonstrated:
      - Elastic Beanstalk app deployment with integrated RDS
      - Secure service communication within a VPC
      - EC2-based testing of database access
      - A solid starting point for 3-tier architecture


Project Completed By : Akshata Waikar



