# AWS Resources

1. Amazon VPC:

A VPC provides an isolated network for our AWS resources.

2. Public Subnet:

The EC2 instance is deployed in a public subnet so that the website can be accessed through the internet.

3. Internet Gateway:

The Internet Gateway connects the VPC to the internet.

4. Route Table:

The public route table contains a route to the Internet Gateway.

```text
0.0.0.0/0 → Internet Gateway

5. Amazon EC2:

The EC2 instance hosts the web application.

Instance name: new-vm
Instance type: t3.micro
Operating system: Amazon Linux

6. Security Group:

The Security Group controls inbound and outbound traffic to the EC2 instance.

SSH: Port 22
HTTP: Port 80

7. Nginx:

Nginx is the web server used to serve the custom HTML webpage.

8. AWS IAM:

IAM is used to manage permissions and access to AWS resources.

9. Project Result:

The custom website was successfully deployed on EC2 and accessed through the public IP address.
