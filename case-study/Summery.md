
---

## Core Search Flow (How to Explain)

### 1️⃣ CDN
- Serves static UI assets
- Caches safe, frequently requested medical summaries
- Reduces latency for doctors

---

### 2️⃣ API Gateway (Search Entry Point)
- Handles authentication
- Identifies tenant (hospital / institution)
- Applies rate limiting
- Protects backend services

---

### 3️⃣ Search Load Balancer (NGINX / Caddy)
- Dedicated load balancer for search services
- Distributes traffic across multiple search orchestrators
- Performs health checks
- Enables horizontal scaling

**Interview line:**
> “Search traffic is isolated behind its own load balancer to ensure reliability under peak medical usage.”

---

### 4️⃣ Search Orchestrator (Node.js)
This is the **brain of the system**.

Responsibilities:
- Parse search queries
- Decide cheap path vs AI path
- Apply tenant and specialty filters
- Coordinate caching, search, ranking, and AI

---

### 5️⃣ Bloom Filter (Fast Elimination)
- Quickly checks if a keyword or query has been seen before
- Avoids unnecessary search calls
- Improves performance at scale

---

### 6️⃣ Redis Cache
- Stores frequent queries and summaries
- Institution-specific caching
- Cache hit → no AI call

**Result:**
- 60–70% reduction in LLM cost
- Sub-200ms responses for hot queries

---

### 7️⃣ Keyword Search (Traditional Search)
- Powered by OpenSearch
- Inverted index
- Filters, facets, metadata
- Handles most searches efficiently

---

### 8️⃣ Vector Search (Semantic Search)
- Uses document embeddings
- Understands intent and meaning
- Used for complex, natural-language queries

---

### 9️⃣ Hybrid Ranking
- Combines:
  - Keyword relevance
  - Semantic similarity
  - Medical metadata
- Produces the most relevant context

---

### 🔟 LLM Summarization Model
- Summarizes retrieved content
- Never searches data directly
- Never generates free-text answers

**Safety rules:**
- Strict prompts
- Token limits
- Source references mandatory

**Interview line:**
> “Search finds the truth, the LLM only explains it.”

---

### 1️⃣1️⃣ Response Formatter
- Formats output
- Adds citations
- Confidence indicators
- Structured response for UI

---

## Analytics & Historical Learning (NEW – Very Important)

### 🔍 Search Analytics Pipeline
