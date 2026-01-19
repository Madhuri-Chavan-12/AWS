# AWS CloudFront

Amazon CloudFront is a **Content Delivery Network (CDN)** service by AWS that delivers content (web pages, images, videos, APIs) to users with **low latency and high transfer speeds** using a global network of **Edge Locations**.

- CloudFront caches your content closer to users so your application loads faster.

---

## Key Concepts

### 1. Edge Locations

* Data centers where CloudFront caches content
* Requests are served from the nearest edge location
* Reduces latency significantly

### 2. Origin

The source of your content. Common origins:

* Amazon S3 (static websites, files)
* Application Load Balancer
* EC2 instance
* Any HTTP server (custom origin)

### 3. Distribution

* A CloudFront configuration that defines how content is delivered
* Two types:

  * **Web distribution** (websites, APIs)
  * **RTMP** (legacy – mostly deprecated)

### 4. Cache Behavior

Defines how CloudFront handles requests:

* Path pattern (e.g. `/images/*`)
* Allowed HTTP methods (GET, POST, etc.)
* Cache TTL (Time To Live)
* Forwarding headers, cookies, query strings

### 5. TTL (Time To Live)

Controls how long objects stay cached at edge locations

* Min TTL
* Default TTL
* Max TTL

Lower TTL = fresher content, higher origin load
Higher TTL = better performance, stale risk

---

## How CloudFront Works (Flow)

1. User requests a file (image, HTML, API)
2. Request goes to nearest Edge Location
3. If cached → served immediately (**Cache Hit**)
4. If not cached → CloudFront fetches from origin (**Cache Miss**)
5. Content is cached at edge and returned to user

---

## CloudFront with S3


Benefits:

* Better security
* Faster delivery
* Lower cost than serving directly from S3

---

## Security Features

### HTTPS / SSL

* Supports HTTPS by default
* Use AWS Certificate Manager (ACM) for free SSL certificates

### Signed URLs & Signed Cookies

* Restrict access to private content
* Used for paid or protected content

### AWS WAF Integration

* Protect against:

  * SQL Injection
  * XSS
  * DDoS attacks

---

## Performance Features

### Compression

* Automatic Gzip / Brotli compression
* Reduces file size and load time

### HTTP/2 and HTTP/3

* Faster connection setup
* Better performance on modern browsers

### Lambda@Edge

* Run code at edge locations
* Use cases:

  * Authentication
  * URL rewrites
  * Header manipulation

---


## Common Use Cases

* Static website hosting
* API acceleration
* Video streaming
* Software downloads
* Global applications

---


## Summary

CloudFront is critical for building **fast, secure, and globally distributed applications** on AWS. It should be used whenever content needs to be delivered to users across regions with minimal latency.


