# AWS CloudWatch 

Amazon CloudWatch is a monitoring and observability service provided by AWS. It helps you collect, track, analyze, and act on metrics, logs, and events from AWS resources and applications running on AWS or on‑premises.

**visibility**, **alerting**, and **operational insights**.

---

## Core Components

### 1. Metrics

* Time‑ordered numerical data about resources and applications.
* Examples:

  * EC2: CPUUtilization, NetworkIn/Out
  * Lambda: Invocations, Duration, Errors
  * RDS: FreeStorageSpace, DatabaseConnections
* Resolution:

  * Standard: 1 minute
  * High‑resolution: up to 1 second (extra cost)

---

### 2. Logs

* Centralized log storage and analysis.
* Sources:

  * EC2 (via CloudWatch Agent)
  * Lambda (automatic)
  * ECS, EKS, API Gateway, VPC Flow Logs
* Key concepts:

  * Log Group: Collection of log streams
  * Log Stream: Sequence of log events from a single source
* Supports log filtering, searching, and metric extraction

---

### 3. Alarms

* Used to trigger actions based on metrics.
* States:

  * OK
  * ALARM
  * INSUFFICIENT_DATA
* Actions:

  * Send SNS notification
  * Auto Scaling action
  * EC2 stop/terminate/recover

---

### 4. Dashboards

* Custom visualizations of metrics
* Can combine metrics from multiple AWS services
* Useful for real‑time monitoring and operational overview

---

### 5. Events (Amazon EventBridge)

* Respond to state changes in AWS resources
* Examples:

  * EC2 instance state change
  * CodePipeline execution state
* Used for event‑driven automation

---

### 6. CloudWatch Agent

* Installed on EC2 or on‑prem servers
* Collects:

  * System‑level metrics (memory, disk, swap)
  * Custom logs
* Replaces older CloudWatch Logs Agent

---

### 7. Custom Metrics

* Publish your own application metrics using:

  * AWS SDK
  * AWS CLI (`put-metric-data`)
* Useful for business or app‑level KPIs

---

### 8. Log Insights

* Query language for analyzing logs
* Helps in:

  * Debugging issues
  * Finding error patterns
  * Performance analysis
* Example query:

  ```
  fields @timestamp, @message
  | filter @message like /ERROR/
  | sort @timestamp desc
  | limit 20
  ```



