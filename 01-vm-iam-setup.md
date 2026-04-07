# Secure VM Deployment & IAM Configuration

## Objective
Deploy a secure Linux VM on Google Cloud and implement Identity & Access Management (IAM) using the principle of least privilege.

## GCP Services Used
- Compute Engine
- Cloud IAM
- Cloud Shell
- VPC Firewall Rules
- service account

## Architecture Overview
- A Linux VM is deployed in a VPC network
- A custom service account is attached to the VM
- A custom IAM role with minimal permissions is created
- Firewall rules restrict access to only required ports (SSH, HTTP)

## Implementation steps

## VM deployment
- Created a Linux VM (e2-micro) in Compute Engine
- Region: asia-south1 (Mumbai)
- Enabled HTTP traffic
- Used SSH for secure access

 ## Service Account creation
 - Created a dedicated service account for VM access
 - Avoided using default service account for security

## Custom IAM Role
- Created a custom role with minimal permissions:
compute.instances.get
compute.instances.list
- Assigned role to service account

## Firewall Configuration
- Allowed only required ports: SSH (20), HTTP (80)
- Denied all unnecessary inbound traffic

## Connectivity Testing
- Verified SSH access
- Tested HTTP access via external IP

## Security Best Practices Implemented
- Principle of Least Privilege
- Use of custom IAM roles instead of broad predefined roles
- Restricted firewall access
- Avoided default service account usage

## Key Learnings
- Difference between predefined vs custom IAM roles
- Role of service accounts in secure resource access
- Importance of firewall rules in cloud security
- Hands-on understanding of VM security hardening
