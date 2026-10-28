# Repolex Knowledge Graph of Textualize/textual-demo

RDF knowledge graph data for [Textualize/textual-demo](https://github.com/Textualize/textual-demo), parsed by [repolex](https://repolex.ai).

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
rlex download Textualize/textual-demo
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── babcbd1b742ba893e834fafb6f82930ae18cad65
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── babcbd1b742ba893e834fafb6f82930ae18cad65
│           └── chunk-001.nq.gz
├── blob
│   ├── 044c47183f85d2d99baa99611cb469f39d1ef1a5.nq.gz
│   ├── 3261deabb08de29efaedb9929ab23a0ec43a03e1.nq.gz
│   ├── 3a883478402f12504551a1063f3f183fc48ade20.nq.gz
│   ├── 47a2c9eed199a62600b3265ddb5d046d6fb978c1.nq.gz
│   ├── 608bb060f69ea9e2968b50620b767569b132eb67.nq.gz
│   ├── 82f927558a3dff0ea8c20858856e70779fd02c93.nq.gz
│   ├── c7ce0602dfe420ef39f23525a260952743788870.nq.gz
│   ├── df61f714ce6bf49b8815d4576dbf6376d204b09a.nq.gz
│   └── e4fba2183587225f216eeada4c78dfab6b2e65f5.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── babcbd1b742ba893e834fafb6f82930ae18cad65.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
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

[Textualize/textual-demo](https://github.com/Textualize/textual-demo)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
