# VPC Network & Firewall Configuration

## Objective
Design and configure a custom-mode VPC network with multiple subnets, 
firewall rules, and test internal connectivity between VM instances.

## GCP Services Used
- VPC Network
- Compute Engine
- Cloud Firewall
- Cloud Shell

## What I Did
- Created a **Custom-Mode VPC** (instead of auto-mode) for full control 
  over IP ranges
- Added **two subnets** in different regions:
  - `subnet-india` — asia-south1 (Mumbai) — CIDR: 10.0.1.0/24
  - `subnet-us` — us-central1 — CIDR: 10.0.2.0/24
- Configured **Firewall Rules**:
  - Allow SSH (port 22) from a specific IP range only
  - Allow HTTP (port 80) and HTTPS (port 443) from all sources (0.0.0.0/0)
  - Deny all other ingress traffic (default deny)
  - Applied rules using **network tags** for targeted VM control
- Deployed **two VM instances** — one in each subnet
- Tested **internal connectivity** between the VMs using `ping` and `curl`
- Assigned **static external IPs** to one VM and tested SSH access

## Commands Used
```bash
# Create custom VPC
gcloud compute networks create nikitha-vpc --subnet-mode=custom

# Create subnet
gcloud compute networks subnets create subnet-india \
  --network=nikitha-vpc \
  --region=asia-south1 \
  --range=10.0.1.0/24

# Create firewall rule
gcloud compute firewall-rules create allow-ssh \
  --network=nikitha-vpc \
  --allow=tcp:22 \
  --source-ranges=0.0.0.0/0 \
  --target-tags=ssh-allowed

# Create VM with network tag
gcloud compute instances create vm-india \
  --zone=asia-south1-a \
  --machine-type=e2-micro \
  --subnet=subnet-india \
  --tags=ssh-allowed
```

## Key Learnings
- Difference between Auto-mode and Custom-mode VPCs
- How subnets are regional (not zonal) in GCP
- How firewall rules with network tags give granular control per VM
- How internal IPs allow communication within a VPC without internet access
