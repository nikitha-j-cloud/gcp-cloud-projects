# Cloud Storage & Lifecycle Management Setup

## Objective
Create and configure Cloud Storage buckets with versioning, lifecycle 
policies, and access controls to manage data cost-effectively.

## GCP Services Used
- Cloud Storage
- Cloud IAM
- Google Cloud Console
- Cloud Shell (gsutil)

## What I Did
- Created a multi-regional Cloud Storage bucket with a globally unique name
- Enabled **Object Versioning** to protect against accidental deletions
- Configured **Lifecycle Rules**:
  - Move objects to Nearline storage after 30 days of no access
  - Move objects to Coldline storage after 90 days
  - Delete objects older than 365 days
- Applied **Uniform Bucket-Level Access** (disabled ACLs, enforced IAM only)
- Created IAM bindings to grant read-only access to a specific service account
- Tested uploads, downloads, and permission enforcement using Cloud Shell

## Commands Used
```bash
# Create a bucket
gsutil mb -l ASIA-SOUTH1 gs://nikitha-gcp-demo-bucket

# Enable versioning
gsutil versioning set on gs://nikitha-gcp-demo-bucket

# Upload a file
gsutil cp sample.txt gs://nikitha-gcp-demo-bucket/

# List bucket contents
gsutil ls -l gs://nikitha-gcp-demo-bucket/
```

## Key Learnings
- Difference between Regional, Multi-Regional, Nearline, and Coldline storage classes
- How lifecycle policies help reduce storage costs automatically
- Why Uniform Bucket-Level Access is preferred over per-object ACLs
- How IAM roles (Storage Object Viewer, Storage Admin) control bucket access
