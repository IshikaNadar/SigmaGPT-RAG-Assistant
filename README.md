# SigmaGPT-RAG-Assistant
Domain‑specific AI assistant using OpenAI embeddings and vector databases with Retrieval‑Augmented Generation (RAG), source attribution, and explainability UI. Designed to deliver transparent, reliable answers with reduced hallucinations in a full‑stack deployment.

# SigmaGPT RAG Assistant — Domain Specific Retrieval Augmented Generation : 
SigmaGPT is a domain‑specific retrieval augmented generation assistant that ingests documents, builds embeddings, and answers user queries with clear source attribution and explainability. The demo shows a full ingestion pipeline, vector index, retrieval + LLM answer generation, and a simple human feedback loop — all deployed with a small sample dataset for recruiters to test.

# MVP Features :

* Document ingestion pipeline :
-Upload PDFs, paste URLs, or add markdown files.
-Automatic text extraction and basic cleaning for each document.
-Configurable chunking with overlap and metadata tagging.

* Embeddings and Vector Index :
-Generate embeddings per chunk using OpenAI or a configurable embeddings provider.
-Index chunks into a vector database (Chroma, Weaviate, RedisVector, or local file snapshot).
-Support for reindexing and incremental updates.

* Retrieval and RAG :
-Query box that retrieves top‑k chunks from the vector index.
-Prompt template that combines retrieved chunks with the user query to call an LLM.
-Answer generation with confidence score and short explanation.

* Explainability and Source Attribution :
-UI shows which documents and chunks were used to produce the answer.
-Each source displays document title, chunk excerpt, and link to original file.
-A short “why this answer” explanation explains which evidence was used.

* Human Feedback Loop :
-Thumbs up / thumbs down per answer.
-Feedback stored for future tuning and simple analytics (positive rate per document).

* Demo readiness :
-Preloaded sample dataset and vector DB snapshot for immediate testing.
-Public demo link and sample accounts for recruiters.

# Architecture and Components :
* Frontend :
-React.js SPA with a query box, answer pane, source list, and ingestion UI.
-Minimal explainability UI showing top‑k chunks and a short rationale.
-Simple admin page to view ingestion status and feedback metrics.

* Backend :
-Node.js + Express API for ingestion, embedding generation, retrieval orchestration, and LLM calls.
-Background worker for chunking and embedding generation.
-Simple job queue for ingestion tasks.

* Vector Database :
-Pluggable vector DB adapter supporting Chroma, Weaviate, RedisVector, or a local fallback.
-Index snapshot included for demo to avoid long reindexing times.

* Embeddings and LLM :
-Configurable provider for embeddings and LLM calls (OpenAI or compatible alternatives).
-Prompt templates stored server side and applied at retrieval time.

* Storage :
-Document storage for uploaded files and extracted text.
-Metadata store for documents, chunks, and feedback (MongoDB or PostgreSQL).

* Deployment :
-Frontend deployable to Vercel.
-Backend and worker deployable to Render, Heroku, or a container platform.
-Optional Docker Compose for local demo with a local vector DB.

# Phase 2 Enhancements and Standout Features :
* Document ingestion improvements :
-OCR for scanned PDFs and improved HTML extraction.
-Auto metadata extraction and entity tagging.

* Advanced retrieval :
-Hybrid search combining sparse and dense retrieval.
-Relevance tuning with feedback signals.

* Explainability upgrades :
-Token level attribution and provenance scoring.
-Short natural language chain‑of‑thought style explanation for answers.

* Evaluation and analytics :
-Answer quality dashboard with feedback trends and per‑document performance.
-A/B testing for prompt templates and retrieval parameters.

* Security and governance :
-Access controls for private corpora.
-Redaction and PII detection during ingestion.
