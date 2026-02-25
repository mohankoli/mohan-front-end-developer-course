Users (Doctors / Students)
          |
          v
        CDN
 (Static Assets + Cached Responses)
          |
          v
     Load Balancer
          |
          v
 API Gateway
(Auth, Tenant, Rate Limit)
          |
          v
 Search Orchestrator (Node.js)
          |
   ------------------------------------------------
   |               |               |              |
   v               v               v              v
Bloom Filter     Redis        Keyword Search   Vector Search
                 Cache         (OpenSearch)     (Vector DB)
                   |                |                |
                   |                |                |
                   v                |                |
            Cached Result           |                |
                        \           |                /
                         \          |               /
                          v         v              v
                           -------- Hybrid Ranking --------
                                          |
                                          v
                             LLM Summarization Model
                          (Controlled, Guardrailed)
                                          |
                                          v
                               Response Formatter
                                          |
                                          v
                                  Final Response
