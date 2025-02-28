EmployeeDir-AWS

A hands-on AWS project deploying an employee directory web application with high availability and networking exploration.

Overview:

This project demonstrates core AWS concepts by building a simple web app:
- VPC: Custom network with subnets across two AZs.
- EC2: Dual web servers hosting an employee directory.
- Security: Network ACL for traffic control.
- High Availability: Multi-AZ resilience.
- Networking: Virtual Private Gateway and Direct Connect exploration.

Built and deleted within AWS Free Tier to ensure no costs or live resources remain.

Architecture

- VPC: 10.0.0.0/16 (us-east-1)

Subnets:

- Public: `10.0.1.0/24` (AZ1), `10.0.3.0/24` (AZ2)
- Private: `10.0.2.0/24` (AZ1), `10.0.4.0/24` (AZ2)
- EC2: Two `t2.micro` instances in public subnets.
- NACL: Secured `Public-AZ1`.
- VPG: Attached for hybrid networking demo.

Steps:

1. [VPC Setup](./setup/vpc-setup.md)
2. [EC2 Web Server](./setup/ec2-setup.md)
3. [Network ACL](./setup/nacl-setup.md)
4. [High Availability](./setup/ha-setup.md)
5. [Networking Peek](./setup/networking-peek.md)

Screenshots:

See `screenshots/` for visuals (sensitive data blurred).

Cleanup:

All resources (VPC, EC2s, NACLs, VPG) terminated post-demo for security and cost control.

Tools:

- AWS Console, SSH (Windows), Git/GitHub

## License
MIT License—free to use or adapt!