You are a senior backend engineer and systems architect.

Design and implement a production-grade `shared_db.py` module for a Streamlit-based AI document intelligence application built in Python.

---

## 🧠 Application Context

The application already supports:

* Document upload (PDF, DOCX, CSV, images, etc.)
* Document parsing and chunking
* Embedding generation (using models like OpenAI / Sentence Transformers)
* Vector-based retrieval (RAG)
* Chart assistant for analytics

However, the current system lacks:

* Persistent database architecture
* Multi-user isolation (no login system)
* Fault tolerance and recovery mechanisms
* Proper storage of embeddings and metadata

---

## 🎯 Objective

Create a **complete database layer (`shared_db.py`)** that handles:

### 1. 📦 Storage Requirements

Design schema and logic for:

* Documents metadata
* Parsed chunks
* Embeddings (vector storage)
* User sessions (without login system)
* Chat history (for assistant context)
* File metadata (type, size, timestamps)

---

### 2. 👤 User Isolation WITHOUT Login

Implement:

* Unique anonymous user identification (UUID stored in Streamlit session/local storage)
* Logical separation of data per user
* Ability to reload previous session documents

---

### 3. 🧱 Database Choice

Use:

* SQLite (for metadata)
* FAISS or ChromaDB (for vector storage)

Design it in a **modular way** so it can later scale to PostgreSQL + pgvector.

---

### 4. ⚡ Core Functionalities (MANDATORY APIs)

Implement clean Python functions/classes for:

* init_db()
* create_user_session()
* save_document()
* store_chunks_and_embeddings()
* retrieve_user_documents()
* semantic_search(query, user_id)
* delete_document()
* clear_user_data()

---

### 5. 🛡️ Fault Tolerance & Reliability

Handle:

* App crashes during upload/embedding
* Partial writes
* Duplicate documents
* Corrupted embeddings
* Database locks (SQLite concurrency issues)

Include:

* Transactions
* Retry mechanisms
* Safe rollback
* Logging (structured logs)

---

### 6. 🔄 Persistence & Recovery

Ensure:

* Data persists across Streamlit restarts
* Reconnect/reload vector index automatically
* Rebuild FAISS/Chroma index if corrupted

---

### 7. 🚀 Performance Considerations

Include:

* Lazy loading of embeddings
* Index caching
* Batch inserts
* Efficient similarity search

---

### 8. 🧪 Developer-Friendly Design

Provide:

* Clean class-based architecture
* Type hints
* Docstrings
* Separation of concerns
* Configurable paths (DB path, vector store path)

---

### 9. 📁 Output Requirements

Return:

* Complete `shared_db.py` file
* Well-structured and production-level code
* No placeholders or pseudo-code
* Ready to plug into Streamlit app

---

### 10. ⚠️ Constraints

* Do NOT assume authentication system exists
* Must work in local environment
* Avoid overly complex distributed systems (keep it realistic for a student project but production-aware)

---

## 💡 Bonus (if possible)

* Add optional migration path to PostgreSQL
* Add basic caching layer
* Add simple monitoring hooks

---

Write the code as if this will be evaluated in a technical interview for a top tech company.
