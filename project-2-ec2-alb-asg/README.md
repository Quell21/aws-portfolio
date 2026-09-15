# Project 2 — EC2 Web Server

## What I Built
An Apache web server running on EC2 inside a custom VPC,
accessible via HTTP from the public internet.

## Architecture
- Instance: t2.micro, Amazon Linux 2023
- VPC: aws-portfolio-vpc
- Subnet: portfolio-public-1 (public)
- Security Group: portfolio-web-sg (ports 80, 443, 22)
- Bootstrapped with User Data script

## Key Concepts Learned
- EC2 launch workflow and instance types
- Key pairs and SSH access
- User Data scripts for automated configuration
- Public vs private subnet placement

ssh -i ~/path-to-keypairs/portfolio-key.pem ec2-user@YOUR-PUBLIC-IP
