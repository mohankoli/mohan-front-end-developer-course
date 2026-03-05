# System Design Back-of-Envelope Cheat Sheet

## 1. Constants (Memorize)

```
Seconds per minute = 60
Seconds per hour = 3600
Seconds per day = 86,400
Seconds per year = 31,536,000

1 KB = 1024 bytes
1 MB = 1024 KB
1 GB = 1024 MB
1 TB = 1024 GB

1 Million = 10^6
1 Billion = 10^9
1 Trillion = 10^12
```

---

# 2. User Traffic Estimation

```
DAU = Total Users × Active %

Requests per day
= DAU × actions per user
```

Example

```
Users = 100M
Active = 10%

DAU = 10M

Requests per day
= 10M × 20
= 200M requests/day
```

---

# 3. QPS Calculation

```
QPS = Total requests per day / 86,400
```

Example

```
200M / 86,400 ≈ 2315 QPS
```

Read / Write split

```
Read QPS = QPS × read %
Write QPS = QPS × write %
```

Example

```
80% read
20% write

Read = 1850 QPS
Write = 465 QPS
```

---

# 4. Storage Estimation

```
Storage = records × size per record
```

Example

```
300M notifications/day
1 KB each

Daily storage
= 300 GB

Yearly storage
= 300 × 365
≈ 110 TB
```

---

# 5. Bandwidth Estimation

```
Bandwidth = QPS × payload size
```

Example

```
3000 QPS
1 KB payload

≈ 3 MB/sec
```

Conversions

```
Per hour
= MB/sec × 3600

Per day
= Hour × 24
```

Example

```
3 MB/sec

= 10.8 GB/hour
= 259 GB/day
```

---

# 6. Storage with Replication

```
Total Storage = Raw Data × Replication Factor
```

Example

```
100 TB data
Replication = 3

Total storage = 300 TB
```

---

# 7. CPU Estimation

```
CPU cores = QPS × request processing time
```

Example

```
QPS = 3000
Processing time = 20ms = 0.02s

3000 × 0.02
= 60 CPU cores
```

Servers needed

```
Servers = total cores / cores per server
```

Example

```
Server = 8 cores

60 / 8 ≈ 8 servers
```

---

# 8. Redis Memory Calculation

```
Memory = number of keys × size per key
```

Example

```
Users = 10M
Cache per user = 500 bytes

10M × 500B
= 5 GB
```

Add overhead

```
≈ +30%
≈ 7 GB Redis memory
```

---

# 9. Quick Mental Math

```
1B records × 1KB ≈ 1TB

100M × 1KB ≈ 100GB

10M × 1KB ≈ 10GB
```

Example

```
110B notifications
1KB each

≈ 110 TB
```

---

# 10. Typical System Components

```
Client
API Gateway
Load Balancer
Application Servers
Cache (Redis)
Queue (Kafka)
Database
Object Storage
CDN
```

---

# What Interviewers Expect

Always estimate:

```
Users
DAU
QPS
Read vs Write
Storage
Bandwidth
Replication
CPU / Servers
Cache size
```
