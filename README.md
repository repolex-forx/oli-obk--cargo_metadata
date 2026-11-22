# Repolex Knowledge Graph of oli-obk/cargo_metadata

RDF knowledge graph data for [oli-obk/cargo_metadata](https://github.com/oli-obk/cargo_metadata), parsed by [repolex](https://repolex.ai).

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
rlex download oli-obk/cargo_metadata
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── c08e66cdf534313085ef810ce6f2e0df8a83fc50
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── c08e66cdf534313085ef810ce6f2e0df8a83fc50.nq.gz
│   └── repolex
│       └── c08e66cdf534313085ef810ce6f2e0df8a83fc50
│           └── chunk-001.nq.gz
├── blob
│   ├── 09b88501bd11a5d2f0972604a4ffc6ae40a43bdb.nq.gz
│   ├── 10d82090ed15fb6ca8719c3dcb625b55198201b3.nq.gz
│   ├── 1b2d7a7b7fe02d3580edfd0baf4b0a6b10b37fb9.nq.gz
│   ├── 21a1a48b588e8e52c8cb0042936a321f65eb1481.nq.gz
│   ├── 245eb229cea3220cf1086f986108e3f54a845c4a.nq.gz
│   ├── 2fbab0cc8a0192813aec05c3c1aa459202009566.nq.gz
│   ├── 31aa79387f27e730e33d871925e152e35e428031.nq.gz
│   ├── 34ce8fde6fe5a5695123234c50903a93d5f89966.nq.gz
│   ├── 35bc4180e25cec55817a1a90edf8b924e584789d.nq.gz
│   ├── 446a68b6726133c7f8bc20abe53e1e6c65a8d0ab.nq.gz
│   ├── 4de86e7d24e5bebd8fbc47abf4e8b9213c5da543.nq.gz
│   ├── 6d639eff6f34623d6ccb1ba40e2bc59197ee4ab3.nq.gz
│   ├── 6f5d46017d54e3cb17cd50a495fa47348f86aab0.nq.gz
│   ├── 7d85e3c32b10249f22b70a19f36f21a42afedfda.nq.gz
│   ├── 7f77850de76d361d1d416ec77bdcc7424676abde.nq.gz
│   ├── 7fe6321c0bba8effce80f4aadce0158e94445018.nq.gz
│   ├── 811404c75d7a3ca24d4c202521cc3a43c7f2b9ec.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   ├── 95a8ab88a0d3158dc5431eea66bb15dd97bd9536.nq.gz
│   ├── b54ec48584ac86192201366c7df392fd05d0d36d.nq.gz
│   ├── b59f0aba0c33c32e5c679d39a6a33cd188b4cdee.nq.gz
│   ├── b77ffcb52726fa1b6f59fa6278be7fedd03039d7.nq.gz
│   ├── bfb8bfe2d9617dcddc59428f92849f496ce1e1b6.nq.gz
│   ├── c2b0909e32a056da5c90635363c7537e323c75fc.nq.gz
│   ├── c55834e61e5f642108dc2d54daa016b0374bbe0d.nq.gz
│   ├── d0a34ed14ba640580235f0f70b57067c886e992e.nq.gz
│   ├── d45ef25d3f364c0e217a2f01e84367406311895c.nq.gz
│   ├── dbe21128a0d4ae36e5416eb0bde68198726c269d.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── e7a11a969c037e00a796aafeff6258501ec15e9a.nq.gz
│   ├── f328e4d9d04c31d0d70d16d21a07d1613be9d577.nq.gz
│   └── f729c925d28d65a3e0b783063fe43a73f026d4eb.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── c08e66cdf534313085ef810ce6f2e0df8a83fc50.nq.gz
├── filetree
│   └── c08e66cdf534313085ef810ce6f2e0df8a83fc50.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 42 files
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

[oli-obk/cargo_metadata](https://github.com/oli-obk/cargo_metadata)

---
*Parsed on 2026-11-22 by [repolex](https://repolex.ai)*
