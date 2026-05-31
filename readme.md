# PatchNewsKG Paper Open Data

This folder collects the data and experiment artifacts that are intended to be
released with the PatchNewsKG thesis. Files here are copied from the project
workspace for publication convenience; the original working data and outputs are
not modified.

## Directory Layout

```text
paper_open_release/
├── news/
│   └── dataset.jsonl
├── qa/
│   └── qa_dataset_check.jsonl
├── qa_results/
│   ├── answers/
│   ├── metrics/
│   ├── tables/
│   └── traces/
└── patch_impact/
    ├── metrics/
    ├── samples/
    └── tables/
```

## Files

### `news/dataset.jsonl`

The processed news dataset used in the thesis experiments. Each line is one
news article in JSON format. Main fields include:

- `news_id`: unique article identifier.
- `title`: article title.
- `content`: article body.
- `date`: publication date.
- `source`: news source.
- `url`: original URL when available.
- `topic`: topic identifier used in the experiments.

This file corresponds to Appendix A.

### `qa/qa_dataset_check.jsonl`

The manually checked QA evaluation set used as the gold QA benchmark. Each line
is one QA item. Main fields include:

- `question`: question text.
- `answer`: reference answer.
- `qa_type`: question type, including `single`, `intra`, and `multi`.
- `source_news_id`: source news identifier or identifiers supporting the answer.
- `check`: automatic scoring rules for the key answer points.

This file corresponds to Appendix B.

### `qa_results/`

Full QA experiment outputs for the settings reported in the thesis:

- `answers/*.jsonl`: model answers and rule-level scoring results.
- `traces/*.jsonl`: retrieval/tool/query traces for each QA setting.
- `metrics/summary.json`: aggregate QA metrics.
- `tables/*`: Markdown and CSV tables used for thesis tables.

The included QA settings are:

- `no_retrieval`
- `semantic_k3`
- `semantic_k5`
- `semantic_k10`
- `graphrag`
- `pnk_kg_only`
- `pnk_kg_source`

This directory corresponds to Appendix C and the QA tables in Chapter 5.

### `patch_impact/`

Patch-log impact experiment outputs used in Section 5.6:

- `metrics/summary.json`: aggregate settings and results.
- `tables/*`: Markdown and CSV tables for the patch impact experiment.
- `samples/random_deletion_runs.csv`: per-run random deletion samples and impact
  statistics.

The experiment reports both direct impact and propagated impact after deleting
1, 3, 5, 10, 50, and 100 committed operations.

## Notes

- Raw working files, intermediate audit files, and local caches are not included.
- The original source files remain in their working locations under `data/` and
  `outputs/`; this folder is a publication package.
- GraphRAG is queried through an external service in the experiments, so this
  package includes GraphRAG answers and traces, not a GraphRAG index.
