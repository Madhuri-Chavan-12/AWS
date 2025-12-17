
# What is IAM?

IAM (Identity and Access Management) is an AWS service that helps you control:

- Who can access AWS

- What they are allowed to do

- Which AWS resources they can use

- IAM = login + permissions (In short)

## Main IAM Components

### 1. IAM User

- Represents a real person or application

- Can login to:

     AWS Console (username + password)

    AWS CLI / API (access key + secret key)


### 2. IAM Group

- Group = collection of users

- Permissions are attached to the group


### 3. IAM Role (Most Important)

- Used by AWS services, not humans

- No password or access key

- Uses temporary credentials

- Used by:

     EC2

     Lambda

    ECS / EKS

     Jenkins / Ansible / Terraform

### 4. IAM Policy

- Policy defines what is allowed or denied.

- Written in JSON.

- Simple example:

```
{
  "Effect": "Allow",
  "Action": "s3:GetObject",
  "Resource": "arn:aws:s3:::my-bucket/*"
}
```
**Types of IAM Policies:**

#### 1. AWS Managed Policy

#### 2. Customer Managed Policy

#### 3. Inline Policy

- Least Privilege Principle

- Give only required permissions.


### Summary

- IAM controls access in AWS

- Users = people

- Roles = services

- Policies = permissions

- Security depends on least privilege
