---
title: Assembly-Theory-Guided Battery Materials
created: 2026-04-21
updated: 2026-04-29
type: project-brief
tags: [battery, materials, assembly-theory, project-idea, research]
sources:
  - /Users/aimee/Obsidian/AgentVault/_sources/notes/2026-04-10__0002__588212dc5929.md
source_urls:
  - https://en.wikipedia.org/wiki/Assembly_theory
  - https://en.wikipedia.org/wiki/Lithium-ion_battery
  - https://en.wikipedia.org/wiki/Biobattery
  - https://www.nature.com/articles/s41586-023-06600-9
  - https://www.molecular-assembly.com/
  - https://docs.materialsproject.org/
  - https://www.materialsproject.org/apps/battery-explorer
  - https://pymatgen.org/
  - https://hackingmaterials.lbl.gov/matminer/
  - https://batteryarchive.org/
  - https://arxiv.org/abs/1710.10324
  - https://arxiv.org/abs/1812.05055
  - https://arxiv.org/abs/2005.00707
  - https://github.com/BufferOverthrow/ai-battery-materials
  - https://github.com/rsilvabuarque/atomate2_ffforge
  - https://github.com/fanhuiyang1018/EICP
  - https://github.com/microsoft/BatteryML
  - https://github.com/materialsproject/matbench
  - https://github.com/croningp/Paper-AssemblyTreeOfLife
  - https://github.com/Tehlikeli107/gpu-assembly-index
  - https://arxiv.org/abs/2410.09100
  - https://arxiv.org/abs/2210.00901
  - https://arxiv.org/abs/2310.14714
  - https://arxiv.org/abs/2312.04013
  - https://doi.org/10.1038/s41597-022-01832-2
  - https://doi.org/10.1016/j.ensm.2020.06.033
  - https://doi.org/10.1021/acs.jpcc.1c06821
  - https://doi.org/10.1021/acs.jcim.5c01964
  - https://doi.org/10.1039/d4dd00293h
  - https://doi.org/10.1038/s41540-024-00403-y

---

# Assembly-Theory-Guided Battery Materials

## Current thesis
The strongest version of this project is **not** “Assembly Theory will magically find a better battery.” It is a falsifiable screening program: compute assembly-inspired complexity features for molecules, polymers, electrolytes, organic redox compounds, and possibly bioelectrochemical components, then test whether those features add predictive signal beyond standard chemistry/materials descriptors.

The current working thesis is cautiously positive: assembly-style descriptors might be useful as a *secondary prior* for underexplored organic, polymeric, electrolyte, and bio-derived storage systems, but they are unlikely to replace electrochemical physics, graph neural network embeddings, DFT-derived features, or empirical cycling data. The project is worth another research pass if it stays computational and evidence-seeking before making wet-lab claims.

**2026-04-29 refinement:** the best first target is now **molecule-level redox-flow / organic-electrode screening**, not inorganic cathode discovery and not whole-cell optimization. The reason is practical: RedDB and related organic redox datasets provide electroactive molecules where SMILES/graph representations make assembly-index experiments plausible, while inorganic crystalline cathodes are already better served by Materials Project, CGCNN/MatGL-style graph learning, DFT features, and Matbench-style benchmarks. Assembly Theory should be treated as a candidate *novelty/search-space descriptor* for molecular battery chemistries, not as a replacement for electrochemical labels.

## Seed idea
The raw note makes a speculative leap from present-day battery chemistry toward a search strategy. Lithium-based systems are already unusually effective, but the note asks whether even better targets might live among higher-assembly materials, including bio-derived or fluid-based systems. The useful part of the idea is not the specific chemistry claim by itself. It is the proposal to use a complexity-oriented search lens when looking for new storage media.

## Problem / opportunity
Battery discovery is constrained by a difficult tradeoff surface: gravimetric and volumetric energy density, power, cycle life, safety, charge/discharge rate, cost, abundance, manufacturability, recyclability, and supply-chain robustness. Most modern computational discovery workflows already use large materials databases, DFT calculations, graph representations, and benchmarked property-prediction models.

The opportunity for Alex's version is narrower and more interesting: ask whether assembly complexity identifies **neglected structured chemistries** that conventional screens underweight. Candidate lanes include:
- organic electrode materials where molecular structure is central to redox behavior;
- polymer and gel electrolytes where hierarchical organization affects ion transport;
- redox-flow or liquid systems where molecular families can be screened computationally;
- bio-battery / enzyme / microbial components where biological structure may matter, while remaining realistic about power-density limits.

## Related work and prior art
Prior art is strong and weakens any broad novelty claim:

- **Assembly Theory itself is now a published and debated measurement program.** The 2023 Nature paper “Assembly theory explains and quantifies selection and evolution” formalizes molecular assembly as a quantifiable complexity signal, but it is not a battery-discovery paper. Its relevance is as a feature source, not as direct electrochemical evidence.
- **Computational materials discovery is mature.** Materials Project, pymatgen, matminer, Matbench, CGCNN, and graph-network approaches already provide databases, descriptors, workflows, and benchmarks for materials-property prediction. A new project must plug into this ecosystem rather than ignoring it.
- **Battery-specific discovery tools already exist.** Materials Project includes battery-focused applications and intercalation/electrode-relevant data. Many ML-for-battery repositories are small, but the broader toolchain around materials informatics is real.
- **Open datasets are easier for inorganic solids than for assembly-theory targets.** Assembly features may be most natural for molecules and polymers, while many battery datasets are crystal/inorganic or device-level. Data alignment is likely a major blocker.
- **Bio-battery claims are especially speculative.** Bio-derived systems are useful as a search lane, not as evidence that high-assembly materials beat lithium-ion benchmarks.

**2026-04-29 prior-art update:** the novelty bar tightened in two directions. First, battery/materials ML has strong mature baselines: Matbench formalizes materials-property benchmarks; BatteryML standardizes battery-degradation modeling; and reviews already cover ML-assisted rechargeable-battery discovery. Second, Assembly Theory itself has moved closer to usable cheminformatics: exact/scalable molecular-assembly algorithms and molecular-assembly-tree code exist. That makes Alex's project more feasible, but less novel as “assembly computation.” The remaining novelty is the **specific ablation question**: does molecular assembly add signal for battery-relevant organic/redox/polymer targets after controlling for RDKit descriptors, fingerprints, molecular size, synthetic accessibility, and graph neural embeddings?

**Most useful adjacent dataset lane:** RedDB, a computational database of electroactive molecules for aqueous redox-flow batteries, appears to be a better v0 substrate than generic lithium-ion cell datasets because it is molecule-centered and electrochemical by design. Cell-level sources such as Battery Archive and BatteryML remain valuable for context but are less aligned with assembly-index features.

## Similar codebases / tools
High-signal tools and codebases to inspect before building anything custom:

- **Materials Project API and docs** — public materials database and query layer; relevant for baseline properties, battery-related entries, and comparison against standard descriptors. Accessed 2026-04-24: https://docs.materialsproject.org/
- **Materials Project Battery Explorer** — domain prior-art for battery-specific exploration; page access was partly blocked by 403 from automation, but the app URL is a relevant product/prior-art surface. Accessed 2026-04-24: https://www.materialsproject.org/apps/battery-explorer
- **pymatgen** — Python materials-analysis library used heavily in Materials Project workflows; useful for composition/structure parsing and feature generation. Accessed 2026-04-24: https://pymatgen.org/
- **matminer** — feature-extraction and data-mining toolkit for materials informatics; likely the fastest baseline for “do assembly-style features add anything?” experiments. Accessed 2026-04-24: https://hackingmaterials.lbl.gov/matminer/
- **Battery Archive** — public battery data repository; more device/cell oriented than molecular, but useful for grounding claims about performance and cycling data. Accessed 2026-04-24: https://batteryarchive.org/
- **BufferOverthrow/ai-battery-materials** — small GitHub repo for ML battery/materials discovery using MatBench/GNN-style framing; low-star but relevant as an example of lightweight prototype shape. Accessed 2026-04-24: https://github.com/BufferOverthrow/ai-battery-materials
- **rsilvabuarque/atomate2_ffforge** — active-learning workflow for ML interatomic potentials across batteries, polymers, electrolytes and other materials; useful model for automation architecture even if not assembly-focused. Accessed 2026-04-24: https://github.com/rsilvabuarque/atomate2_ffforge
- **fanhuiyang1018/EICP** — interpretable ML for lithium-ion battery electrolytes; relevant because electrolyte structure/function may be a better target for assembly-like descriptors than bulk cathode screening. Accessed 2026-04-24: https://github.com/fanhuiyang1018/EICP

**Additional 2026-04-29 tools / codebases:**
- **microsoft/BatteryML** — open-source platform for machine learning on battery degradation; strong evidence that battery ML infrastructure exists, but mostly cell/degradation oriented rather than molecule-level assembly screening. Accessed 2026-04-29: https://github.com/microsoft/BatteryML and https://arxiv.org/abs/2310.14714
- **materialsproject/matbench** — benchmark suite for materials-property prediction; useful for discipline around splits, baselines, and overclaim prevention. Accessed 2026-04-29: https://github.com/materialsproject/matbench and https://matbench.materialsproject.org/
- **croningp/Paper-AssemblyTreeOfLife** — code for “Exploring and Mapping Chemical Space with Molecular Assembly Trees”; relevant for assembly-space visualization and algorithmic precedent. Accessed 2026-04-29: https://github.com/croningp/Paper-AssemblyTreeOfLife
- **Tehlikeli107/gpu-assembly-index** — tiny, very low-star GPU assembly-index calculator; interesting as evidence that independent assembly-index implementations are emerging, but not yet authoritative or battery-validated. Accessed 2026-04-29: https://github.com/Tehlikeli107/gpu-assembly-index
- **materialsproject/api** — official Materials Project API client; useful if the project later compares assembly-guided organic candidates against inorganic/materials baselines. Accessed 2026-04-29: https://github.com/materialsproject/api

## Relevant literature
This round found useful *adjacent* literature rather than direct support for “assembly index predicts battery quality.” That absence matters.

- **“Assembly theory explains and quantifies selection and evolution”** — establishes the molecular-assembly concept; relevant as the candidate descriptor family, not as battery evidence. Accessed 2026-04-24: https://www.nature.com/articles/s41586-023-06600-9
- **Molecular Assembly project site** — project-facing background on assembly-index measurement and tooling; relevant for operationalizing the descriptor. Accessed 2026-04-24: https://www.molecular-assembly.com/
- **“Crystal Graph Convolutional Neural Networks for an Accurate and Interpretable Prediction of Material Properties”** — arXiv 1710.10324; shows that graph/structure representations are an established baseline for materials prediction. Accessed 2026-04-24: https://arxiv.org/abs/1710.10324
- **“Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals”** — arXiv 1812.05055; relevant as a general graph-learning baseline that assembly features would need to complement. Accessed 2026-04-24: https://arxiv.org/abs/1812.05055
- **“Benchmarking Materials Property Prediction Methods: The Matbench Test Set and Automatminer Reference Algorithm”** — arXiv 2005.00707; relevant for benchmark discipline and avoiding anecdotal feature claims. Accessed 2026-04-24: https://arxiv.org/abs/2005.00707

Automated arXiv API and Semantic Scholar search endpoints returned 429 rate-limit errors during the cron run, so this section leans on direct arXiv pages and verified domain sources rather than a complete literature survey. A later pass should retry Semantic Scholar for citation counts and review papers.

**2026-04-29 literature additions:**
- **“RedDB, a computational database of electroactive molecules for aqueous redox flow batteries”** — Scientific Data 2022; useful because it provides an explicitly electroactive, molecule-centered candidate dataset for the first assembly-feature ablation. Accessed 2026-04-29: https://doi.org/10.1038/s41597-022-01832-2
- **“Machine learning assisted materials design and discovery for rechargeable batteries”** — Energy Storage Materials 2020 review; shows that ML-guided battery discovery is already broad prior art, weakening generic novelty claims. Accessed 2026-04-29: https://doi.org/10.1016/j.ensm.2020.06.033
- **“Machine Learning-Assisted Discovery of High-Voltage Organic Materials for Rechargeable Batteries”** — Journal of Physical Chemistry C 2021; relevant because organic-electrode discovery is already an ML target and therefore a fair comparison lane. Accessed 2026-04-29: https://doi.org/10.1021/acs.jpcc.1c06821
- **“Rapid Exploration of the Assembly Chemical Space of Molecular Graphs”** — arXiv 2410.09100 / JCIM 2025; important because exact/scalable molecular assembly computation is becoming practical for organic molecules. Accessed 2026-04-29: https://arxiv.org/abs/2410.09100 and https://doi.org/10.1021/acs.jcim.5c01964
- **“A materials discovery framework based on conditional generative models applied to the design of polymer electrolytes”** — Data-centric Engineering / RSC 2025, arXiv 2312.04013; useful adjacent evidence for polymer-electrolyte generative loops, though not assembly-based. Accessed 2026-04-29: https://arxiv.org/abs/2312.04013 and https://doi.org/10.1039/d4dd00293h
- **“On the salient limitations of the methods of assembly theory and their classification of molecular biosignatures”** — npj Systems Biology and Applications 2024 / arXiv 2210.00901; important negative/critical evidence because assembly index may collapse into compression-like or graph-complexity proxies. Accessed 2026-04-29: https://arxiv.org/abs/2210.00901 and https://doi.org/10.1038/s41540-024-00403-y

## Feasibility assessment
Near-term feasibility is moderate if scoped as a computational feature-ablation study, low if scoped as immediate battery invention.

**Feasible v0 path:**
1. choose one tractable target class, probably organic redox molecules or electrolyte solvents/additives rather than all battery materials;
2. assemble a small public dataset with property labels such as redox potential, ionic conductivity, stability window, donor number, solubility, or cycling proxy;
3. compute normal descriptors with RDKit/matminer/pymatgen as appropriate;
4. add assembly-index or approximation features where computable;
5. run ablation tests: baseline descriptors vs baseline + assembly features;
6. inspect whether high-assembly outliers are chemically plausible or merely hard-to-synthesize artifacts.

**Operational blockers:**
- assembly index may be expensive or ambiguous for polymers, crystals, mixtures, and device-level components;
- battery performance labels are heterogeneous and often not directly comparable across papers;
- high complexity can correlate with synthesis difficulty, cost, instability, or poor manufacturability;
- the most available databases may not cover the molecular classes where assembly theory is most meaningful.

**2026-04-29 feasibility update:** feasibility improves if v0 is scoped around RedDB-style organic/redox molecules plus a transparent feature-ablation benchmark. A practical prototype can avoid wet-lab claims entirely: ingest SMILES and electrochemical labels; compute RDKit descriptors, fingerprints, simple graph-complexity features, synthetic-accessibility proxies, and one exact or approximate molecular-assembly feature; then compare scaffold-aware predictive performance and candidate-ranking behavior. The hard part is no longer “can any assembly-like number be computed?” but “does it add nontrivial signal after controlling for obvious confounders?”

**Recommended v0 experiment:**
1. start with RedDB or another redox-flow / organic-electrode molecular dataset with SMILES and redox labels;
2. implement three baselines: RDKit/fingerprints, graph neural embedding if available, and trivial size/heteroatom/ring descriptors;
3. add exact MA if open tooling works; otherwise add clearly labeled proxies and one molecular-assembly-tree feature;
4. run scaffold-aware or chemical-family-aware splits, not random-only splits;
5. report negative results honestly if assembly features proxy molecular size, compressibility, or synthesis complexity rather than electrochemical usefulness.

## Novelty and differentiation
Someone has already done much of the surrounding work well: Materials Project for data infrastructure, pymatgen/matminer for feature tooling, Matbench for benchmarking, CGCNN/graph networks for structure-aware ML, and numerous ML battery-screening experiments for property prediction. The novelty is **not** “ML for battery materials.”

What remains differentiated about Alex's version:
- explicitly testing Assembly Theory as a descriptor family in battery-relevant search;
- focusing on whether assembly complexity surfaces underexplored structured chemistries rather than merely predicting known inorganic baselines;
- treating the idea as falsifiable: if assembly features do not improve prediction or candidate ranking, that is a useful negative result;
- connecting origin-of-life / complexity measurement ideas to materials informatics while clearly labeling the bridge as speculative.

Speculative connection: assembly theory may be more useful for **search-space triage** than direct performance prediction. It might flag molecules/material families whose formation history or hierarchical structure suggests unexplored functionality, but that is an intuition to test, not a validated mechanism.

**2026-04-29 novelty challenge:** someone has already done much of the enabling work well: public battery/materials datasets, ML battery reviews, organic-electrode ML screens, polymer-electrolyte generative design, Matbench-style benchmark discipline, and molecular-assembly algorithms. What has *not* shown up in this pass is a strong public example of **Assembly Theory used as an ablated descriptor in battery-relevant molecule screening**. That gap is narrow but real.

Differentiation should therefore be stated conservatively: Alex's version is novel if it produces a reproducible battery-domain ablation of assembly features, identifies where assembly adds value or fails, and publishes the negative/positive result as a bridge between complexity science and materials informatics. It is not novel if it only says “complex molecules may make better batteries.”

## Risks / failure modes
- **Descriptor mismatch:** molecular assembly index may not map cleanly to crystals, composites, electrodes, or full electrochemical cells.
- **Complexity fetish:** high assembly could select expensive, fragile, toxic, or synthetically unrealistic candidates.
- **Data leakage / benchmark overclaiming:** small public datasets can make weak descriptors look useful if splits are not chemically meaningful.
- **Battery-performance confounding:** measured performance depends on formulation, electrolyte, separator, morphology, test protocol, and cycling conditions, not only active material identity.
- **Novelty collapse:** if assembly features merely proxy for molecular size or graph complexity, standard cheminformatics descriptors may already capture the signal.

**New 2026-04-29 risk:** assembly features may be redundant with much cheaper descriptors. The critical null hypothesis is that MA mostly tracks molecular size, repeated motifs, ring systems, synthetic accessibility, or compression-like graph structure. The project should pre-register these controls internally before treating any apparent performance lift as meaningful.

## Open questions
- Which target class makes assembly features most meaningful: organic electrodes, redox-flow molecules, electrolyte solvents/additives, polymers, enzymes, or microbial systems?
- Can a practical assembly-index approximation be computed at scale, or is the first experiment limited to small molecules?
- What baseline descriptors should be used so the test is fair: RDKit descriptors, graph neural embeddings, matminer composition features, DFT-derived properties, or all of the above?
- Are there public datasets with enough labels for battery-relevant molecular properties and enough structure data to compute assembly features?
- What counts as success: improved predictive accuracy, better candidate ranking, better novelty search, or a literature map of high-complexity outliers?

**2026-04-29 additions:**
- Does RedDB expose enough machine-readable structures and labels to run scaffold-aware ablations without heroic data cleaning?
- Which assembly implementation is trustworthy enough for a first pass: exact molecular assembly from recent algorithms, molecular assembly trees, GPU prototype code, or a deliberately simple proxy?
- Can assembly features be normalized by atom count / molecular weight so they do not merely reward larger molecules?
- Should success be judged by prediction error, enrichment of plausible candidates, or discovery of interpretable high-assembly outliers missed by standard descriptors?

## Future research directions
- Retry Semantic Scholar searches for review papers on organic battery materials, polymer electrolytes, and materials-informatics benchmarks once rate limits clear.
- Look for public organic-electrode and redox-flow molecule datasets with SMILES strings and comparable electrochemical labels.
- Investigate whether the Molecular Assembly ecosystem exposes usable software or APIs for assembly-index computation.
- Compare assembly-index features against simpler graph measures: molecular weight, ring count, heteroatom count, synthetic accessibility, graph diameter, fragment complexity, and standard fingerprints.
- If the computational signal is weak, pivot the project into a useful negative-result note: “Assembly Theory as a materials-discovery prior: where it fails and why.”

**2026-04-29 next research directions:**
- Pull RedDB metadata and confirm data access format, license, label definitions, and SMILES coverage.
- Run a tiny notebook-style benchmark on 100-1,000 molecules before broad literature expansion: standard descriptors vs assembly/proxy descriptors under scaffold-aware splits.
- Search for explicit critiques and replications of assembly-index algorithms so the project does not depend on a disputed measurement without controls.
- If RedDB is unsuitable, pivot to organic-electrode datasets from high-voltage organic-material ML papers or polymer-electrolyte monomer datasets.

## Implementation sketch / experiment ideas
A concrete first experiment could be completed without wet-lab work:

1. **Dataset selection:** pick one molecule-level dataset, ideally redox-flow or organic electrode candidates with SMILES and measured/calculated redox properties.
2. **Baseline featurization:** generate RDKit descriptors/fingerprints plus any available domain labels.
3. **Assembly proxy:** compute exact assembly index if tooling is available; otherwise start with transparent approximations such as fragment reuse, graph edit construction proxies, motif counts, and hierarchical decomposition depth.
4. **Ablation model:** train simple models under scaffold/time-aware splits: baseline-only, assembly-only, and baseline-plus-assembly.
5. **Outlier review:** inspect high-assembly/high-predicted-performance candidates for toxicity, synthesis plausibility, abundance, and literature coverage.
6. **Decision gate:** continue only if assembly features add out-of-sample signal or produce a compelling shortlist that standard descriptors miss.

## Relationship to the current corpus
This is currently more of an incubator page than a settled article. It is included in the live layer because it captures an Alex-originated research direction rather than public discourse synthesis alone. For a map of the broader article layer, start with [[index]]. For the adjacent systems-level framing around diagnostics, forecasting, controllability, and energy infrastructure rather than chemistry search, see [[energy-legibility-is-becoming-an-infrastructure-layer]].

## Working triage scores
| Date | Maturity | Novelty | Feasibility | Strategic fit | Evidence | Notes |
|---|---:|---:|---:|---:|---:|---|
| 2026-04-29 | 5 | 4 | 4 | 3 | 5 | Evidence and feasibility improved because the project now has a concrete RedDB/organic-redox ablation path and clearer assembly-computation prior art; strategic fit remains moderate because wet-lab translation is distant. |

## Citations / sources
- **Assembly theory explains and quantifies selection and evolution** — https://www.nature.com/articles/s41586-023-06600-9 — accessed 2026-04-24. Relevance: core Assembly Theory paper; supplies candidate complexity concept but not battery validation.
- **Molecular Assembly** — https://www.molecular-assembly.com/ — accessed 2026-04-24. Relevance: project/tooling context for assembly-index measurement.
- **Materials Project documentation** — https://docs.materialsproject.org/ — accessed 2026-04-24. Relevance: established materials data/query infrastructure to use as a baseline.
- **Materials Project Battery Explorer** — https://www.materialsproject.org/apps/battery-explorer — accessed 2026-04-24. Relevance: prior-art battery exploration product; automation saw 403 on the app page, so details need manual follow-up.
- **pymatgen** — https://pymatgen.org/ — accessed 2026-04-24. Relevance: standard Python library for materials analysis and data preparation.
- **matminer** — https://hackingmaterials.lbl.gov/matminer/ — accessed 2026-04-24. Relevance: feature-extraction toolkit for materials-informatics baselines.
- **Battery Archive** — https://batteryarchive.org/ — accessed 2026-04-24. Relevance: public battery dataset repository; more cell/device focused than molecular.
- **Crystal Graph Convolutional Neural Networks for an Accurate and Interpretable Prediction of Material Properties** — https://arxiv.org/abs/1710.10324 — accessed 2026-04-24. Relevance: graph/structure-aware baseline method.
- **Graph Networks as a Universal Machine Learning Framework for Molecules and Crystals** — https://arxiv.org/abs/1812.05055 — accessed 2026-04-24. Relevance: general molecule/crystal graph-learning baseline.
- **Benchmarking Materials Property Prediction Methods: The Matbench Test Set and Automatminer Reference Algorithm** — https://arxiv.org/abs/2005.00707 — accessed 2026-04-24. Relevance: benchmark discipline for materials-property prediction.
- **BufferOverthrow/ai-battery-materials** — https://github.com/BufferOverthrow/ai-battery-materials — accessed 2026-04-24. Relevance: small example ML battery-materials prototype; useful as shape, not authority.
- **rsilvabuarque/atomate2_ffforge** — https://github.com/rsilvabuarque/atomate2_ffforge — accessed 2026-04-24. Relevance: active-learning / MLIP workflow touching batteries, polymers, and electrolytes.
- **fanhuiyang1018/EICP** — https://github.com/fanhuiyang1018/EICP — accessed 2026-04-24. Relevance: interpretable ML for electrolyte conductivity; relevant candidate target area.

- **BatteryML: An Open-source platform for Machine Learning on Battery Degradation** — https://github.com/microsoft/BatteryML and https://arxiv.org/abs/2310.14714 — accessed 2026-04-29. Relevance: strong open-source prior art for battery ML infrastructure; mostly degradation/cell-level rather than molecular assembly screening.
- **Matbench** — https://github.com/materialsproject/matbench and https://matbench.materialsproject.org/ — accessed 2026-04-29. Relevance: benchmark discipline and baseline comparison for materials-property ML.
- **RedDB, a computational database of electroactive molecules for aqueous redox flow batteries** — https://doi.org/10.1038/s41597-022-01832-2 — accessed 2026-04-29. Relevance: likely best molecule-level substrate for a first assembly-feature ablation.
- **Machine learning assisted materials design and discovery for rechargeable batteries** — https://doi.org/10.1016/j.ensm.2020.06.033 — accessed 2026-04-29. Relevance: review showing broad prior art in battery materials informatics.
- **Machine Learning-Assisted Discovery of High-Voltage Organic Materials for Rechargeable Batteries** — https://doi.org/10.1021/acs.jpcc.1c06821 — accessed 2026-04-29. Relevance: organic-electrode ML prior art that any assembly descriptor must beat or complement.
- **Rapid Exploration of Assembly Chemical Space of Molecular Graphs** — https://arxiv.org/abs/2410.09100 and https://doi.org/10.1021/acs.jcim.5c01964 — accessed 2026-04-29. Relevance: exact/scalable molecular-assembly computation makes the ablation technically more plausible.
- **A materials discovery framework based on conditional generative models applied to the design of polymer electrolytes** — https://arxiv.org/abs/2312.04013 and https://doi.org/10.1039/d4dd00293h — accessed 2026-04-29. Relevance: adjacent polymer-electrolyte generative-design baseline.
- **On the salient limitations of the methods of Assembly Theory and their classification of molecular biosignatures** — https://arxiv.org/abs/2210.00901 and https://doi.org/10.1038/s41540-024-00403-y — accessed 2026-04-29. Relevance: critical/negative evidence; forces controls against compression-like and size-confounded assembly signals.
- **Paper-AssemblyTreeOfLife** — https://github.com/croningp/Paper-AssemblyTreeOfLife — accessed 2026-04-29. Relevance: codebase for assembly chemical-space mapping; possible source of implementation ideas.
- **GPU Assembly Index Calculator** — https://github.com/Tehlikeli107/gpu-assembly-index — accessed 2026-04-29. Relevance: emerging low-maturity implementation; useful to inspect but not yet authoritative.

## Nightly research log
### 2026-04-24
Selected for the nightly maturation pass because the overview marked it as the least-developed / lowest-evidence high-upside project: novelty 5, feasibility 2, evidence 2. This round substantially strengthened the page by grounding the idea in Materials Project, pymatgen, matminer, Matbench/CGCNN/graph-network baselines, Battery Archive, small GitHub battery-ML repos, and the core Assembly Theory paper.

Key conclusion: the project remains interesting only if framed as a falsifiable descriptor-ablation study. Prior art already covers ML-driven materials discovery well, so Alex's differentiator is the specific Assembly Theory feature hypothesis and the cross-field bridge from complexity measurement to battery-relevant search. The strongest next move is to pick one molecule-level battery target class and test whether assembly-derived features add predictive or ranking value beyond standard descriptors.

### 2026-04-29
Selected again as the least-developed / most technically uncertain project after all five top-level stubs had received one prior maturation pass. This round moved the page from a broad “assembly theory might help battery discovery” hypothesis toward a narrower, testable RedDB / organic-redox ablation program.

Concrete updates: strengthened the current thesis; added RedDB as the best v0 dataset lane; added BatteryML, Matbench, molecular-assembly-tree code, and emerging assembly-index implementation references; added literature on organic-electrode ML, polymer-electrolyte generative design, assembly chemical-space algorithms, and critiques of Assembly Theory; updated feasibility, novelty, risks, open questions, future research directions, citations, and a working score vector.

Key conclusion: the project remains worth further effort only as a falsifiable feature-ablation study. Prior art already does battery/materials ML well, and Assembly Theory itself is contested. The interesting contribution would be a controlled result showing whether molecular assembly adds signal beyond standard descriptors—or a well-documented negative result showing that it does not.
