# Repolex Knowledge Graph of simonw/llm-cmd

RDF knowledge graph data for [simonw/llm-cmd](https://github.com/simonw/llm-cmd), parsed by [repolex](https://repolex.ai).

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
rlex download simonw/llm-cmd
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1db3a14fdf2b9a01d1af53689346b12fb3c6dd06
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1db3a14fdf2b9a01d1af53689346b12fb3c6dd06
│           └── chunk-001.nq.gz
├── blob
│   ├── 02b5db8a052e210d7419af8c9d5b3f057a13dc4e.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 301bfd0b3e3be398352b9334ed531d41cb5a49f0.nq.gz
│   ├── 33b9d3375295a95ea6be77e31da221946c59379a.nq.gz
│   ├── 5142287ae4bf2184fb5a8f7a659e0c523168cb6a.nq.gz
│   ├── 9a56ceaa1c9a6e1037fea3e2921e67239363c776.nq.gz
│   ├── b259043609eff59c381cae87e3a1572ed1161635.nq.gz
│   └── e61ce1d68a38f43ce1ad952ccdb94f9ab7d69670.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1db3a14fdf2b9a01d1af53689346b12fb3c6dd06.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 16 files
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

[simonw/llm-cmd](https://github.com/simonw/llm-cmd)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
