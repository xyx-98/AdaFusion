# PathoOracle / AdaFusion NC Figure Plan

## One-sentence manuscript argument

In computational pathology, pathology foundation models encode complementary and spatially structured tissue preferences; PathoOracle/AdaFusion orchestrates these models through compact adaptive gating, improving downstream performance while exposing phenotype- and microenvironment-level model specialisation that can guide efficient model selection.

## Terminology ledger

- `PathoOracle`: preferred NC manuscript name for the interpretability-oriented orchestration framework.
- `AdaFusion`: method/module name for compact adaptive feature fusion.
- `PFM`: pathology foundation model.
- `adaptive gate`: sample-aware model-wise or model-channel weighting module.
- `contribution score`: scalar model contribution derived from adaptive gate weights.
- `dominance map`: spatial map assigning each tile to the PFM with the largest contribution score.
- `phenotype preference`: recurring association between PFM contribution and tissue morphology or phenotype cluster.
- `microenvironment topology`: graph/nuclear-feature description of local tissue structure beyond visual tissue categories.
- `preference-guided routing`: selecting a smaller PFM subset based on contribution similarity/complementarity.

## Results narrative

The Results should move from utility to explanation and then deployment:

1. Compact orchestration improves prediction and representation quality.
2. The learned contribution scores are spatially coherent and phenotype-aware.
3. These preferences are reproducible and quantifiable across slides, labels, and phenotype clusters.
4. PFM preferences extend beyond visible tissue appearance into microenvironment topology.
5. Preference similarity and complementarity support efficient model selection/routing.

This order keeps performance as the entry point but makes interpretability the main story.

## Main Figure Set

## Figure-to-experiment mapping

Principle:
Except for Fig. 1, each main figure should be an experimental result figure. A small top `a` panel can show the experimental design or analysis schematic, but the visual weight should stay on measured results, representative examples and quantification.

### Fig. 2 corresponds to Experiment A + B + part of C

Main experimental question:
Does compact adaptive orchestration improve downstream performance and representation granularity?

Included experiments:
- A1: ROCAUC summary across datasets.
- A2: Balanced ACC summary across datasets.
- A3: PCC summary for HEST / spatial transcriptomics tasks.
- A4: FPS / storage / feature burden comparison, if complete enough for main text.
- B1: Feature distribution visualization across single PFMs and fused features.
- C1: Cluster separability of fused features versus single PFM features.

Recommended panels:
- a: Experimental schematic for performance evaluation and feature-compression settings.
- b: Delta performance over best single PFM across datasets.
- c: 64/256/512 compression tradeoff.
- d: Fusion baseline comparison.
- e: One cluster-separability example plus quantitative separability score.
- f: Efficiency panel only if it strengthens the story; otherwise Supplementary.

Supplementary candidates:
- Full per-dataset tables.
- Full original/512/256/64 results for every PFM.
- All UMAPs not used as the main representative example.

### Fig. 3 corresponds to Experiment D1 + D2 + representative-tile selection

Main experimental question:
Do different PFMs spatially dominate different tissue regions in real slides?

Included experiments:
- D1: Winner-takes-all PFM dominance map for each tissue / slide.
- D2: Local tile-level contribution composition map or inset.
- Representative high-contribution tile retrieval for each PFM.

Recommended panels:
- a: Optional mini schematic explaining contribution score -> dominance map.
- b: Three-dataset image plate: H&E overview, dominance map, ROI H&E, ROI preference overlay.
- c: Representative tiles from high-confidence PFM-dominant regions.
- d: Small local ROI contribution composition quantification if space allows.

Suggested datasets:
- ATEC: treatment-response tissue with heterogeneous tumour/stroma regions.
- DHMC-Lung: lung cancer subtype tissue with different tissue architectures.
- PANDA: prostate grading with elongated tissue strips and glandular morphology.

Supplementary candidates:
- Additional slides from the same three datasets.
- Full slide contact sheets.
- Alternative visualization forms such as separate per-PFM opacity maps.

### Fig. 4 corresponds to Experiment D3 + D4 + D5/D6

Main experimental question:
Are PFM preferences quantifiable and reproducible across slides, labels and tissue phenotype clusters?

Included experiments:
- D3: Per-slide group/tile proportions and group-level contribution statistics.
- D4: Per-PFM continuous contribution score maps or score distributions.
- D5: ResNet-feature tissue grouping followed by PFM preference proportion analysis.
- D6: Test-set-wide tile clustering, not slide-wise clustering, followed by PFM preference analysis.

Recommended panels:
- a: Optional mini schematic: tiles -> phenotype clusters -> PFM preference profiles.
- b: Slide-level dominance proportion distributions.
- c: Cluster-by-PFM preference heatmap.
- d: Clinical-label-specific preference profiles.
- e: Representative phenotype-cluster thumbnails.
- f: Stability or confidence interval panel.

Supplementary candidates:
- All cluster numbers / sensitivity to K.
- All datasets not selected for the main heatmap.
- Per-PFM continuous maps for additional slides.

### Fig. 5 corresponds to Experiment D6.1 + D6.2 + D6.3 + D6.4

Main experimental question:
Do PFM preferences reflect microenvironment topology beyond coarse visual tissue type?

Included experiments:
- D6.1: Graph visualization of representative PFM-dominant tiles.
- D6.2: Graph topology metric statistics for top-k tiles per PFM, and top-versus-bottom comparisons.
- D6.3: Nuclear-feature or graph-feature association with PFM contribution scores, ideally as significance dot plot.
- D6.4: Graph encoding / graph-feature embedding, colored by dominant PFM.

Recommended panels:
- a: Optional mini schematic: nuclei/cells -> graph -> graph descriptors -> contribution association.
- b: Representative graph overlays on high-contribution tiles.
- c: Significance dot plot for PFM contribution versus nuclear/graph features.
- d: Top-k versus bottom-k graph metric comparison.
- e: Graph-feature embedding colored by PFM, only if visually clean.

Supplementary candidates:
- All individual scatter plots for feature-contribution correlations.
- Full graph metric list.
- Extra representative graphs per PFM.

### Fig. 6 corresponds to Experiment A5 + routing / selection experiments

Main experimental question:
Can measured PFM similarity and complementarity guide efficient FM subset selection?

Included experiments:
- A5: Coarse PFM complementarity test using UNI and H-optimus-0 as anchor models, plus most/least similar additional PFMs.
- A5.1: Similarity based on tissue tile clustering coverage.
- A5.2: Similarity based on tile-level PFM attention / contribution assignment distributions.
- A5.3: Similarity based on representative PFM-dominant tile features plus graph encoding.
- Automatic FM selection / routing experiments.

Recommended panels:
- a: Optional mini schematic: preference profiles -> similarity/complementarity -> selected subset.
- b: PFM-PFM similarity matrix.
- c: Complementarity graph or ranked pair/subset results.
- d: Automatic selection result across datasets.
- e: Performance-cost Pareto plot comparing best single PFM, selected subset, and all PFMs.
- f: Optional spatial sanity check: selected subset reproduces full-model preference pattern.

Supplementary candidates:
- All anchor-model combinations.
- Full greedy-selection traces.
- Per-dataset selected model subsets.

### Optional Fig. 7 corresponds to Experiment E

Main experimental question:
Do PathoOracle explanations align with task-specific biological or clinical signals?

Included experiments:
- E1: Convert previous performance tables into task-specific visual summaries.
- E2: Spatial transcriptomics / gene expression visualization in HEST.
- E3: CAMELYON16 tumour-region-specific PFM contribution and tumour-region attention comparison.
- E4: Runtime, storage and feature-resource comparison, if not already in Fig. 2 or Fig. 6.

Recommendation:
Use Fig. 7 only if one task-specific biological result is exceptionally convincing. Otherwise, put E-series analyses into Supplementary Figures and mention them in Results as supporting evidence.

### Fig. 1 | Why multi-PFM orchestration is needed and how PathoOracle works

Core conclusion:
PFMs differ in pretraining geography, data source, scale, tissue composition, architecture and objectives, motivating a compact adaptive orchestration framework.

Status:
Already drafted as `writing/fig1.png`.

Role:
Conceptual entry figure and visual vocabulary for model colors, method flow, contribution maps and downstream tasks.

Key revision targets:
- Keep model colors identical in all later figures.
- Reduce small text if final double-column width makes panels b-d hard to read.
- Consider replacing any decorative elements with data-backed panels when moving from concept draft to submission figure.

### Fig. 2 | Compact adaptive orchestration improves performance and representation granularity

Core conclusion:
AdaFusion improves or preserves performance across diverse pathology tasks despite aggressive feature compression, and yields more discriminative phenotype-level representations than individual PFMs or naive fusion.

Archetype:
Quantitative grid with one representative visual example.

Panel map:
- a: Dataset/task overview matrix. Rows: datasets; columns: task type, sample number, metric, split/MCCV setting.
- b: Main performance summary across all datasets. Use paired dot/slope plot or heatmap of delta over best single PFM, not a huge table.
- c: Compactness/performance tradeoff. Compare original, 512, 256, 64 dimensions for single PFMs and AdaFusion.
- d: Benchmark comparison against fusion baselines: naive ensemble, self-attention, top-k MoE, AdaFusion-C, AdaFusion-F.
- e: Cluster separability example. One dataset, one visually strong case: individual PFM embeddings vs AdaFusion embedding, with phenotype labels or cluster purity/silhouette/NMI.
- f: Optional feature burden/FPS/storage panel if the numbers are ready; otherwise move to Supplementary.

Evidence needed:
- MCCV mean and uncertainty for AUC/BACC/PCC.
- Statistical comparison against best single PFM and fusion baselines.
- Cluster separability metric: silhouette, Davies-Bouldin, Calinski-Harabasz, NMI/ARI if labels exist, or phenotype purity if pathology/cluster labels exist.

Reviewer risk:
The claim "cluster区分度更高" needs a quantitative metric, not only UMAP. UMAP can be the example, but a small bar/dot plot should quantify separability.

### Fig. 3 | Spatial contribution maps reveal phenotype-specific PFM preferences

Core conclusion:
Different PFMs dominate distinct tissue regions in a spatially coherent way across representative pathology tasks.

Archetype:
Image plate + quant, with the image plate as the hero.

Panel map:
- a: Three-dataset representative image plate. Suggested rows: ATEC, DHMC-Lung, PANDA. Columns: H&E overview, PFM dominance map, ROI H&E crop 1, ROI preference crop 1, ROI H&E crop 2, ROI preference crop 2.
- b: Representative dominant tiles for each PFM, selected from high-confidence contribution regions.
- c: Local composition insets for the selected ROIs, showing model contribution proportions rather than winner-takes-all only.

Current asset fit:
The existing fig3 draft already fits this role. It should remain mostly qualitative/感性, with just enough local quantification to prove the maps are not arbitrary.

Key revision targets:
- Avoid too many tiny representative tiles; choose fewer, larger, pathologically interpretable tiles.
- Use the same ROI colors and PFM colors throughout.
- Add scale bars consistently.
- Keep one shared legend, not repeated legends.

Reviewer risk:
Dominance maps can look like noisy pixel mosaics. The figure needs ROI crops and representative tiles to connect colors to recognizable tissue morphology.

### Fig. 4 | PFM preferences are reproducible and quantifiable across phenotypes and labels

Core conclusion:
PFM contribution patterns are not isolated visual anecdotes; they form reproducible preference profiles across slides, phenotype clusters and clinical labels.

Archetype:
Quantitative grid.

Panel map:
- a: Slide-level PFM dominance proportion distributions for multiple datasets.
- b: Phenotype-cluster by PFM enrichment heatmap. Rows: clusters/phenotypes; columns: PFMs; values: dominance enrichment or mean contribution.
- c: Clinical label-specific preference profiles. Example: positive vs negative response, tumour subtype, grade group.
- d: Stability across MCCV folds or slides. Show confidence intervals/bootstrapped uncertainty.
- e: Representative cluster thumbnails beside the most interpretable phenotype clusters.

Evidence needed:
- Definition of phenotype clusters: K-means/GMM/ResNet-based clusters, pathology-validated labels, or morphology-derived clusters.
- Per-slide and per-label statistics.
- Multiple-testing correction if many cluster-PFM associations are tested.

Reviewer risk:
If clusters are unsupervised, avoid naming them as biological phenotypes unless morphology is visually defensible or pathologist-confirmed. Use "phenotype-like clusters" or "morphological clusters" when needed.

### Fig. 5 | PFM preferences capture microenvironment topology beyond visible tissue appearance

Core conclusion:
PFM specialisation is associated not only with gross tissue morphology but also with nuclear and graph-based microenvironment structure.

Archetype:
Asymmetric mixed-modality figure.

Panel map:
- a: Pipeline for microenvironment analysis: tile -> nuclei/cell detection -> graph construction -> graph/nuclear descriptors -> association with PFM contribution.
- b: Representative high-contribution tiles for selected PFMs with nuclear graph overlays.
- c: Significance dot plot. x-axis: PFMs; y-axis: nuclear/graph features; color: correlation direction/effect size; size: -log10(p).
- d: Top vs bottom contribution comparison for graph metrics, shown as paired dot/box/violin plots.
- e: Optional graph embedding UMAP colored by dominant PFM, if it cleanly separates.

Evidence needed:
- Exact nuclear/graph feature list.
- Sampling strategy for tiles.
- Correlation metric and statistical test.
- Correction for repeated tests.

Reviewer risk:
Graph analysis can feel bolted on unless it answers a clear question. Keep the claim narrow: "preferences are associated with microenvironment topology", not "PFMs understand cell-cell interactions" unless validated.

### Fig. 6 | Similarity and complementarity reveal efficient PFM combinations

Core conclusion:
Contribution/profile similarity identifies redundant and complementary PFMs, enabling smaller model subsets that approximate or match full multi-PFM performance.

Archetype:
Quantitative grid with routing schematic.

Panel map:
- a: PFM-PFM similarity matrix based on contribution profiles, tissue cluster profiles, or attention distributions.
- b: Complementarity graph/network. Edges indicate low similarity plus positive performance gain when combined.
- c: Automatic FM selection/routing results. Show selected subsets across datasets/tasks.
- d: Performance-cost Pareto plot. x-axis: compute/storage/FPS/model count; y-axis: performance; highlight selected subset vs all PFMs and best single PFM.
- e: Case study showing that preference-guided subset reproduces the full-model spatial contribution pattern.

Evidence needed:
- The "previous similarity result" should be formalized: feature-space similarity, dominance-map similarity, cluster-profile similarity, or attention-distribution similarity.
- Automatic selection rule: greedy forward selection, routing by phenotype profile, or trained selector.
- Cost metrics: feature extraction cost, storage, inference FPS, memory, or number of PFMs.

Reviewer risk:
This figure should not read as a separate engineering appendix. It must close the loop: interpretability is useful because it supports efficient deployment.

### Optional Fig. 7 | Task-specific biological/clinical readouts

Core conclusion:
PathoOracle explanations align with task-specific biological signals in selected clinical or molecular tasks.

Use only if the evidence is strong enough:
- HEST: predicted gene expression spatial maps aligned with tissue regions.
- CAMELYON16: contribution/preference in annotated tumour regions.
- HER2/Yale cohorts: preference profiles linked to HER2 or trastuzumab response.

Recommendation:
Keep this as Supplementary unless one task-specific result is exceptionally strong and visually convincing. The main manuscript already has a full logic arc with Fig. 1-6.

## Preferred 6-figure main-text structure

If the target is tight and elegant:

- Fig. 1: Framework and motivation.
- Fig. 2: Performance, compactness and representation granularity.
- Fig. 3: Spatial PFM contribution maps, qualitative across three datasets.
- Fig. 4: Quantified phenotype/label preference profiles.
- Fig. 5: Microenvironment graph/nuclear feature analysis.
- Fig. 6: Similarity, complementarity and efficient FM routing.

This is cleaner than making 7 main figures. Fig. 7-style task-specific readouts can become Supplementary Figures or a small panel inside Fig. 4/5 if needed.

## Suggested Results headings

1. Adaptive orchestration improves pathology modelling with compact representations.
2. Fused representations enhance phenotypic discrimination across downstream tasks.
3. Foundation models show spatially coherent but heterogeneous tissue preferences.
4. Preference profiles vary reproducibly across phenotypes and clinical labels.
5. Model preferences are associated with microenvironment topology.
6. Preference regularities enable efficient foundation-model routing.

## Main claims and evidence status

- Claim: AdaFusion improves performance across datasets.
  Evidence: MCCV result CSVs exist for 12 datasets.
  Status: supported, needs polished statistical summary.

- Claim: AdaFusion improves cluster/phenotype separability.
  Evidence: planned from feature distribution/cluster visualization.
  Status: needs quantitative separability metric.

- Claim: Different PFMs prefer different tissue regions.
  Evidence: existing dominance maps and fig3 draft across ATEC, DHMC-Lung and PANDA.
  Status: supported qualitatively, needs quantification.

- Claim: Preferences are stable across slides/labels/clusters.
  Evidence: experiment plan exists.
  Status: needs compiled aggregate statistics.

- Claim: Preferences reflect microenvironment topology.
  Evidence: experiment plan exists for graph/nuclear features.
  Status: needs completed analysis and bounded wording.

- Claim: Similarity/complementarity supports automatic FM selection.
  Evidence: previous similarity and selection results mentioned.
  Status: needs formal definition and main-figure-ready summary.
