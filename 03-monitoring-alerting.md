# Cloud Monitoring & Alerting Dashboard

## Objective
Set up Cloud Monitoring dashboards and alerting policies to track 
VM health and get notified of performance issues automatically.

## GCP Services Used
- Cloud Monitoring
- Cloud Logging
- Compute Engine
- Cloud Shell

## What I Did
- Enabled **Cloud Monitoring** on an existing GCP project
- Created a custom **Monitoring Dashboard** with the following widgets:
  - CPU Utilization (line chart) for 2 VM instances
  - Disk Read/Write I/O (stacked area chart)
  - Network Ingress/Egress traffic
  - VM Uptime status
- Configured an **Alerting Policy**:
  - Trigger: CPU utilization > 80% for more than 5 minutes
  - Notification channel: Email alert to project owner
- Set up an **Uptime Check** to monitor VM availability every 60 seconds
- Used **Cloud Logging** to:
  - Filter VM serial port (startup) logs
  - Query firewall deny logs using log filter:
  - resource.type="gce_instance"
logName="projects/PROJECT_ID/logs/compute.googleapis.com%2Ffirewall"

## Key Learnings
- How Cloud Monitoring is different from basic GCP Console metrics
- How to use MQL (Monitoring Query Language) for custom metrics
- Importance of alerting before issues become outages
- How Cloud Logging and Monitoring work together for observability
