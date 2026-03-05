# System Design Quick Sheet

## Assumption
Users = 100M  
Active Users = 10M  

Avg requests/user = 20  

Requests/day  
= 10M × 20  
= 200M

---

## QPS
QPS = Requests/day / 86400

200M / 86400 ≈ 2315 QPS

Read 80%  ≈ 1800  
Write 20% ≈ 500

---

## Storage
300M notifications/day  
1 KB each

Daily = 300 GB  

Yearly  
300 × 365 ≈ 110 TB  

Replication ×3  
≈ 330 TB

---

## Bandwidth
Bandwidth = QPS × payload

3000 QPS × 1 KB  
≈ 3 MB/sec

Per hour  
≈ 10.8 GB

Per day  
≈ 260 GB

---

## CPU
CPU cores = QPS × request time

3000 × 0.02s  
= 60 cores

Servers (8 cores)  
≈ 8 servers

---

## Redis Memory
Users = 10M  
Cache/user = 500B  

10M × 500B  
= 5 GB  

With overhead ≈ 7 GB
