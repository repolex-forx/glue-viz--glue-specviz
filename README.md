# Repolex Knowledge Graph of glue-viz/glue-specviz

RDF knowledge graph data for [glue-viz/glue-specviz](https://github.com/glue-viz/glue-specviz), parsed by [repolex](https://repolex.ai).

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
rlex download glue-viz/glue-specviz
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3fa33fda16e07c312248c497a093fe2e42cbe717
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3fa33fda16e07c312248c497a093fe2e42cbe717
│           └── chunk-001.nq.gz
├── blob
│   ├── 2fbf4a681e02c534958a80babba574dd7f840e65.nq.gz
│   ├── 3abd18a5d88bdcb24d63c7be53d9f860fdf1c93e.nq.gz
│   ├── 438654f328167db35583069ee63675ae9bf4a1b2.nq.gz
│   ├── 5e1dfc4391518fdc90f6191c4ff8ce3b81c7c1d8.nq.gz
│   ├── 72b552e805413279f8363154d381a285817c2c91.nq.gz
│   ├── 868375043bd316d56e7fb84b6351c8a9d4a223b5.nq.gz
│   ├── b2a1f6bb7b8018cc442873023afbe1fc49d12b93.nq.gz
│   ├── bb1c07df9d08b5a7f9b3205acedd0136bdaadfef.nq.gz
│   ├── c715f8520eb73171daccd0ec3593e43e79aaf55f.nq.gz
│   ├── de3cd94d005cb6c4b5f533ae5bba970bbff5082b.nq.gz
│   └── e01e8168834cd469e5b81e1edc1654c7542d8452.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3fa33fda16e07c312248c497a093fe2e42cbe717.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 19 files
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

[glue-viz/glue-specviz](https://github.com/glue-viz/glue-specviz)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
