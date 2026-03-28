# Hyperlexicon Troubleshooting Guide

## Common Issues and Solutions

### 1. Database Build Issues

#### Problem: "NLTK not available"
```
RuntimeError: NLTK not available. pip install nltk and rerun.
```
**Solution:**
```bash
pip install nltk
python -c "import nltk; nltk.download('wordnet'); nltk.download('omw-1.4')"
```

#### Problem: "AttributeError: _ARRAY_API not found"
```
AttributeError: _ARRAY_API not found
```
**Solution:**
```bash
pip install "numpy<2"
```

#### Problem: Build process hangs or runs out of memory
**Solution:**
- Reduce batch size in the build process
- Use a smaller subset of WordNet
- Ensure at least 4GB RAM available

### 2. Lookup Issues

#### Problem: Empty results for all queries
**Cause:** Missing edges in database (bug in version 0.1.0)
**Solution:**
1. Delete existing database: `rm hyperlexicon.db`
2. Rebuild with fixed code: `python apps/hyperlexicon/hyperlexicon_service_clean.py build --db hyperlexicon.db --index sense.index --langs en`

#### Problem: Slow queries
**Solutions:**
1. Ensure FAISS index is loaded: Check `sense.index` file exists
2. Use smaller `k` values for faster results
3. Consider using a smaller embedding model

#### Problem: "Database not found" error
**Solution:**
```bash
ls -la hyperlexicon.db sense.index
# If missing, rebuild the database
python apps/hyperlexicon/hyperlexicon_service_clean.py build --db hyperlexicon.db --index sense.index --langs en
```

### 3. API Server Issues

#### Problem: "Connection refused" when accessing API
**Cause:** Server not running
**Solution:**
```bash
# Start the server
python apps/hyperlexicon/hyperlexicon_service_clean.py serve --db hyperlexicon.db --index sense.index --host 0.0.0.0 --port 8000

# Test in another terminal
curl "http://localhost:8000/lookup?q=test"
```

#### Problem: "Address already in use"
**Solution:**
```bash
# Kill existing processes
pkill -f hyperlexicon

# Or find and kill specific process
lsof -ti:8000 | xargs kill -9
```

### 4. Embedding Issues

#### Problem: "CUDA out of memory" or GPU issues
**Solution:**
```bash
# Force CPU usage
export CUDA_VISIBLE_DEVICES=""
```

#### Problem: Model download fails
**Solution:**
```bash
# Manual download
python -c "from sentence_transformers import SentenceTransformer; SentenceTransformer('sentence-transformers/all-MiniLM-L6-v2')"
```

### 5. Performance Optimization

#### Problem: Queries are too slow
**Solutions:**
1. **Use SSD storage** for faster I/O
2. **Increase memory** to avoid disk swapping
3. **Use smaller models** for faster embedding
4. **Reduce result count** with smaller `k` values
5. **Enable WAL mode** for concurrent access:
   ```sql
   PRAGMA journal_mode=WAL;
   ```

#### Problem: Memory usage too high
**Solutions:**
1. Use smaller embedding models
2. Process queries in smaller batches
3. Consider using approximate nearest neighbors (already implemented with HNSW)

### 6. Data Quality Issues

#### Problem: Poor results for specific domains
**Cause:** WordNet coverage limitations
**Solutions:**
1. Add custom domain-specific data
2. Use domain filtering: `--domain technology`
3. Extend with additional knowledge sources

#### Problem: Missing modern concepts
**Cause:** WordNet is from 2006
**Solutions:**
1. Implement online learning features
2. Add custom concept definitions
3. Use more recent language models

## Frequently Asked Questions

### Q: What's the difference between lexical and semantic search?
**A:** Lexical search finds exact matches in surface forms. Semantic search finds concepts with similar meanings using vector embeddings.

### Q: Why do some queries return no results?
**A:** This could be because:
1. The term isn't in WordNet
2. The database wasn't built correctly (missing edges)
3. The embedding model failed to load

### Q: Can I add my own concepts?
**A:** Currently, you'd need to modify the build process. Future versions will support dynamic concept addition.

### Q: How accurate are the results?
**A:** Accuracy depends on:
- WordNet's concept coverage
- Embedding model quality
- Query specificity
- Domain filtering

### Q: Can I use this in production?
**A:** The system is research-grade. For production use:
1. Add proper error handling
2. Implement authentication
3. Add rate limiting
4. Set up monitoring

## Getting Help

### Debug Information
To get debug information, run:
```bash
# Check system status
python -c "
import sys
print('Python version:', sys.version)
import sqlite3
print('SQLite version:', sqlite3.sqlite_version)
import numpy
print('NumPy version:', numpy.__version__)
"

# Check database status
sqlite3 hyperlexicon.db "SELECT type, COUNT(*) FROM node GROUP BY type;"

# Check index status
ls -la sense.index sense.ids.npy
```

### Performance Monitoring
```bash
# Monitor memory usage
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "computer" --db hyperlexicon.db --index sense.index --k 1
time python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "machine learning" --db hyperlexicon.db --index sense.index --k 5
```

### Log Files
The system generates minimal logs. For more detailed logging, check:
- API server output (when running with `--log-level info`)
- Python warnings and errors
- SQLite error messages

---
*Generated on: {datetime.now().isoformat()}*
