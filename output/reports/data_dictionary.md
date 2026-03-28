# Hyperlexicon Data Dictionary

## Overview
This document describes the data structures and schema used in the Hyperlexicon system.

## Node Types

### Sense Nodes
Represent semantic concepts from WordNet.

**Attributes:**
- `id`: Unique identifier (integer)
- `type`: Always "Sense"
- `payload`: JSON object with:
  - `synset`: WordNet synset identifier (e.g., "00001740-n")
  - `pos`: Part of speech (n, v, a, r)
  - `lang`: Language code (e.g., "en")
  - `lemmas`: List of word forms
  - `lexname`: Lexical category name

**Example:**
```json
{
  "id": 12345,
  "type": "Sense",
  "payload": {
    "synset": "00001740-n",
    "pos": "n",
    "lang": "en",
    "lemmas": ["entity", "something"],
    "lexname": "noun.Tops"
  }
}
```

### Definition Nodes
Store textual definitions for concepts.

**Attributes:**
- `id`: Unique identifier
- `type`: Always "Definition"
- `payload`: JSON object with:
  - `text`: Definition text
  - `lang`: Language code

### Surface Nodes
Represent word forms and surface strings.

**Attributes:**
- `id`: Unique identifier
- `type`: Always "Surface"
- `payload`: JSON object with:
  - `text`: Surface form text
  - `lang`: Language code

### Example Nodes
Store usage examples.

**Attributes:**
- `id`: Unique identifier
- `type`: Always "Example"
- `payload`: JSON object with:
  - `text`: Example text
  - `lang`: Language code

### Domain Nodes
Represent topic domains.

**Attributes:**
- `id`: Unique identifier
- `type`: Always "Domain"
- `payload`: JSON object with:
  - `name`: Domain name

### Register Nodes
Represent usage registers (formal, informal, etc.).

**Attributes:**
- `id`: Unique identifier
- `type`: Always "Register"
- `payload`: JSON object with:
  - `name`: Register name

## Edge Types

### explained_by
Links a Sense to its Definition.

**Direction:** Sense → Definition

**Attributes:**
- `src`: Sense node ID
- `dst`: Definition node ID
- `type`: "explained_by"
- `weight`: 1.0 (default)
- `confidence`: 1.0 (default)

### realizes
Links a Surface form to its Sense.

**Direction:** Surface → Sense

**Attributes:**
- `src`: Surface node ID
- `dst`: Sense node ID
- `type`: "realizes"
- `weight`: 1.0 (default)
- `confidence`: 1.0 (default)

### hypernym
Links a concept to its broader category.

**Direction:** Specific → General

**Attributes:**
- `src`: Specific concept ID
- `dst`: General concept ID
- `type`: "hypernym"
- `weight`: 1.0 (default)
- `confidence`: 1.0 (default)

### hyponym
Links a concept to its narrower instances.

**Direction:** General → Specific

**Attributes:**
- `src`: General concept ID
- `dst`: Specific concept ID
- `type`: "hyponym"
- `weight`: 1.0 (default)
- `confidence`: 1.0 (default)

### antonym
Links concepts with opposite meanings.

**Direction:** Bidirectional

**Attributes:**
- `src`: First concept ID
- `dst`: Second concept ID
- `type`: "antonym"
- `weight`: 1.0 (default)
- `confidence`: 0.9 (WordNet antonyms)

### similar_to
Links similar concepts.

**Direction:** Bidirectional

**Attributes:**
- `src`: First concept ID
- `dst`: Second concept ID
- `type`: "similar_to"
- `weight`: 0.8 (default)
- `confidence`: 0.9 (default)

### preferred_in
Links concepts to their preferred domains.

**Direction:** Sense → Domain

**Attributes:**
- `src`: Sense node ID
- `dst`: Domain node ID
- `type`: "preferred_in"
- `weight`: 0.8 (default)
- `confidence`: 0.9 (default)

### usage
Links concepts to their usage registers.

**Direction:** Sense → Register

**Attributes:**
- `src`: Sense node ID
- `dst`: Register node ID
- `type`: "usage"
- `weight`: 0.8 (default)
- `confidence`: 0.9 (default)

## Full-Text Search Index (Lexicon)

### Structure
The FTS5 virtual table provides fast text search over surface forms.

**Columns:**
- `rowid`: Surface node ID (links to node.id)
- `surface`: Surface form text
- `lang`: Language code
- `surface_unaccented`: Normalized surface form

### Search Features
- Exact phrase matching: `"machine learning"`
- Prefix matching: `computer*`
- Boolean operators: `robot OR android`
- Language filtering: `lang:en`

## Embedding Space

### Overview
Concepts are embedded using SentenceTransformers to enable semantic similarity search.

### Model
- **Name**: `sentence-transformers/all-MiniLM-L6-v2`
- **Dimension**: 384
- **Normalization**: L2 normalized

### Generation Process
1. Combine lemmas and definition: `"word1 word2...\n definition text"`
2. Encode using SentenceTransformer
3. Store in FAISS HNSW index
4. Map back to node IDs via numpy array

## Performance Characteristics

### Database Size (Approximate)
- **Small**: ~50MB (10k concepts)
- **Medium**: ~150MB (100k concepts)
- **Full WordNet**: ~150MB (117k concepts)

### Query Performance
- **Lexical search**: < 10ms
- **Semantic search**: < 100ms
- **Full pipeline**: < 200ms (including reranking)

### Memory Usage
- **Database**: Loaded in memory by SQLite
- **Index**: ~200MB for full WordNet
- **Runtime**: ~500MB total

---
*Generated on: {datetime.now().isoformat()}*
