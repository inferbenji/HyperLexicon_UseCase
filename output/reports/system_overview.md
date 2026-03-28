# Hyperlexicon System Overview

## Project Description
Hyperlexicon is a **sense-centric hybrid retrieval system** for interpretable language state estimation, applying Active Inference principles to language processing.

## Core Features
- **Hybrid Retrieval**: Combines symbolic graph reasoning with vector similarity search
- **Sense-Centric**: Focuses on semantic meaning rather than surface strings
- **Interpretable**: Every retrieval can be explained through provenance tracking
- **Online Learning**: System adapts through usage patterns

## System Architecture

### Components
1. **SQLite Database**: Stores the knowledge graph with nodes and relationships
2. **FAISS Index**: Provides fast vector similarity search over embeddings
3. **Sentence Transformers**: Generate semantic embeddings for concepts
4. **FastAPI Server**: RESTful API for system interaction
5. **CLI Tools**: Command-line interface for direct system access

### Data Flow
```
Query → Lexical Search → Semantic Search → Reranking → Results
     ↓          ↓              ↓           ↓          ↓
 Surface   FTS5 Index    FAISS Index   Cross-encoder  JSON API
 Matching   (SQLite)      (Embeddings)  Reranker      Response
```

## Technology Stack
- **Backend**: Python 3.10+
- **Database**: SQLite with FTS5 full-text search
- **Vector Search**: FAISS (Facebook AI Similarity Search)
- **Embeddings**: SentenceTransformers (HuggingFace)
- **Web Framework**: FastAPI
- **Data Processing**: NumPy, pandas
- **Visualization**: Matplotlib, seaborn

## Installation Requirements
```bash
pip install faiss-cpu sentence-transformers fastapi uvicorn nltk tqdm numpy
```

## Quick Start
```bash
# Build the database
python apps/hyperlexicon/hyperlexicon_service_clean.py build --db hyperlexicon.db --index sense.index --langs en

# Test lookup
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "computer" --db hyperlexicon.db --index sense.index --k 5

# Start API server
python apps/hyperlexicon/hyperlexicon_service_clean.py serve --db hyperlexicon.db --index sense.index --host 0.0.0.0 --port 8000
```

---
*Generated on: 2025-08-24T14:10:11.231462*
