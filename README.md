# Secure AWS Web Application Deployment

A secure AWS web application deployment using VPC, EC2, IAM, and Nginx.

## Project Objective

The objective of this project is to deploy a web application on AWS using a secure and structured network architecture.

## AWS Services Used

- Amazon VPC
- Public and Private Subnets
- Internet Gateway
- Route Tables
- Amazon EC2
- Security Groups
- AWS IAM
- Nginx Web Server

## Project Architecture

![AWS Architecture Diagram](architecture/aws-architecture-diagram.png.docx)

The initial architecture will be:

Internet → Internet Gateway → Public Subnet → EC2 → Nginx → Website

## Project Implementation

1. Create and configure the VPC.
2. Configure public and private subnets.
3. Configure route tables and Internet Gateway.
4. Launch an EC2 instance.
5. Configure Security Groups.
6. Install and configure Nginx.
7. Deploy a sample website.
8. Document the deployment and troubleshooting steps.

## Security Considerations

- Restrict SSH access to the required IP address.
- Allow only necessary inbound traffic.
- Use IAM roles instead of hardcoded AWS access keys.
- Keep private resources in private subnets.
- Monitor AWS resources and remove unused resources.

## Future Improvements

- Add a private EC2 instance.
- Configure a NAT Gateway.
- Add an Application Load Balancer.
- Containerize the application using Docker.
- Configure CI/CD using GitHub Actions.
- Automate infrastructure using Terraform.

## Project Status

In Progress
