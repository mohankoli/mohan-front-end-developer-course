# AI-Powered Search Case Study  
*(ServiceNow – Staff / Manager Interview Ready)*

> “Let me walk you through a real AI-powered search system I led end-to-end.”

---

## 1. Business Context

### Company & Domain
- Company: ** WK LS**
- Domain: **Medical publishing**
- Users: Medical institutions, doctors, students
- Content: Standard medical procedures and treatment protocols
- Data size: **25+ million documents**
- Time range: **1970 to present**
- Journey: Physical books → fully digitized content

### Why This Was Critical
- Used during **real medical treatments**
- Doctors rely on it for decision-making
- **Accuracy, relevance, and trust are mandatory**

**Interview signal:**  
> This was a high-impact, mission-critical healthcare system.

---

## 2. Problem With Traditional Search

Before 2023, we used **keyword-based search**.

### Issues
- Exact keyword match only
- Doctors had to guess correct medical terms
- Very long documents
- No summaries
- Poor results for natural language questions

### Example
**Query:**  
> “What is the protocol for post-operative sepsis in diabetic patients?”

**Result:**
- Hundreds of documents
- No clear answer
- Time wasted during treatment

---

## 3. Goal of AI-Powered Search

We wanted to build a system that supports:

- Natural language search
- Semantic understanding
- Clear summaries
- High relevance
- Low response time
- Cost control at large scale

### Constraints
- 25M+ documents
- Multi-tenant system
- Healthcare compliance (HIPAA-sensitive)
- LLM usage must be cost-predictable

---

## 4. High-Level Design Approach

> “We designed a **hybrid AI-powered search system**.”

### Key Decision
We **did not replace** traditional search.  
We **enhanced it with AI**.

### Why Hybrid Search?
- Traditional search is fast and cheap
- AI is powerful but expensive
- Hybrid gives the **best balance**

**Benefits:**
- Cost-effective  
- Reliable  
- Enterprise-ready  

---

## 5. Data Storage & Indexing

### Source of Truth
**DynamoDB**
- Stores original medical content
- Versioned documents
- Metadata (specialty, year, tags, institution)

### Keyword Search
**Elasticsearch / OpenSearch**
- Inverted index
- Filters and facets
- Exact keyword matching
- Handles most queries efficiently

### Semantic Search (Vector Layer)
- Documents split into small chunks
- Each chunk converted to an embedding
- Stored in:
  - OpenSearch Vector Index  
  *(FAISS / Pinecone also acceptable)*

### Why Hybrid?
- ~80% of queries handled by keyword search
- AI used only when needed

---

## 6. AI Search Pipeline (Core Flow)

> I explain this step-by-step in interviews.

### Step 1: Document Chunking
- Large medical documents split into meaningful chunks
- Medical context preserved

### Step 2: Embedding Generation
- Used LLM embedding model
- Each chunk converted into a vector
- Done **offline** to reduce cost

### Step 3: Query Processing
User query example:
> “Summarize treatment protocol for pediatric asthma”

System:
- Converts query into an embedding
- Runs semantic search
- Applies keyword + metadata filters

### Step 4: Hybrid Retrieval
Results combined using:
- Keyword relevance
- Semantic similarity
- Medical specialty filters

### Step 5: Context Preparation
- Top relevant chunks selected
- Duplicates removed
- Ranked by relevance

### Step 6: LLM Summarization
- LLM generates:
  - Short, clear medical summary
  - References to source documents
- Strict prompts to avoid hallucinations

---

## 7. Redis & Cost Optimization

### Redis Used For
- Caching frequent queries
- Caching summaries
- Institution-specific results

### Example
- Same hospital searches same protocol
- Cache hit → **no LLM call**

### Result
- **60–70% reduction in LLM cost**
- Cached responses under **200ms**

---

## 8. Fault Tolerance & Reliability

### Fail-Safe Design
- If AI fails, system falls back to keyword search
- No downtime
- No blank results

### Observability
- Latency monitoring
- LLM timeout handling
- Error budgets

### Multi-Tenant Safety
- Tenant-aware indexes
- Tenant-aware cache keys
- Strong data isolation

---

## 9. Quality, Accuracy & Trust

Because this is healthcare:

- Human review for critical protocols
- Strong prompt guardrails
- No free-text hallucinations
- Every summary links to original sources

**Key interview line:**
> “In healthcare, correctness mattered more than creativity.”

---

## 10. My Role

- Led system design and architecture
- Defined hybrid search strategy
- Balanced quality, latency, and cost
- Worked with product teams and medical experts
- Mentored engineers
- Owned delivery and production reliability

---

## One-Line Summary (Memorize This)

> Led the design and delivery of a scalable, cost-effective AI-powered search system for 25+ million medical documents using hybrid search, vector embeddings, Redis caching, and controlled LLM summarization.
