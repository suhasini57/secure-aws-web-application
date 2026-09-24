# EC2 Auto Scaling Setup

## 1. Objective

Configured Amazon EC2 Auto Scaling with the existing Application Load Balancer to automatically manage EC2 instances and maintain application availability.

The Auto Scaling Group was integrated with the existing Application Load Balancer and Target Group.

---

## 2. Architecture

The application architecture was enhanced by introducing an Application Load Balancer and Auto Scaling Group.

Internet → Application Load Balancer → Target Group → Auto Scaling Group → EC2 Instances → Nginx → Web Application

The Application Load Balancer distributes incoming requests to healthy EC2 instances.

The Auto Scaling Group manages the EC2 instances and can launch additional instances when required.

### Architecture Flow

Internet
↓
Application Load Balancer
↓
Target Group
↓
Auto Scaling Group
↓
EC2 Instance 1 → Nginx
EC2 Instance 2 → Nginx
↓
Web Application

## 3. Launch Template

A Launch Template was created to provide the configuration required when Auto Scaling launches new EC2 instances.

### Configuration

- Amazon Linux 2023
- Instance type: t3.micro
- IAM instance profile configured
- Existing EC2 security group configured
- User Data configured for automatic Nginx installation and configuration

---

## 4. User Data

The following User Data was configured in the Launch Template.

The script installs Nginx, enables the service, starts the service, and creates the application webpage.

---

## 5. Auto Scaling Group

An Auto Scaling Group was created using the Launch Template.

### Configuration

- Auto Scaling Group: aws-web-asg
- Minimum capacity: 1
- Desired capacity: 1
- Maximum capacity: 2
- Existing Target Group: aws-web-targets
- EC2 health checks: Enabled
- Elastic Load Balancing health checks: Enabled
- Health check grace period: 300 seconds

---

## 6. Application Load Balancer Integration

The Auto Scaling Group was associated with the existing Target Group.

The Application Load Balancer distributes HTTP requests to healthy EC2 instances registered with the Target Group.

---

## 7. Testing

### Test 1: Auto Scaling Instance Launch

The Auto Scaling Group successfully launched an EC2 instance using the configured Launch Template.

The User Data script automatically installed Nginx, enabled Nginx, started Nginx, and created the application web page.

### Test 2: Application Access

The application was successfully accessed through the Application Load Balancer.

Expected application output:

**Secure AWS Web Application**

**Application deployed using AWS Auto Scaling.**

### Test 3: Target Health

The Auto Scaling instance was registered with the Target Group.

The ALB health check verified that the Nginx web server was responding successfully.

**Result: Target Healthy**

### Test 4: Scaling

The Auto Scaling Group was tested by increasing the desired capacity.

The ASG successfully launched an additional EC2 instance using the Launch Template.

The new instance was registered with the Target Group and could serve the application through the ALB.

---

## 8. Implementation Result

The Auto Scaling implementation was successfully completed.

The project now uses an Application Load Balancer, Target Group, Auto Scaling Group, EC2 instances, Nginx, and the web application.

This implementation demonstrates automated EC2 provisioning, application initialization using User Data, health checks, load balancing, and Auto Scaling.

---

## 9. Key Concepts Learned

- EC2 Launch Templates
- Auto Scaling Groups
- Minimum, desired, and maximum capacity
- Scaling policies
- EC2 health checks
- Elastic Load Balancing health checks
- User Data
- ALB and Auto Scaling integration
- Automatic EC2 instance provisioning
- High availability concepts
