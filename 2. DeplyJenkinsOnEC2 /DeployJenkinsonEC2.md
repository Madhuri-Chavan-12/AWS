# AWS EC2 Notes 

Amazon Elastic Compute Cloud (EC2) is a service that provides **resizable virtual servers** in the cloud. You can run applications without managing physical hardware.

---

## Key EC2 Concepts

### 1. AMI (Amazon Machine Image)

* Template used to launch EC2 instances
* Includes:

  * OS (Amazon Linux, Ubuntu, RHEL, Windows)
  * Pre-installed software
* Types:

  * AWS provided
  * Marketplace AMIs
  * Custom AMIs

---

### 2. Instance Types

Defines **CPU, memory, storage, and networking capacity**.

| Family  | Use Case                      |  
| ------- | ----------------------------- |  
| t2 / t3 | Low-cost, burstable workloads |  
| m5      | General purpose               |  
| c5      | Compute intensive             |  
| r5      | Memory intensive              |



---

### 3. Key Pair

* Used for **secure SSH access**
* Public key → stored in AWS
* Private key (.pem) → stored by user

```bash
ssh -i key.pem ubuntu@<public-ip>
```


---

### 4. Security Group

Acts as a **virtual firewall**.

* Stateful
* Allows only **allowed inbound & outbound traffic**

Common Rules:

* SSH → Port 22
* HTTP → Port 80
* HTTPS → Port 443

---

### 5. Storage (EBS)

Elastic Block Store provides **persistent storage**.

Types:

* gp3 / gp2 (General purpose)
* io1 / io2 (High IOPS)
* st1 (Throughput optimized)

Features:

* Data persists even if instance stops
* Can create snapshots

---

### 6. Instance Lifecycle

| State      | Meaning                                     |  
| ---------- | ------------------------------------------- |  
| Running    | Instance is active                          |  
| Stopped    | Instance is off (EBS retained)              |  
| Terminated | Instance deleted (EBS lost unless snapshot) |  

---

## EC2 Networking

### Public IP vs Private IP

* **Public IP** → Internet access
* **Private IP** → Internal AWS network

### Elastic IP (EIP)

* Static public IPv4 address
* Use when IP must not change

---

## Connecting to EC2


```bash
ssh -i key.pem ec2-user@<public-ip>
```

---

## Monitoring & Logs

### CloudWatch

* CPU Utilization
* Disk, Network metrics

### EC2 Status Checks

* System status
* Instance status

---

## IAM with EC2

* Assign role to EC2
* EC2 can access AWS services securely



