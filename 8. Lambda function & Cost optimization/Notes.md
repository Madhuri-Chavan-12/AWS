# AWS Lambda Functions & Cost Optimization



## 1. What is AWS Lambda?

AWS Lambda is a **serverless compute service** that lets you run code **without provisioning or managing servers**.

You upload your code, define a trigger, and AWS:

* Automatically runs the code
* Scales it
* Handles infrastructure, OS, and runtime management

 Pay **only for execution time**, not for idle servers.

---

## 2. Key Characteristics of Lambda

* **Event-driven**: Executes in response to events
* **Stateless**: No guaranteed state between executions
* **Auto-scaling**: Scales horizontally by default
* **Managed runtime**: AWS manages OS, patching, and scaling

---

## 3. Common Lambda Triggers (Event Sources)

* API Gateway (REST / HTTP APIs)
* Application Load Balancer (ALB)
* S3 (file upload/delete)
* DynamoDB Streams
* Kinesis Streams
* EventBridge / CloudWatch Events
* SQS
* SNS

---

## 4. Lambda Execution Model

### 4.1 Cold Start

* First invocation creates a **new execution environment**
* Includes:

  * Container startup
  * Runtime initialization
  * Code initialization
* Slower than warm starts

### 4.2 Warm Start

* Execution environment is reused
* Much faster

**Cold starts increase latency and cost** if not managed properly.

---

## 5. Lambda Pricing Model

Lambda cost is based on **two main factors**:

### 5.1 Number of Requests

* Charged per invocation
* First **1 million requests/month are free**

### 5.2 Execution Duration

* Measured in **milliseconds**
* Based on:

  * Memory allocated (MB)
  * Execution time

 Cost = Requests + (Memory × Duration)

---

## 6. Memory & CPU Relationship

* Lambda allocates **CPU proportional to memory**
* More memory = more CPU = faster execution

Sometimes **higher memory reduces total cost** because execution finishes faster.

---


# COST OPTIMIZATION 



## 1. Memory Optimization

### Problem:

* Over-allocating memory wastes money

### Solution:

* Benchmark function with different memory sizes
* Use AWS Lambda Power Tuning tool

> Measure **cost vs execution time**, not just speed.

---

## 2. Reduce Execution Time

Ways to reduce runtime:

* Optimize code logic
* Avoid unnecessary loops
* Use efficient libraries
* Reuse connections (DB, HTTP clients)

Shorter runtime = lower cost.

---

## 3. Use Appropriate Timeouts

* Default timeout = 3 seconds
* Max timeout = 15 minutes

Set timeout **just above expected runtime**.

Long timeouts hide bugs and increase cost.

