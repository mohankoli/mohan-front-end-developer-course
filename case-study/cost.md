# Hybrid Search Architecture – Cost Analysis

## Scale Assumptions

- Total Documents: **25 Million**
- Total Users: **1 Million**
- Daily Active Users (25%): **250,000**
- Avg Searches per User: **5 per day**
- Total Searches per Day: **1.25 Million**
- Keyword Search: **80%**
- Semantic (Vector) Search: **20%**

---

# One-Time Cost

| Item | Estimated Cost |
|------|----------------|
| OpenAI Embeddings (25M documents) | ~$500,000 |

> One-time indexing cost for generating embeddings.

---

# Recurring Infrastructure Cost

## Monthly & Yearly Estimate

| Component | Purpose | Monthly Cost | Yearly Cost |
|------------|----------|--------------|--------------|
| OpenAI Query Embeddings | 20% semantic queries | $7,500 | $90,000 |
| DynamoDB | Source of Truth (documents) | $5,000 | $60,000 |
| PostgreSQL + pgvector (Primary + 1 Replica) | Vector search | $6,000 | $72,000 |
| OpenSearch Cluster | Keyword search (80%) | $8,000 | $96,000 |
| **Total Recurring Cost** |  | **~$26,500** | **~$318,000** |

---

# Architecture Overview

## Data Layer
- DynamoDB stores original medical documents.
- Supports versioning and metadata storage.

## Search Layer
- OpenSearch handles 80% of queries (keyword-based).
- Horizontally scalable using shards and additional data nodes.

## Vector Layer
- PostgreSQL with pgvector extension.
- 1 Primary node (writes).
- 1 Read Replica (vector queries).
- Scale by adding read replicas.

## AI Layer
- OpenAI Embeddings:
  - One-time document indexing.
  - Per-query embedding for semantic search.

---

# Interview Summary

For 25M documents and 1M users (25% daily active):

- One-time embedding cost ≈ **$500K**
- Recurring yearly infrastructure cost ≈ **$318K**
- Hybrid architecture reduces AI cost by limiting vector search to 20% of queries.
