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

# Project 3 — Application Load Balancer & Auto Scaling #

## What I Built
An Application Load Balancer distributing traffic across
multiple EC2 instances managed by an Auto Scaling Group,
spread across 2 Availability Zones.

## Architecture
- ALB: Internet-facing across portfolio-public-1 and portfolio-public-2
- Target Group: HTTP health checks on path /
- ASG: min 1, desired 2, max 4 — spans both AZs
- Scaling Policy: Target tracking CPU at 50%
- Launch Template: Amazon Linux 2023, t2.micro, public IP enabled

## Security Design
- ALB SG: accepts 80/443 from internet (0.0.0.0/0)
- EC2 SG: accepts 80/443 ONLY from portfolio-alb-sg (security group chaining)
- SSH on port 22 restricted to my IP only
- EC2 instances not directly accessible from internet on HTTP/HTTPS

## Key Concepts Learned
- Security group chaining — EC2 only accepts traffic sourced from ALB SG
- Launch Templates define WHAT, ASG defines WHERE (subnets/AZs)
- ELB health checks vs EC2 health checks
- IMDSv2 token-based metadata in User Data scripts
- Auto-assign public IP must be set in Launch Template network settings
- ASG replaces manually managed EC2 — infrastructure is now self-healing

## Problems Solved
- 503 error caused by Apache not running — fixed via User Data
- ALB not switching AZs — caused by only one instance registered
- Day 3 server showing behind ALB — deregistered manually registered instance
- Instances showing private IP only — enabled auto-assign public IP in Launch Template
