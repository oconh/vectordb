# vectordb

A vector database built from scratch in Python. Implements HNSW (Hierarchical Navigable Small World) indexing for approximate nearest neighbour search.

Built to understand how vector databases actually work under the hood, rather than using an existing library.

## Status

Work in progress. Building in phases.

## Goals

- Implement a storage engine for vectors and metadata
- Brute force exact search as a correctness baseline
- HNSW index for approximate nearest neighbour search
- Simple Python client API
- HTTP API via FastAPI
- Benchmark against ann-benchmarks datasets

## Structure

```
vec/
├── src/
│   ├── storage/       # Vector storage and serialisation
│   ├── index/         # HNSW and brute force index implementations
│   └── query/         # Query layer and filtering
├── tests/
├── benchmarks/        # ANN benchmark comparisons
└── docs/              # Notes on implementation decisions
```

## Phases

**Phase 1 — Storage engine**
In-memory and on-disk storage for vectors with metadata. Serialisation to binary format.

**Phase 2 — Brute force search**
Exact nearest neighbour search using cosine similarity and euclidean distance. Used as a correctness baseline throughout.

**Phase 3 — HNSW index**
Graph-based approximate nearest neighbour search. Main implementation effort.

**Phase 4 — Query layer**
Python client API. Metadata filtering. Batch inserts.

**Phase 5 — HTTP API**
FastAPI wrapper so anything can talk to it.

**Phase 6 — Benchmarking**
Run against standard ANN benchmark datasets. Compare recall and latency against Faiss, Qdrant, Chroma.

## References

- Malkov & Yashunin, [Efficient and robust approximate nearest neighbor search using Hierarchical Navigable Small World graphs](https://arxiv.org/abs/1603.09320), 2018
- [ann-benchmarks](https://ann-benchmarks.com) — standard benchmarking datasets and methodology

## Setup

```bash
git clone https://github.com/oconh/vectordb
cd vectordb
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Running tests

```bash
pytest tests/
```
