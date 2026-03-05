# System Design Interview Cheat Sheet (Back-of-the-Envelope Calculations)

This guide covers the most common calculations used in system design
interviews such as: - Estimating number of users - QPS (Queries Per
Second) - Read vs Write traffic - Storage estimation - Bandwidth
estimation

------------------------------------------------------------------------

# 1. Key Assumptions (Used in Interviews)

Typical assumptions used by engineers:

  Metric             Typical Assumption
  ------------------ --------------------
  Payload size       1 KB
  Seconds per day    86,400
  Seconds per year   31,536,000
  1 KB               1024 bytes
  1 GB               1024 MB
  1 TB               1024 GB

These assumptions help perform fast mental calculations.

------------------------------------------------------------------------

# 2. User Traffic Estimation

Example:

Total users = 100 Million\
Daily active users (DAU) = 10%

DAU = 10 Million

If each user performs 20 actions per day:

Total requests/day

10M × 20 = 200M requests/day

------------------------------------------------------------------------

# 3. QPS (Queries Per Second)

Formula:

QPS = Total requests per day / Seconds per day

Example:

200M / 86,400 ≈ 2315 QPS

If read/write ratio = 80/20

Read QPS = 1850\
Write QPS = 465

------------------------------------------------------------------------

# 4. Storage Calculation

Formula:

Storage = Number of records × Size per record

Example:

Notifications per day = 300M\
Notification size = 1 KB

Daily storage:

300M × 1 KB = 300 GB/day

Yearly storage:

300 GB × 365 ≈ 109.5 TB

------------------------------------------------------------------------

# 5. Bandwidth Calculation

Formula:

Bandwidth = QPS × Payload size

Example:

3000 requests/sec × 1 KB

≈ 3 MB/sec

Per hour:

3 MB × 3600 = 10.8 GB/hour

Per day:

10.8 GB × 24 = 259 GB/day

------------------------------------------------------------------------

# 6. Scaling Storage with Replication

Most production systems use replication factor = 3

Example:

100 TB/year data

Total storage needed:

100 TB × 3 = 300 TB

------------------------------------------------------------------------

# 7. Common Back-of-the-Envelope Problems

Typical interview questions:

-   Design Notification System
-   Design URL Shortener
-   Design Twitter / X
-   Design WhatsApp
-   Design Instagram Feed
-   Design YouTube
-   Design Search System
-   Design Chat System
-   Design Rate Limiter
-   Design Distributed Cache

------------------------------------------------------------------------

# 8. Fast Mental Math Tricks

1 Billion = 1000 Million

1 Million = 10\^6\
1 Billion = 10\^9\
1 Trillion = 10\^12

Examples:

300 Million ≈ 0.3 Billion

110 Billion notifications × 1 KB

≈ 110 TB storage

------------------------------------------------------------------------

# 9. Interview Tip

When exact numbers are unknown, state assumptions clearly:

Example:

"I will assume 1 KB payload per record and calculate approximate
storage."

Interviewers care more about reasoning than exact numbers.

------------------------------------------------------------------------

# 10. Typical Architecture Components

Most scalable systems include:

Client API Gateway Load Balancer Application Servers Cache (Redis)
Message Queue (Kafka) Database (SQL / NoSQL) Search Index
(Elasticsearch) Object Storage (S3) CDN

------------------------------------------------------------------------

# Summary

In system design interviews always estimate:

-   Number of users
-   QPS
-   Read vs Write ratio
-   Storage per day/year
-   Bandwidth
-   Replication cost

These calculations demonstrate strong system design thinking.
