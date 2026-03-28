<div align="center">

# Hyperlexicon &mdash; Biomedical Use Case

### *Sense-Augmented Retrieval via Multi-Source Lexical Knowledge Graphs*

**v0.2.0** &nbsp;&middot;&nbsp; Proprietary &nbsp;&middot;&nbsp; All Rights Reserved &nbsp;&middot;&nbsp; &copy; 2025&ndash;2026 Benjamin Nelson

</div>

---

## Quick Navigation

| Category | Jump to |
|---|---|
| Interactive Visualizations | [Biomedical Use Case](#biomedical-use-case-html) &middot; [Whitepaper](#whitepaper) &middot; [Executive Brief](#executive-brief) &middot; [Knowledge Graph](#knowledge-graph-html) |
| Technical Reports | [System Overview](#system-overview) &middot; [Data Dictionary](#data-dictionary) &middot; [API Reference](#api-reference) &middot; [Usage Examples](#usage-examples) &middot; [Troubleshooting](#troubleshooting) |
| Analysis Data | [Database Analysis](#database-analysis) &middot; [Statistics](#statistics) &middot; [Functionality Tests](#functionality-tests) &middot; [Comprehensive Summary](#comprehensive-summary) |
| Network Visualizations | [Visualization Catalog](#network-visualization-catalog) |
| BRCA1 Network | [Topology](#brca1-network-topology) &middot; [Entities](#entity-catalog) &middot; [Relationships](#edge-relationships) &middot; [Quality Metrics](#quality-metrics) |
| System | [Architecture](#system-architecture) &middot; [Scale & Performance](#scale--performance) |

---

## Interactive Visualizations

Standalone HTML pages &mdash; open directly in a browser for rich, styled presentations.

| Document | File | Description |
|---|---|---|
| <a id="biomedical-use-case-html"></a>Biomedical Use Case | [index.html](index.html) | Multi-source knowledge graph, sense-augmented embeddings, STSBenchmark results, BRCA1 pathway node registry |
| <a id="whitepaper"></a>Whitepaper | [hyperlexiconbrief.html](hyperlexiconbrief.html) | System capabilities, multi-source fusion, Quadrinary Router, benchmark results, deployment profile |
| <a id="executive-brief"></a>Executive Brief | [docs/executive-brief.html](docs/executive-brief.html) | Performance envelope, architecture efficiency, operational comparison |
| <a id="knowledge-graph-html"></a>Knowledge Graph Schema | [docs/knowledge-graph.html](docs/knowledge-graph.html) | Multi-source schema (WordNet + ConceptNet + Wiktionary), multilingual coverage, BRCA1 node registry |

Additional variants in `docs/`:

| File | Description |
|---|---|
| [docs/index.html](docs/index.html) | Biomedical use case (alternate copy) |
| [docs/hyperlexicon_brief.html](docs/hyperlexicon_brief.html) | Knowledge graph structure (alternate styling) |
| [docs/hyperlexicon_brief1.html](docs/hyperlexicon_brief1.html) | Executive brief (alternate styling) |

---

## Technical Reports

Markdown documentation generated from system analysis. Readable directly on GitHub.

| <a id="system-overview"></a>Report | File | Description |
|---|---|---|
| System Overview | [output/reports/system_overview.md](output/reports/system_overview.md) | Architecture, core features, technology stack, data flow |
| <a id="data-dictionary"></a>Data Dictionary | [output/reports/data_dictionary.md](output/reports/data_dictionary.md) | Node types, edge types, FTS5 schema, embedding space specs |
| <a id="api-reference"></a>API Reference | [output/reports/api_reference.md](output/reports/api_reference.md) | REST endpoints (`/lookup`, `/define`, `/translate`), request/response formats |
| <a id="usage-examples"></a>Usage Examples | [output/reports/usage_examples.md](output/reports/usage_examples.md) | CLI commands, Python API, integration patterns |
| <a id="troubleshooting"></a>Troubleshooting | [output/reports/troubleshooting_guide.md](output/reports/troubleshooting_guide.md) | Common issues, FAQ, debug commands, performance tuning |
| Reports Index | [output/reports/README.md](output/reports/README.md) | Documentation table of contents |

---

## Analysis Data

Each analysis is available in both human-readable (`.txt`) and machine-readable (`.json`) formats.

| <a id="database-analysis"></a>Analysis | Human-Readable | Machine-Readable | Key Findings |
|---|---|---|---|
| Database Structure | [database_analysis.txt](output/database/database_analysis.txt) | [database_analysis.json](output/database/database_analysis.json) | 491,102 nodes &middot; 587,754 edges &middot; 139.64 MB &middot; 7 tables |
| <a id="statistics"></a>Network Statistics | [statistics_summary.txt](output/analysis/statistics_summary.txt) | [statistics_report.json](output/analysis/statistics_report.json) | Avg degree 2.39 &middot; max degree 816 &middot; median query &lt;100 ms |
| <a id="functionality-tests"></a>Functionality Tests | [functionality_test_summary.txt](output/analysis/functionality_test_summary.txt) | [functionality_test_report.json](output/analysis/functionality_test_report.json) | 8/8 queries passed &middot; 100% success rate &middot; edge-case coverage |
| <a id="comprehensive-summary"></a>Comprehensive Summary | [comprehensive_analysis_summary.txt](output/comprehensive_analysis_summary.txt) | [comprehensive_analysis_summary.json](output/comprehensive_analysis_summary.json) | Rollup of all analysis components with system status |

---

## Network Visualization Catalog

Generated PNG charts and graphs from network analysis. Browse the full catalog or jump to individual images.

**[View full visualization index](output/visualizations/visualization_index.md)**

### Whole Network

| Visualization | File | Description |
|---|---|---|
| Force-Directed Layout | [whole_network_force_directed.png](output/visualizations/whole_network_force_directed.png) | Entire network with nodes colored by type, sized by degree |
| Circular Layout | [whole_network_circular.png](output/visualizations/whole_network_circular.png) | Nodes organized by type with colored relationship edges |

### Structural Analysis

| Visualization | File | Description |
|---|---|---|
| Node Type Distribution | [network_by_node_type.png](output/visualizations/network_by_node_type.png) | Relationship patterns between different node types |
| Degree Distributions | [degree_distributions.png](output/visualizations/degree_distributions.png) | In-degree, out-degree, and total degree distribution plots |
| Hierarchical Structure | [hierarchical_structure.png](output/visualizations/hierarchical_structure.png) | Hypernym/hyponym hierarchical relationships |
| Relationship Heatmap | [relationship_heatmap.png](output/visualizations/relationship_heatmap.png) | Frequency of relationship types between node types |

### Subgraph Neighborhoods

| Visualization | File | Description |
|---|---|---|
| Node 104504 | [neighborhood_node_104504.png](output/visualizations/neighborhood_node_104504.png) | Local neighborhood subgraph around node 104504 |
| Node 21795 | [neighborhood_node_21795.png](output/visualizations/neighborhood_node_21795.png) | Local neighborhood subgraph around node 21795 |
| Node 29441 | [neighborhood_node_29441.png](output/visualizations/neighborhood_node_29441.png) | Local neighborhood subgraph around node 29441 |

### Statistical Dashboards

| Visualization | File | Description |
|---|---|---|
| Comprehensive Stats | [comprehensive_network_stats.png](output/visualizations/comprehensive_network_stats.png) | Multi-panel dashboard of network metrics |
| Network Evolution | [network_evolution.png](output/visualizations/network_evolution.png) | Time-series analysis of network growth |

### Distribution Charts

| Visualization | File | Description |
|---|---|---|
| Node Type Distribution | [node_type_distribution.png](output/visualizations/node_type_distribution.png) | Bar chart of node counts by type |
| Edge Type Distribution | [edge_type_distribution.png](output/visualizations/edge_type_distribution.png) | Bar chart of edge counts by type |
| Degree Distribution | [degree_distribution.png](output/visualizations/degree_distribution.png) | Overall network degree distribution |

---

## BRCA1 Network Topology

<a id="brca1-network-topology"></a>

This use case models the **BRCA1 gene pathway** as a knowledge graph demonstrating Hyperlexicon's biomedical capabilities.

| Metric | Value |
|---|---|
| Entities | 8 unique nodes |
| Relationships | 7 directed edges |
| Entity Types | 6 (`gene`, `pathway`, `variant`, `effect`, `classification`, `tissue`, `source`, `output`) |
| Relationship Types | 6 (`participates_in`, `affects`, `causes`, `observed_in`, `supports`, `supported_by`, `renders_to`) |
| Confidence Range | 0.72 &ndash; 0.95 |
| Temporal Span | Single timepoint (2025-08-26) |

### <a id="entity-catalog"></a>Entity Catalog

| Object ID | Display Label | Type | External ID | Ontology |
|---|---|---|---|---|
| gene:BRCA1 | BRCA1 gene | gene | ENSG00000012048 | GO:DNA repair |
| pathway:DNA_repair | DNA repair pathway | pathway | &mdash; | GO:0006281 |
| variant:c.68_69delAG | BRCA1 c.68_69delAG | variant | &mdash; | &mdash; |
| effect:frameshift_truncation | Frameshift &rarr; truncated protein | effect | &mdash; | &mdash; |
| classification:pathogenic | Pathogenic | classification | &mdash; | &mdash; |
| tissue:mammary_epithelium | Mammary epithelium | tissue | &mdash; | UBERON:0002398 |
| source:ClinVar_PMID12345678 | ClinVar + PMID:12345678 | source | &mdash; | &mdash; |
| output:one_liner | Frameshift &rarr; truncated protein (pathogenic) | output | &mdash; | &mdash; |

### <a id="edge-relationships"></a>Edge Relationships

| Source | Target | Relation | Confidence | Evidence |
|---|---|---|---|---|
| gene:BRCA1 | pathway:DNA_repair | participates_in | 0.92 | Ontological |
| variant:c.68_69delAG | gene:BRCA1 | affects | 0.90 | Curated |
| variant:c.68_69delAG | effect:frameshift_truncation | causes | 0.88 | Clinical |
| effect:frameshift_truncation | classification:pathogenic | supports | 0.87 | Clinical |
| classification:pathogenic | source:ClinVar_PMID12345678 | supported_by | 0.86 | Literature |
| classification:pathogenic | output:one_liner | renders_to | 0.95 | Template |
| variant:c.68_69delAG | tissue:mammary_epithelium | observed_in | 0.72 | Study Data |

### Confidence Summary

| Metric | Value |
|---|---|
| Mean | 0.870 |
| Std. Deviation | 0.076 |
| Minimum | 0.72 |
| Maximum | 0.95 |
| Median | 0.87 |

### <a id="quality-metrics"></a>Quality Metrics

| Dimension | Score | Notes |
|---|---|---|
| Completeness | 85% | Missing some ontology mappings |
| Consistency | 95% | Consistent identifier schemes |
| Timeliness | 100% | Single timepoint, current |
| Accuracy | 92% | High-confidence clinical sources |
| Provenance | 88% | Most edges have clear source attribution |

---

## System Architecture

```
Query
  |
  +---> Lexical Search  (SQLite FTS5)     exact, prefix, and Boolean surface matching
  |
  +---> Semantic Search (FAISS HNSW)      dense vector similarity over 384-dim embeddings
  |
  +---> Cross-Encoder Reranking           sentence-transformer reranker for final scoring
              |
              +---> Ranked results with full provenance, edge citations, and explanations
```

**Stack:** Python 3.10+ &middot; SQLite + FTS5 &middot; FAISS &middot; SentenceTransformers &middot; FastAPI
**Interfaces:** REST API (`/lookup`, `/define`, `/translate`, `/teach`) &middot; CLI

---

## Scale & Performance

Derived from analysis of the production knowledge base (v0.2.0):

| Metric | Value |
|---|---|
| Knowledge sources | WordNet 3.1 + ConceptNet 5.7 + Wiktionary |
| Synsets (Sense nodes) | 117,659 |
| Surface forms | 206,978 |
| Additional senses (Wiktionary) | 200,000+ |
| Commonsense edges (ConceptNet) | 500,000+ |
| Domain categories | 438 |
| Languages | 10 (en + 9 via Open Multilingual WordNet) |
| Primary encoder | Mistral-7B (4096-dim) |
| Fallback encoder | MiniLM (384-dim, 22M params) |
| STSBenchmark Spearman &rho; | 0.8752 (sense-augmented, zero fine-tuning) |
| Query latency p50 / p95 | &lt; 30 ms / &lt; 80 ms |
| Throughput | 15 kQPS @ 25% headroom |
| LLM escalation rate | 1&ndash;5% (fast-path efficiency: 95&ndash;99%) |
| Availability (design target) | 99.9% |

---

## Repository Structure

```
HyperLexicon_UseCase/
+-- README.md                          <-- you are here
+-- index.html                         Biomedical use case (BRCA1 knowledge graph)
+-- hyperlexiconbrief.html             Whitepaper (hybrid intelligence at biomedical scale)
+-- docs/
|   +-- executive-brief.html           Technical intelligence brief
|   +-- knowledge-graph.html           Knowledge graph schema
|   +-- index.html                     Biomedical use case (alternate)
|   +-- hyperlexicon_brief.html        Knowledge graph (alternate styling)
|   +-- hyperlexicon_brief1.html       Executive brief (alternate styling)
|   +-- jellyfish1.png                 Background image asset
+-- output/
    +-- comprehensive_analysis_summary.json
    +-- comprehensive_analysis_summary.txt
    +-- analysis/
    |   +-- statistics_report.json
    |   +-- statistics_summary.txt
    |   +-- functionality_test_report.json
    |   +-- functionality_test_summary.txt
    +-- database/
    |   +-- database_analysis.json
    |   +-- database_analysis.txt
    +-- reports/
    |   +-- README.md                  Documentation index
    |   +-- system_overview.md
    |   +-- data_dictionary.md
    |   +-- api_reference.md
    |   +-- usage_examples.md
    |   +-- troubleshooting_guide.md
    +-- visualizations/
        +-- visualization_index.md     Full catalog of all visualizations
        +-- whole_network_force_directed.png
        +-- whole_network_circular.png
        +-- network_by_node_type.png
        +-- degree_distributions.png
        +-- hierarchical_structure.png
        +-- relationship_heatmap.png
        +-- comprehensive_network_stats.png
        +-- network_evolution.png
        +-- neighborhood_node_104504.png
        +-- neighborhood_node_21795.png
        +-- neighborhood_node_29441.png
        +-- node_type_distribution.png
        +-- edge_type_distribution.png
        +-- degree_distribution.png
```

---

## Licensing

> **This software is proprietary. All rights are reserved.**
>
> &copy; 2025&ndash;2026 Benjamin Nelson. This source code and all accompanying files are confidential.
> Viewing within this repository is permitted for evaluation purposes only.
> Reproduction, modification, distribution, sublicensing, or commercial use &mdash; in whole or in part &mdash;
> is strictly prohibited without a written license from the copyright holder.
>
> **Commercial licensing is available.**
> For licensing, partnership, or acquisition enquiries, contact:
> **[benjaminnelson1@outlook.com](mailto:benjaminnelson1@outlook.com)**

---

## Acknowledgements

The lexical data encoded in Hyperlexicon is derived from **Princeton WordNet**, developed at Princeton University's Cognitive Science Laboratory.

> Fellbaum, C. (Ed.). (1998). *WordNet: An Electronic Lexical Database*. Cambridge, MA: MIT Press.
> Miller, G. A. (1995). WordNet: A Lexical Database for English. *Communications of the ACM*, 38(11), 39&ndash;41.

Data compiled: 2025-08-26T21:25:36.980436Z &middot; Format version: 1.0

---

<div align="center">
<sub>&copy; 2025&ndash;2026 Benjamin Nelson &nbsp;&middot;&nbsp; All Rights Reserved &nbsp;&middot;&nbsp; Hyperlexicon v0.2.0</sub>
</div>
