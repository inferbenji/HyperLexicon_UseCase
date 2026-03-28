# Hyperlexicon Documentation

## Overview
This documentation provides comprehensive information about the Hyperlexicon system, a sense-centric hybrid retrieval system for interpretable language state estimation.

## Documentation Index

### 📋 System Documentation
- [**System Overview**](system_overview.md) - Architecture and core concepts
- [**Data Dictionary**](data_dictionary.md) - Schema and data structures
- [**API Reference**](api_reference.md) - REST API documentation

### 🚀 Usage and Examples
- [**Usage Examples**](usage_examples.md) - Tutorials and code examples
- [**Troubleshooting Guide**](troubleshooting_guide.md) - Common issues and solutions

### 📊 Analysis Reports
- [`../analysis/database_analysis.json`](../analysis/database_analysis.json) - Database structure analysis
- [`../analysis/statistics_report.json`](../analysis/statistics_report.json) - Statistical summaries
- [`../analysis/functionality_test_report.json`](../analysis/functionality_test_report.json) - Test results

### 📈 Visualizations
- [`../visualizations/node_type_distribution.png`](../visualizations/node_type_distribution.png) - Node distribution chart
- [`../visualizations/edge_type_distribution.png`](../visualizations/edge_type_distribution.png) - Edge distribution chart
- [`../visualizations/degree_distribution.png`](../visualizations/degree_distribution.png) - Network degree distribution

## Quick Start
```bash
# Test the system
python apps/hyperlexicon/hyperlexicon_service_clean.py lookup "computer" --db hyperlexicon.db --index sense.index --k 3

# Start API server
python apps/hyperlexicon/hyperlexicon_service_clean.py serve --db hyperlexicon.db --index sense.index --host 0.0.0.0 --port 8000

# Access documentation
open output/reports/README.md
```

## System Status
- **Database**: ✅ Ready
- **Index**: ✅ Ready
- **Documentation**: ✅ Generated

## Contributing
To contribute to the documentation:
1. Update the source scripts in `src/`
2. Run the documentation generator
3. Submit a pull request with improvements

---
*Generated on: 2025-08-24T14:10:11.232389*
