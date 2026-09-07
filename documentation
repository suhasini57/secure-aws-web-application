deployment-steps.md

1. Deployment Steps

   1.1. EC2 Instance:

        An existing EC2 instance named `new-vm` was used for this project.
        
        - Instance type: t3.micro
        - Operating system: Amazon Linux
        - VPC: Existing AWS VPC
        - Subnet: Public subnet
        - Web server: Nginx

    1.2. EC2 Connection: 

          The instance was accessed using EC2 Instance Connect because the original SSH key pair was not available on the current system.
          
          The connected Linux username was:
          
          ```text
          ec2-user

2. Verify Nginx: 
The Nginx service was checked using: sudo systemctl status nginx(The service was active and running).

3. Deploy the Website:
The default Nginx webpage was replaced with a custom HTML webpage.
The website files were placed in: /usr/share/nginx/html/index.html

4. Verify the Website:
The website was tested locally using: curl http://localhost
It was then accessed through the EC2 public IP address.

5. Result:
The custom project webpage was successfully deployed and accessed through the internet.

