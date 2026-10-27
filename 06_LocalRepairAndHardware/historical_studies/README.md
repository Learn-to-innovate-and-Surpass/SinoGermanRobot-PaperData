# Frozen studies supporting manuscript sections VI.1–VI.3

These are recorded offline experiments preceding the current-web adaptation in package 06. Complete selected cohorts, failures and observed checkpoints are included. This release supports inspection and reanalysis of the reported statistics; it does not include executable optimization, fitting, robot-control or environment code.

Start with:

- [`summary.csv`](summary.csv): compact, record-checked headline counts for all three stages.
- [`DATASET_CATALOG.json`](DATASET_CATALOG.json): file counts, sizes and stage entry points.
- [`paper_result_checks.json`](paper_result_checks.json): denominator, checkpoint and paired-comparison checks.
- [`input_index.csv`](input_index.csv): 2400 input pointers and hashes. Historical random1000 and S1000 point to packages 01 and 04. Only the new A200/B200 cohorts are stored here.
- [`PUBLICATION_SCOPE.json`](PUBLICATION_SCOPE.json): numerical parameter data versus excluded executable code.

## VI.1 Nearest-two-joint version and failure diagnosis

`VI1/results/baseline/random/` and `VI1/results/baseline/S/` each contain 1000 case records and 1000 baseline candidate files. `VI1/results/new/random/` and `VI1/results/new/S/` each contain 1000 case records and 3000 budget candidate files at K=5,10,30. The CSVs at `VI1/results/` retain their original detailed measurements, curves and extrapolation limits. Frozen scene options, generation manifests, runtime metadata and positive controls are under `records/` and `verification/`.

The 180° baseline passed 15/1000 random and 237/1000 S trajectories. The initial nearest-two-joint version passed 0/1000 at each inspected budget in both cohorts. Reduced surrogate loss is not counted as a complete-path success. No failed record or budget output was replaced with a later successful candidate.

## VI.2 Staged offsets, retained baselines and retrospective unions

| Path below `VI2/results/` | Evidence |
| --- | --- |
| `cases/`, `candidates/` | Development evaluation records and their candidate outputs |
| `S1000_frozen/` | All 1000 frozen staged-search cases, preseed documents and final candidates; 426 geometric passes, including 23/50 development and 403/950 evaluation cases |
| `S1000_historical_union/` | All 1000 retrospective union cases/candidates; old multi-cap union546, selected union562, 16 new-only cases |
| `random_extra_seed/` | All 1000 random cases and outputs; retained15 old passes plus10 added passes gives25/1000 |
| `profile_affine_exploration/` | Recorded development exploration, separate from frozen evaluation |
| `upgrade_analysis/` | Original case/aggregate CSVs and analysis summaries |

Contracts and independent checks are retained. Retrospective unions are marked post-hoc and are not treated as frozen blind tests. Additional search and fallback work are not hidden behind an equal-compute claim.

## VI.3 Fitted proposals and local collision repair

| Path below `VI3/` | Evidence |
| --- | --- |
| `results/historical1000/` | Regression/prototype proposal comparison on historical S1000: combined400, prototype-only400, ridge-only379 |
| `results/fresh200/`, `inputs/fresh200/` | Regression A200 cohort: combined80, prototype-only80, ridge-only77 |
| `results/cap360_historical1000/`, `results/cap360_fresh200/` | Expanded-angle evaluation and all recorded cases/candidates, separately labeled |
| `results/fresh200_previous_nonmirror/` | Earlier A200 comparison records |
| `results/local_blocks_historical1000/` | Full frozen S1000 batch: geometry1000, geometry plus research feature400, strict source0 |
| `results/local_blocks_fresh200_local/`, `inputs/fresh200_local/` | Local-policy B200 batch: geometry200, geometry plus feature80, strict source0 |
| `results/local_blocks_analysis/`, `results/vi3_analysis/` | Original detailed comparison tables and summaries |
| `probes/results/` | Development diagnostics, including the three source-bounded probes and warm-initialization/fit-attribution records |
| `verification/` | Independent checks, paired offset comparisons, source-bound/probe and local-batch audits |
| `model_data/fitted_offsets.json` | Numerical regression coefficients, feature centers, development labels, prototypes, recorded results and formula descriptions; no executable implementation |

At K=5,10,30 the S1000 confirmed geometry counts are848/1000/1000 and B200 counts165/200/200. Early success may be carried forward as an observed state; a nominal budget is not the number of rounds actually executed. All actually saved local checkpoint files are present (152 for S1000 and35 for B200). The remaining states are described in the case records rather than fabricated as new checkpoint files.

The three source-bounded probes are development-only: 3/3 geometry and strict-source passes, 0/3 geometry-plus-feature passes. They are not pooled into the main1000 or200 denominators. A200 and B200 are newly sampled variants of the same five sources, not new industrial tasks. The historical S1000 local batch adds438 geometry passes relative to the earlier post-hoc union of562; this comparison remains a historical re-evaluation with different computation.

## What was preserved or changed for publication

All retained numeric values, Boolean/null labels, array lengths, joints, speeds, counters and timings preserve the source data. The release contains no new simulation or physical experiment. JSON formatting may be compacted, and original `.json.gz` candidate files are unpacked to `.json` to avoid nested archive layers. Old gzip/source hashes retain their historical meanings; `../PUBLIC_FILE_MANIFEST.json` hashes the published files.

Personal absolute paths and private device/network identifiers are sanitized. Resolved public `path` and input-index pointers are relative to the entire release root. A legacy `relative_path` field retains its original study-relative meaning; use the accompanying resolved `path` when present. `source-project/...` retains a nonpersonal historical source label for material outside this data selection. Original/derived hash and path mappings are retained privately.

The main study cohorts retain complete per-case coverage, alongside the development and validation records actually available. Standalone authoring scripts, frozen `.py` copies, environments, compiled caches, temporary aggregation files, manuscript renderings and unrelated delivery metadata were excluded. A small five-case integration rerun duplicates main-batch cases and is not counted as a new cohort. Numerical fitted parameters and per-trial fit results are research data; publication of these JSON values does not include training or optimization source code.

作者自有数据适用仓库的CC BY4.0许可，署名见仓库引用信息。第三方引用或软件许可不因此改变。

