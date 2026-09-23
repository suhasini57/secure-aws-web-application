Application Load Balancer Setup

1. Objective: Deploy an Application Load Balancer (ALB) in front of the existing EC2/Nginx web server to distribute incoming HTTP traffic and monitor the health of the web server.

2. Architecture: The application uses an internet-facing Application Load Balancer to receive HTTP traffic and forward requests to the EC2 instance running Nginx.

```text
Internet
   ↓
Application Load Balancer
   ↓
Target Group
   ↓
EC2 - new-vm
   ↓
Nginx
   ↓
Web Application
```

3. ALB Configuration: The Application Load Balancer is configured as an internet-facing load balancer to accept HTTP traffic from the internet.
Configuration:
* **Name:** aws-learning-alb
* **Scheme:** Internet-facing
* **Protocol:** HTTP
* **Port:** 80
