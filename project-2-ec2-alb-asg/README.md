# Project 2 — EC2 Web Server #

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

# Project 3 — ALB & Auto Scaling #

## What I Built
An Application Load Balancer distributing traffic across
multiple EC2 instances managed by an Auto Scaling Group.

## Architecture
- ALB: Internet-facing, across 2 public subnets
- Target Group: portfolio-tg with HTTP health checks
- Auto Scaling: min 1, desired 2, max 4 instances
- Scaling Policy: CPU target tracking at 50%

## Security Design
- ALB SG accepts traffic from internet on port 80/443
- EC2 SG only accepts port 80 traffic FROM the ALB SG
- SSH restricted to my IP only

## Key Concepts Learned
- ALB listener rules and target groups
- Launch templates vs launch configurations
- Target tracking vs step scaling policies
- Security group chaining between ALB and EC2

