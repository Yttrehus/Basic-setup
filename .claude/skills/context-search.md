# Context Search

Search Qdrant for routes, conversations, docs, and advisor brain.

## Prerequisites
- SSH tunnel active: `tunnel start`
- Python venv with openai, qdrant-client

## Commands
```bash
ctx "query"                          # Hybrid search (routes + conversations + docs)
ctx "query" --advisor                # Nate Jones + Miessler frameworks
ctx "query" --advisor --author nate  # Only Nate Jones
ctx "query" --routes                 # Only route data
ctx "query" --conversations          # Only past conversations
ctx "query" --docs                   # Only established docs
ctx "query" --limit 10               # More results
ctx "query" --exact                  # Pattern/exact match
ctx "query" --filter bynavn=Randers  # Metadata filter
```

## Collections
| Collection | Content | Vectors |
|-----------|---------|---------|
| routes | Stop data, addresses, GPS | dense + sparse |
| conversations | Past sessions | dense |
| docs | Established knowledge | dense |
| advisor_brain | Nate Jones + Miessler | dense |

## How it works
1. Query analyzed for patterns (route IDs, weekdays, postcodes)
2. Routing: filter / pattern / hybrid based on query type
3. Dense (semantic) + Sparse (BM25) via Reciprocal Rank Fusion
4. Temporal decay: newer results score higher (30-day half-life)
5. Cross-encoder reranking for advisor queries
