# Hyperlexicon Usage Examples

## CLI Usage

### Basic Lookup
```bash
# Simple word lookup
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "computer" --db hyperlexicon.db --index sense.index

# Multi-word phrase
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "machine learning" --db hyperlexicon.db --index sense.index

# Limit results
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "robot" --db hyperlexicon.db --index sense.index --k 3
```

### Advanced Lookup
```bash
# With domain filtering
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "bank" --db hyperlexicon.db --index sense.index --domain finance

# With register filtering
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "computer" --db hyperlexicon.db --index sense.index --register formal
```

### Building and Maintenance
```bash
# Build fresh database
python apps/hyperlexicon/hyperlexicon_service_clean.py build --db hyperlexicon.db --index sense.index --langs en

# Add additional languages
python apps/hyperlexicon/hyperlexicon_service_clean.py build --db hyperlexicon.db --index sense.index --langs en,es,fr

# Start API server
python apps/hyperlexicon/hyperlexicon_service_clean.py serve --db hyperlexicon.db --index sense.index --host 0.0.0.0 --port 8000
```

## Python API Usage

### Direct Runtime Usage
```python
from hyperlexicon_service_clean import Runtime

# Initialize
runtime = Runtime('hyperlexicon.db', 'sense.index', 'sense.index')

# Simple lookup
results = runtime.lookup("computer", k=5)
for result in results:
    print(f"ID: {result['id']}")
    print(f"Definition: {result['definition']}")
    print(f"Score: {result.get('score', 0)}")

# Advanced lookup
results = runtime.lookup("machine learning", lang="en", k=3)
```

### Using the API Client
```python
import requests

# Simple query
response = requests.get("http://localhost:8000/lookup?q=computer&k=3")
results = response.json()

for result in results:
    print(result['definition'])
    print(f"Related terms: {result['surfaces_en']}")
```

## Use Cases

### 1. Semantic Search
```python
# Find concepts related to AI
results = runtime.lookup("artificial intelligence", k=10)
for result in results:
    if result.get('score', 0) > 0.7:  # High confidence results
        print(f"High-confidence match: {result['definition']}")
```

### 2. Concept Exploration
```python
# Explore relationships around a concept
results = runtime.lookup("robot", k=1)
if results:
    concept = results[0]
    print(f"Definition: {concept['definition']}")

    # Show hypernyms (broader concepts)
    for hypernym in concept['neighbors']['hypernym']:
        print(f"Broader: {hypernym['lemmas']}")

    # Show hyponyms (narrower concepts)
    for hyponym in concept['neighbors']['hyponym']:
        print(f"Narrower: {hyponym['lemmas']}")
```

### 3. Language Learning
```python
# Find synonyms and related terms
results = runtime.lookup("happy", k=5)
for result in results:
    print(f"Related: {result['surfaces_en']}")
    print(f"Definition: {result['definition']}")
```

## Integration Examples

### Web Application
```python
from fastapi import FastAPI
from hyperlexicon_service_clean import Runtime

app = FastAPI()
runtime = Runtime('hyperlexicon.db', 'sense.index', 'sense.index')

@app.get("/search/{query}")
def search(query: str, limit: int = 5):
    results = runtime.lookup(query, k=limit)
    return {"query": query, "results": results}
```

### Command Line Tool
```bash
#!/bin/bash
# hyperlexicon-cli.sh

DB_PATH="hyperlexicon.db"
INDEX_PATH="sense.index"

if [ $# -eq 0 ]; then
    echo "Usage: $0 <query> [limit]"
    exit 1
fi

QUERY="$1"
LIMIT="${2:-5}"

python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "$QUERY" --db "$DB_PATH" --index "$INDEX_PATH" --k "$LIMIT"
```

---
*Generated on: {datetime.now().isoformat()}*
