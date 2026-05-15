# Next steps

1. Pull the RedDB paper, metadata, and any downloadable tables; verify license, schema, and molecule/label coverage.
2. Decide on the exact prediction target for v0: redox potential, stability proxy, or another machine-readable electrochemical label.
3. Set up a minimal Python environment for RDKit, pandas, and baseline modeling.
4. Create a first dataset-ingestion script that normalizes SMILES, deduplicates molecules, and records missing labels.
5. Implement baseline descriptors: RDKit features, fingerprints, and simple size/ring/heteroatom counts.
6. Evaluate one assembly-feature path: exact molecular assembly if usable, otherwise a clearly labeled approximation or proxy.
7. Define scaffold-aware train/test splits and a negative-result bar before tuning models.
8. Run a small pilot benchmark on a subset to test whether the pipeline is stable and whether assembly features are computationally tractable.
9. Record failure modes explicitly, especially size confounding, data leakage, and synthetic-accessibility bias.
10. Decide after the pilot whether to continue, pivot to a negative-result note, or expand to a second dataset.
