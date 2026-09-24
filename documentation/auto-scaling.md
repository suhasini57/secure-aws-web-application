# EC2 Auto Scaling Setup

## 1. Objective

Configured Amazon EC2 Auto Scaling with the existing Application Load Balancer to automatically manage EC2 instances and maintain application availability.

The Auto Scaling Group was integrated with the existing Application Load Balancer and Target Group.

---

## 2. Architecture

The application architecture was enhanced by introducing an Application Load Balancer and Auto Scaling Group.

Internet -> Application Load Balancer -> Target Group -> Auto Scaling Group -> EC2 Instances -> Nginx -> Web Application

### Architecture Flow

Internet
|
v
Application Load Balancer
|
v
Target Group
|
v
Auto Scaling Group
|
+---- EC2 Instance 1 -> Nginx
|
+---- EC2 Instance 2 -> Nginx
|
v
Web Application

The Application Load Balancer distributes incoming HTTP requests to healthy EC2 instances.

The Auto Scaling Group manages the EC2 instances and can launch additional instances when required.

---

## 3. Launch Template

A Launch Template was created to provide the configuration required when Auto Scaling launches new EC2 instances.

### Configuration

- Operating System: Amazon Linux 2023
- Instance Type: t3.micro
- IAM Instance Profile: Configured
- Security Group: Existing EC2 security group
- User Data: Configured for automatic Nginx installation and configuration

---

## 4. User Data

User Data was configured in the Launch Template to automatically initialize newly launched EC2 instances.

The User Data configuration performs the following tasks:

- Installs Nginx
- Enables the Nginx service
- Starts the Nginx service
- Creates the web application page

This allows new EC2 instances launched by the Auto Scaling Group to automatically become web servers without manual configuration.

---

## 5. Auto Scaling Group

An Auto Scaling Group was created using the configured Launch Template.

### Configuration

- Auto Scaling Group: aws-web-asg
- Minimum Capacity: 1
- Desired Capacity: 1
- Maximum Capacity: 2
- Target Group: aws-web-targets
- EC2 Health Checks: Enabled
- Elastic Load Balancing Health Checks: Enabled
- Health Check Grace Period: 300 seconds

---

## 6. Application Load Balancer Integration

The Auto Scaling Group was associated with the existing Target Group.

The Application Load Balancer receives incoming HTTP requests and forwards them to healthy EC2 instances registered with the Target Group.

When the Auto Scaling Group launches an additional EC2 instance, the instance is automatically registered with the Target Group.

This allows the ALB to distribute traffic across the available healthy instances.

---

## 7. Testing

### Test 1: Auto Scaling Instance Launch

The Auto Scaling Group successfully launched an EC2 instance using the configured Launch Template.

The User Data configuration automatically installed Nginx, enabled the service, started the service, and created the application web page.

Result: Successful

---

### Test 2: Application Access

The application was successfully accessed through the Application Load Balancer.

Application output:

**Secure AWS Web Application**

**Application deployed using AWS Auto Scaling.**

Result: Successful

---

### Test 3: Target Health

The Auto Scaling instance was registered with the Target Group.

The Application Load Balancer health check verified that the Nginx web server was responding successfully.

Result: Target Healthy

---

### Test 4: Scaling

The Auto Scaling Group was tested by increasing the desired capacity.

The ASG successfully launched an additional EC2 instance using the configured Launch Template.

The new instance was registered with the Target Group and could serve the application through the Application Load Balancer.

Result: Successful

---

## 8. Implementation Result

The EC2 Auto Scaling implementation was successfully completed.

The project now uses:

- Application Load Balancer
- Target Group
- Auto Scaling Group
- EC2 instances
- Nginx
- Web Application
- Launch Template
- User Data
- Health Checks

The implementation demonstrates automated EC2 instance provisioning, application initialization using User Data, load balancing, health monitoring, and Auto Scaling.

---

## 9. Key Concepts Learned

- EC2 Launch Templates
- Auto Scaling Groups
- Minimum capacity
- Desired capacity
- Maximum capacity
- Scaling concepts
- EC2 health checks
- Elastic Load Balancing health checks
- User Data
- Application Load Balancer integration
- Target Groups
- Automatic EC2 instance provisioning
- Load balancing
- High availability concepts

---

## 10. Project Architecture Summary

The final architecture for this phase is:

Internet -> Application Load Balancer -> Target Group -> Auto Scaling Group -> EC2 Instances -> Nginx -> Web Application

The Application Load Balancer provides traffic distribution, while the Auto Scaling Group manages the number of EC2 instances.

This architecture improves application availability and provides automated instance provisioning and scaling.

---

## 11. Project Status

EC2 Auto Scaling implementation completed successfully.

The application was tested through the Application Load Balancer, the target health was verified, and scaling was successfully tested by launching an additional EC2 instance.