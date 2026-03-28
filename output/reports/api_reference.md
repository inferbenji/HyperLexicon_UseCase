# Hyperlexicon API Reference

## Overview
The Hyperlexicon system provides a RESTful API for semantic search and language understanding.

## Base URL
```
http://localhost:8000
```

## Endpoints

### GET /lookup
Perform semantic lookup for a query term or phrase.

**Parameters:**
- `q` (string, required): Query term or phrase
- `k` (integer, optional): Number of results to return (default: 8)
- `domain` (string, optional): Filter by topic domain
- `register` (string, optional): Filter by usage register

**Response:**
```json
[
  {
    "id": 12345,
    "definition": "A machine for performing calculations automatically",
    "surfaces_en": ["computer", "computing machine"],
    "domains": ["technology"],
    "registers": ["formal"],
    "neighbors": {
      "hypernym": [{"id": 67890, "lemmas": "machine"}],
      "hyponym": [{"id": 54321, "lemmas": "laptop"}],
      "antonym": [],
      "similar_to": [{"id": 98765, "lemmas": "calculator"}]
    },
    "score": 0.85
  }
]
```

**Example:**
```bash
curl "http://localhost:8000/lookup?q=artificial%20intelligence&k=3"
```

### GET /define (Future)
Get definitions for a term.

### GET /translate (Future)
Translate terms between languages.

## Response Format
All API responses follow a consistent format:

- **Success**: HTTP 200 with JSON array of results
- **Error**: HTTP 4xx/5xx with error message

## Rate Limiting
- No rate limiting implemented in current version
- Each request processes up to 8 results by default

## Error Handling
The API provides detailed error messages for debugging:

```json
{
  "error": "Database connection failed",
  "details": "Could not connect to hyperlexicon.db"
}
```

## Authentication
- No authentication required in current version
- Future versions may implement API keys

---
*Generated on: {datetime.now().isoformat()}*
