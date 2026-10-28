# Repolex Knowledge Graph of dask/cachey

RDF knowledge graph data for [dask/cachey](https://github.com/dask/cachey), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download dask/cachey
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 789e03dbc64e4f39a56724f9b02643c02f704959
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 789e03dbc64e4f39a56724f9b02643c02f704959
│           └── chunk-001.nq.gz
├── blob
│   ├── 19cb69c444affca257b262d35813e6ab64fe7170.nq.gz
│   ├── 5e6aee600ff6adf9759508c3c2272ed26fbe8bf3.nq.gz
│   ├── 649c11513b9778bcd3f1a975545011c550ad506b.nq.gz
│   ├── 7378dec685b7b8929117758c3a77e0bbcf90d6c8.nq.gz
│   ├── 7739d9f559acb16d5e820afa221919ed4a455193.nq.gz
│   ├── 7eac6d00df2bdab68976c129ef4b319a307f4ffa.nq.gz
│   ├── 8f36012f383b69f9452613b2a8d03e7a4b39f098.nq.gz
│   ├── 990fa3561f0a7e99a874b54db5da9dbb685b9bf2.nq.gz
│   ├── a24bf02c28c5392d62949d791ea4955e5b13fea3.nq.gz
│   ├── a5bcbc68355351a40a9c709a60e456775deefc33.nq.gz
│   ├── ab4175a59fe6a4d47de60f899e7442bb1fde9585.nq.gz
│   ├── c6d453569a7a916f27be6105e96bd3d967fd9226.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f123f59d7356d6365f97efe14a1edf83b7abd391.nq.gz
│   ├── f9e8c2f9fde66a3c4c522bf4e831bc4e217fb585.nq.gz
│   └── fad7fc968a1cc84203403b99670920175d874bfe.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 789e03dbc64e4f39a56724f9b02643c02f704959.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 24 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[dask/cachey](https://github.com/dask/cachey)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
