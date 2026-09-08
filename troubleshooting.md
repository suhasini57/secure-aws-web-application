# Troubleshooting

1. Old SSH Key Pair Unavailable:

Problem:
The original `.pem` key pair was not available on the current system, so SSH access through Git Bash was difficult.

Solution:
Used EC2 Instance Connect to access the running EC2 instance through the AWS Console.

2. Nginx Verification:

Problem:
The website needed to be checked before making changes.

Solution:
Verified the Nginx service using:

```bash
sudo systemctl status nginx
The service was active and running.

3. Default Nginx Page:

Problem:
The default Nginx welcome page was displayed.

Solution:
Replaced the default HTML file with a custom project webpage.

File location:
/usr/share/nginx/html/index.html

4. Website Verification:

Solution:
Tested the website locally using:

curl http://localhost
Then accessed it through the EC2 public IP address.

5. Result: The custom AWS project webpage was successfully deployed and accessed through the internet.
