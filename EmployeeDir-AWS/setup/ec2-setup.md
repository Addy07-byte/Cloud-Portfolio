Step 2: EC2 Web Server

Overview:

Launched an EC2 instance to host an employee directory webpage.

Instance Details
- Name: `EmployeeDir-Web`
- Type: `t2.micro` (Free Tier)
- AMI: Amazon Linux 2
- Subnet: `Public-AZ1` (10.0.1.0/24, us-east-1a)
- Public IP: Enabled 

Setup:

1. Launched via AWS Console.
2. Created key pair `EmployeeDir-Key` (stored locally, not shared).
3. SSH’d in from Windows:
   ```cmd
   ssh -i "C:\Desktop\AWS Cloud\EmployeeDir-Key.pem" ec2-user@<public-ip>

Insatlled Apache:

sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd

Added /var/www/html/index.html:

<!DOCTYPE html>
<html>
<head>
    <title>Employee Directory</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        h1 { color: #333; }
        table { border-collapse: collapse; width: 50%; }
        th, td { border: 1px solid #ddd; padding: 8px; text-align: left; }
        th { background-color: #f2f2f2; }
    </style>
</head>
<body>
    <h1>Employee Directory</h1>
    <table>
        <tr><th>Name</th><th>Role</th></tr>
        <tr><td>Alice Smith</td><td>Developer</td></tr>
        <tr><td>Bob Jones</td><td>Ops Engineer</td></tr>
        <tr><td>Clara Lee</td><td>Manager</td></tr>
    </table>
</body>
</html>

Security Group:

Name: Web-SG
Inbound: SSH (22, my IP), HTTP (80, 0.0.0.0/0)
Outbound: All traffic

Verification:

Visited http://<public-ip>—displayed employee table.

Troubleshooting

Fixed SSH permissions on Windows:
	
icacls "C:\Desktop\AWS Cloud\EmployeeDir-Key.pem" /inheritance:r
icacls "C:\Desktop\AWS Cloud\EmployeeDir-Key.pem" /grant:r "%username%:F"

Screenshots:

Webpage: ../screenshots/webpage-az1.png




















