Step 1: VPC Setup

Overview:
Set up a VPC with public and private subnets across two AZs for a robust network.

VPC:

- Name: `EmployeeDir-VPC`
- CIDR: `10.0.0.0/16` (65,536 IPs)
- Region: `us-east-1`

Subnets:

- Public-AZ1: `10.0.1.0/24` (us-east-1a)
- Private-AZ1: `10.0.2.0/24` (us-east-1a)
- Public-AZ2: `10.0.3.0/24` (us-east-1b)
- Private-AZ2: `10.0.4.0/24` (us-east-1b)

Internet Gateway:

- Name: `EmployeeDir-IGW`
- Attached to `EmployeeDir-VPC` for public subnet internet access.

Route Tables:

- Main-RT: Private subnets, local traffic (`10.0.0.0/16 → local`).
- Public-RT: Public subnets, internet access (`0.0.0.0/0 → EmployeeDir-IGW`).

Process:

- Created via AWS Console in 45 minutes.
- Verified subnet associations and routing.

Screenshots:

- VPC List: `../screenshots/vpc.png`
- Subnets: `../screenshots/subnets.png`
- Route Tables: `../screenshots/routes.png`

Cleanup:

Deleted with VPC at project end.