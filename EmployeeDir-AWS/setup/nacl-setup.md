Step 3: Network ACL

Overview:

Secured `Public-AZ1` subnet with a custom Network ACL.

NACL Details
- Name: `Custom-NACL`
- Subnet: `Public-AZ1` (10.0.1.0/24, us-east-1a)

Rules

Inbound:
- 100: Allow TCP 80 (HTTP) from 0.0.0.0/0
- 110: Allow TCP 22 (SSH) from <my-ip>/32
- 900: Deny all traffic

Outbound:
- 100: Allow TCP 1025-65535 (ephemeral) to 0.0.0.0/0
- 900: Deny all traffic

Setup:

- Created and associated via AWS Console.
- Configured stateless rules to allow web and SSH traffic.

Testing:
- SSH’d into `EmployeeDir-Web`—successful.
- Loaded `http://<public-ip>`—employee directory displayed.

Screenshots:

- NACL Rules: `../screenshots/nacl-rules.png`
- Subnet Association: `../screenshots/nacl-subnet-association.png`

Cleanup:

Deleted with VPC at end.