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
resource "aws_route_table" "main_rt" {
  vpc_id = aws_vpc.main.id
  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.main_igw.id
  }
  tags = { Name = "main-route-table" }
}

resource "aws_route_table_association" "public_assoc" {
  subnet_id      = aws_subnet.public.id
  route_table_id = aws_route_table.main_rt.id
}

resource "aws_instance" "web" {
  ami           = "ami-0f5ee92e2d63afc18" # Amazon Linux 2 in ap-south-1
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.public.id
  tags = { Name = "WebServer" }
}
