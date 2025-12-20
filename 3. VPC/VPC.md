# AWS VPC (Virtual Private Cloud) 

A **VPC (Virtual Private Cloud)** is a **private network** in AWS where you can launch AWS resources like **EC2, RDS, Load Balancers**, etc.

Think of VPC as your **own data center in the cloud**, fully controlled by you.

---

## Why do we need VPC?

AWS is a shared cloud, but:

* We don’t want everyone to access our servers
* We want **network-level security**
* We want control over **IP range, routing, and traffic**

VPC gives:

* Isolation
* Security
* Full network control

---

## VPC Components

### 1. CIDR Block

CIDR defines the **IP address range** of the VPC.

Example:

```
10.0.0.0/16
```

This means:

* Total IPs ≈ 65,536
* Private IP range

---

### 2. Subnet

A **subnet** is a smaller network inside a VPC.

Types of Subnets:

* **Public Subnet** → Has internet access
* **Private Subnet** → No direct internet access

Example:

```
Public Subnet  : 10.0.1.0/24
Private Subnet : 10.0.2.0/24
```

---

### 3. Internet Gateway (IGW)

* Allows communication between VPC and the Internet
* Required for public subnets

Without IGW → No internet

---

### 4. Route Table

Route table decides **where network traffic goes**.

Example Routes:


| Destination &emsp;&nbsp;|  Target&emsp;&emsp;&emsp;&emsp;&emsp;|          
|-----------------|--------------------|  
| 10.0.0.0/16 &emsp;&nbsp;&nbsp;| local &emsp;&emsp;&emsp;&emsp;&emsp;&nbsp; |  
| 0.0.0.0/0  &emsp;&emsp;&nbsp;  | Internet Gateway   |


---

### 5. NAT Gateway

* Used by **private subnets** to access the internet
* Prevents inbound internet traffic

Why needed?

* App servers need updates
* DB should not be public

---

### 6. Security Group

* Works like a **virtual firewall**
* Controls **inbound and outbound traffic**
* Stateful (return traffic allowed automatically)

Example:

* Allow SSH (22)
* Allow HTTP (80)

---

### 7. Network ACL (NACL)

* Another security layer
* Works at **subnet level**
* Stateless (need both inbound & outbound rules)

---



## Public vs Private Subnet (Quick Comparison)

| Feature &emsp;&emsp;&emsp; | Public Subnet | Private Subnet  |  
| -----------------| ----------------| ---------------- |  
| Internet Access  | Yes &emsp;&emsp;&emsp;&emsp;&nbsp;          | No (via NAT) &nbsp;&nbsp;  |  
| Use Case &emsp;&emsp;&ensp;     | Web servers &nbsp;  | DB, backend  &nbsp;&nbsp;  |  
| IGW Route &emsp;&ensp;&nbsp;     | Yes &emsp;&emsp;&emsp;&nbsp;&nbsp;&nbsp;&nbsp;         | No   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;          |  

---

## Summary

* VPC = private network in AWS
* Subnet divides VPC
* IGW provides internet
* NAT Gateway for private subnet internet access
* Security Group & NACL secure the network

<img width="1024" height="1536" alt="VPC Image" src="https://github.com/user-attachments/assets/73d07134-3e92-4e5e-a819-f282dc2e05fb" />


