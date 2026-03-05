# System Design Quick Sheet — Document Search / RAG System

## Assumptions
- Users = 100M
- Active Users = 10M
- Avg searches/user = 10
- PDF uploads/day = 1M
- Avg PDF size = 5 MB
- Chunks per PDF = 100
- Embedding size = 1 KB

---

## Requests / Day

Search Requests  
3M users × 10 queries  
= **30M searches/day**

Upload Requests  
= **1M uploads/day**

Total Requests  
= **31M requests/day**

---

## QPS

QPS = Requests / 86400

31M / 86400 ≈ **360 QPS**

---

## Traffic Split

Read (Search) ≈ **350 QPS**

Write (Upload + Index) ≈ **10 QPS**

---

## Storage

### Raw PDF Storage
1M PDFs × 5 MB  
= **5 TB/day**

Yearly  
5 × 365  
≈ **1.8 PB**

Replication ×3  
≈ **5.4 PB**

---

### Vector DB Storage

Chunks/day  
1M × 100  
= **100M chunks**

Embedding size  
= **1 KB**

Daily  
100M × 1 KB  
= **100 GB/day**

Yearly  
100 × 365  
≈ **36 TB**

Replication ×3  
≈ **108 TB**

---

## Bandwidth

Search response ≈ **5 KB**

350 QPS × 5 KB  
≈ **1.7 MB/sec**

Per hour  
≈ **6 GB**

Per day  
≈ **150 GB**

Upload bandwidth

10 QPS × 5 MB  
≈ **50 MB/sec**

---

## CPU

CPU cores = QPS × request time

360 × 0.05s  
≈ **18 cores**

Servers (8 cores)

≈ **3 servers**

Safe estimate  
≈ **5 servers**

---

## Worker Compute (Embeddings)

Chunks/day  
= **100M**

Embedding time  
= **50 ms**

Compute required

100M × 0.05 sec  
= **5M seconds**

Workers required

5M / 86400  
≈ **58 workers**

---

## Redis Cache

Active Users = **10M**

Cache/user = **1 KB**

10M × 1 KB  
= **10 GB**

With overhead  
≈ **15 GB**

<img width="1472" height="811" alt="image" src="https://github.com/user-attachments/assets/c85a39f1-1850-42c1-8d99-6c1a0f94b418" />
