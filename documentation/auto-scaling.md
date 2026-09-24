# EC2 Auto Scaling Setup

## Objective

EC2 Auto Scaling was implemented with the existing Application Load Balancer to automatically manage EC2 instances and maintain application availability.

The Auto Scaling Group uses the existing Launch Template and Target Group.

---

## Architecture

The application architecture for this phase is:

**Internet → Application Load Balancer → Target Group → Auto Scaling Group → EC2 Instances → Nginx → Web Application**

The Application Load Balancer receives incoming HTTP requests and forwards traffic to healthy EC2 instances.

The Auto Scaling Group manages the EC2 instances and can launch additional instances when required.

### Architecture Flow

**Internet**

↓

**Application Load Balancer**

↓

**Target Group**

↓

**Auto Scaling Group**

↓

**EC2 Instance 1 → Nginx**

**EC2 Instance 2 → Nginx**

↓

**Web Application**

---

## Launch Template

A Launch Template was created to provide the configuration required when the Auto Scaling Group launches new EC2 instances.

### Configuration

| Configuration | Value |
|---|---|
| Operating System | Amazon Linux 2023 |
| Instance Type | t3.micro |
| IAM Instance Profile | Configured |
| Security Group | Existing EC2 security group |
| User Data | Configured |

---

## User Data

User Data was configured in the Launch Template to automatically initialize newly launched EC2 instances.

The configuration performs the following tasks:

- Installs Nginx
- Enables the Nginx service
- Starts the Nginx service
- Creates the web application page

This allows newly launched EC2 instances to automatically become web servers without manual configuration.

---

## Auto Scaling Group

An Auto Scaling Group was created using the configured Launch Template.

### Configuration

| Configuration | Value |
|---|---|
| Auto Scaling Group | aws-web-asg |
| Minimum Capacity | 1 |
| Desired Capacity | 1 |
| Maximum Capacity | 2 |
| Target Group | aws-web-targets |
| EC2 Health Checks | Enabled |
| ELB Health Checks | Enabled |
| Health Check Grace Period | 300 seconds |

---

## Application Load Balancer Integration

The Auto Scaling Group was associated with the existing Target Group.

The Application Load Balancer forwards HTTP requests to healthy EC2 instances registered with the Target Group.

When the Auto Scaling Group launches an additional EC2 instance, the instance is automatically registered with the Target Group.

The ALB can then distribute traffic across the available healthy instances.

---

## Testing

### Test 1: EC2 Instance Launch

The Auto Scaling Group successfully launched an EC2 instance using the configured Launch Template.

The User Data configuration automatically installed and started Nginx and created the application web page.

**Result: Successful**

---

### Test 2: Application Access

The application was successfully accessed through the Application Load Balancer.

Application output:

**Secure AWS Web Application**

**Application deployed using AWS Auto Scaling.**

**Result: Successful**

---

### Test 3: Target Health

The Auto Scaling instance was registered with the Target Group.

The Application Load Balancer health check verified that the Nginx web server was responding successfully.

**Result: Target Healthy**

---

### Test 4: Scaling

The Auto Scaling Group was tested by increasing the desired capacity.

The ASG successfully launched an additional EC2 instance using the configured Launch Template.

The new instance was registered with the Target Group and could serve the application through the Application Load Balancer.

**Result: Successful**

---

## Implementation Result

The EC2 Auto Scaling implementation was successfully completed.

The project now includes:

- Application Load Balancer
- Target Group
- Auto Scaling Group
- Launch Template
- EC2 instances
- Nginx
- User Data
- Health Checks
- Web Application

The implementation demonstrates:

- Automated EC2 instance provisioning
- Application initialization using User Data
- Load balancing
- Health monitoring
- Auto Scaling
- High availability concepts

---

## Key Concepts Learned

- EC2 Launch Templates
- Auto Scaling Groups
- Minimum capacity
- Desired capacity
- Maximum capacity
- Scaling concepts
- EC2 health checks
- Elastic Load Balancing health checks
- User Data
- Target Groups
- Application Load Balancer integration
- Automatic EC2 instance provisioning
- Load balancing
- High availability

---

## Project Status

**EC2 Auto Scaling implementation completed successfully.**

The application was successfully accessed through the Application Load Balancer.

The Target Group health check was verified successfully.

Scaling was tested by increasing the desired capacity and launching an additional EC2 instance.

The new instance was registered with the Target Group and was able to serve the application through the Application Load Balancer.
