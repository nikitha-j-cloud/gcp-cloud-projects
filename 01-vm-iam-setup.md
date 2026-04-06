# Secure VM Deployment & IAM Configuration

## Objective
Deploy a Linux VM on Compute Engine and configure IAM with least-privilege access.

## GCP Services Used
- Compute Engine
- Cloud IAM
- Cloud Shell
- VPC Firewall Rules

## What I Did
- Provisioned a Linux VM (e2-micro) with custom startup script
- Created a custom IAM role with only required permissions
- Assigned the role to a service account
- Configured firewall rules to allow only SSH (port 22) and HTTP (port 80)
- Tested connectivity using Cloud Shell

## Key Learnings
- Difference between predefined and custom IAM roles
- How service accounts differ from user accounts
- Principle of least privilege in GCP
