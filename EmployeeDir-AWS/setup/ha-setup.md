Step 4: High Availability

Overview:

Added a second EC2 in `Public-AZ2` for high availability across two AZs.

Instance Details:

- Name: `EmployeeDir-Web2`
- Type: `t2.micro`
- AMI: Amazon Linux 2
- Subnet: `Public-AZ2` (10.0.3.0/24, us-east-1b)
- Public IP: Enabled (redacted)

Setup:

1. Launched via AWS Console.
2. Reused `EmployeeDir-Key` and `Web-SG`.
3. Installed Apache (same as Step 2).
4. Copied `index.html` to `/var/www/html/` (identical to `EmployeeDir-Web`).

Verification:

- Tested: `http://<public-ip1>` (AZ1) and `http://<public-ip2>` (AZ2)—both served webpage.
- HA: Two AZs ensure uptime if one fails (no load balancer in demo).

Security Note:

- `Public-AZ1`: Secured with `Custom-NACL`.
- `Public-AZ2`: Default NACL (allows all)—demo-only, production would secure similarly.

Screenshots:

- Instances List: `../screenshots/ec2-instances.png`
- Webpage (AZ2): `../screenshots/webpage-az2.png`

Cleanup:

Terminated with all resources at end.

