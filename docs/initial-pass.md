# Initial pass

## Why this brief ranked highest today

Among the remaining top-level `type: project-brief` notes, this one had the clearest combination of depth, evidence, bounded scope, and a realistic first milestone. Unlike the shorter conversion stubs, it already contains a refined thesis, prior-art review, feasibility analysis, risks, open questions, and a concrete first experiment.

## Maturity / actionability assessment

- Maturity: 5/5
  - explicit thesis
  - scoped problem framing
  - prior art and literature coverage
  - feasibility and risk analysis
  - concrete implementation path
  - citations and source trail
- Actionability: 5/5
  - clear v0 benchmark path
  - obvious first artifact: a reproducible molecule-level ablation benchmark
  - concrete dataset candidate: RedDB
  - identifiable baseline features, controls, and evaluation protocol

## Routing decision

Treated as a **coding** incubation and routed to `/Users/aimee/.openclaw/git/AlexanderPico/assembly-theory-guided-battery-materials/` because the first milestone is fundamentally a software/data workflow: ingest datasets, compute descriptors, run ablations, and evaluate benchmark results.

## Key constraints / open questions

- Assembly features may be redundant with cheaper descriptors such as molecular size or graph complexity.
- Public battery datasets are heterogeneous; dataset choice can invalidate the benchmark if labels are poorly aligned.
- Assembly tooling quality and trustworthiness still need validation.
- The project should avoid broad battery-discovery claims before proving incremental signal in a narrow molecule-level setting.

## Deliberately not being built yet

- no wet-lab workflow
- no broad inorganic cathode discovery pipeline
- no productized battery-discovery platform
- no claims that Assembly Theory outperforms established materials-informatics baselines without controlled evidence
