# Application Load Balancer Setup

## 1. Objective

Deploy an Application Load Balancer (ALB) in front of the existing EC2/Nginx web server to distribute incoming HTTP traffic and monitor the health of the web server.

## 2. Architecture

The application uses an internet-facing Application Load Balancer to receive HTTP traffic and forward requests to the EC2 instance running Nginx.

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

## 3. ALB Configuration

The Application Load Balancer is configured as an internet-facing load balancer to accept HTTP traffic from the internet.

### Configuration

* **Name:** aws-learning-alb
* **Scheme:** Internet-facing
* **Protocol:** HTTP
* **Port:** 80

## 4. Target Group

The target group is used to register the EC2 instance running Nginx with the Application Load Balancer.

### Configuration

* **Name:** aws-web-targets
* **Protocol:** HTTP
* **Port:** 80
* **Target:** EC2 - new-vm
* **Health Check Path:** `/`
* **Success Code:** `200`

The Application Load Balancer uses the health check to verify that the Nginx web server is responding successfully.

## 5. Security Configuration

Separate security group rules are used for the Application Load Balancer and the EC2 instance.

### ALB Security Group

* **Inbound:** HTTP (Port 80) from the internet (`0.0.0.0/0`)

### EC2 Security Group

* **Inbound:** HTTP (Port 80) from the ALB Security Group

This configuration allows users to access the application through the ALB while restricting direct HTTP access to the EC2 instance.

## 6. Testing

The Application Load Balancer and Nginx web server are tested using target health checks.

### Test 1: Nginx Running

```text
Nginx running
     ↓
Target healthy
     ↓
ALB DNS
     ↓
Website accessible
```

Expected result: The EC2 target is healthy and the website is accessible through the ALB DNS name.

### Test 2: Nginx Stopped

```text
Nginx stopped
     ↓
Target unhealthy
```

Expected result: The target becomes unhealthy because the Nginx web server is no longer responding on port 80.

### Test 3: Nginx Restarted

```text
Nginx restarted
     ↓
Target healthy
```

Expected result: The target becomes healthy again after the Nginx web server starts responding to the health check.

