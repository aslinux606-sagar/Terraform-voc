# Terraform VPC - AWS DevOps Project

This project provisions a complete AWS VPC infrastructure using Terraform, built entirely from mobile.

## Architecture
- VPC CIDR: 10.0.0.0/16
- Public Subnet: 10.0.1.0/24 (ap-south-1a)
- Internet Gateway for public access
- DNS Support Enabled

## Tech Stack
- Terraform
- AWS (VPC, Subnet, IGW)
- GitHub

## How to Deploy
```bash
terraform init
terraform plan
terraform apply
