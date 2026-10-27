# Data scope and interpretation

[English overview](README.md) · [中文概览](README_ZH.md)

## Scope by package

| Package | Unit and included evidence | Main boundary |
| --- | --- | --- |
| 01 Random baseline | 1000 independent-random ten-step inputs, three configurations and all 3000 failed diagnostics; 30-case review notes and separate manual reconstructions | The 30 filled review rows mix simulation observations, manual edits and recorded hardware issues. They are not 30 documented physical motion trials. |
| 02 Programming efficiency | Five selected S cases, ten original paired-method rows, input/target/derived files and notes | Eight rows have complete timing pairs. The two missing traditional times remain missing. The denominator is five unique cases, not ten independent tasks. |
| 03 Modeling study | M01, M41 and M47 observed prompt/time records; all 50 prompt designs; three original model previews | The other 47 rows of artificial numerical fills are omitted from measurement tables. Design availability is not experimental completion. The comparison changes both task rules and tool access. |
| 04 Source-augmented baseline | Five source actions, 1000 generated S inputs, all 3000 old-baseline results and range-qualification records | Geometric passes at 35°/45°/90° are 0/30/486. All 516 passing configurations fail the strict source-range/locked-profile qualification. |
| 05 Adaptation and MCP | Bilingual robot-model adaptation guidance and pointers to existing public software | Documentation, not an additional empirical study. No new optimizer, SDK or commercial CAD installation is supplied. |
| 06 Local repair and hardware | Historical VI.1–VI.3 per-case research records and saved numerical fit coefficients; current-web S1000 inputs/candidates; ten recorded hardware samples and offline revalidation | Frozen historical outputs, current-web adaptations, same-source new variants and hardware observations are distinct versions and statistical populations. |
| 07 Independent-random comparison | 1000 inputs, six configurations with 6000 final records and 6000 final candidates, 4347 actually saved checkpoint files, and an index of 77 passing method/case pairs involving 72 input IDs | Best geometry coverage is 65/1000; all geometric-and-research-feature joint passes are 0. Strict source preservation is inapplicable without a source envelope. |

All failures and recorded time-budget exits are retained. Missing future states remain unobserved. A successful index is a pointer into the complete results, not a replacement for failed cases. No selection of successful cases changes the planned denominator.

## Populations, metrics and time

- Independent-random inputs use 60 independently generated joint angles per ten-step trajectory before the stated sampling-budget filter. The retained 1000 inputs were selected from 1059 generated candidates by that budget alone.
- S-series inputs are related variations of five source actions. 1000 files are not 1000 distinct industrial tasks. New variants from the same sources are not validation on unseen task families.
- Geometry indicates full-path passage under the specified model, proxies, scene and budget. It does not by itself establish source/semantic preservation, hardware completion or suitability for positive VLA demonstrations.
- The research-feature joint pass requires geometry and the stated feature conditions. A feature-gate flag alone is not the joint pass. Strict-source fields require the source applicability context.
- The current hardware sample completed 99 of 100 unique planned steps with reported retry recovery and 9 of 10 entire trajectories. Repeating the same step does not increase the unique-step numerator. First-attempt and all-attempt rates remain unknown.
- `held` means an earlier terminal state is carried forward. `observed` refers to an archived state, not necessarily a newly executed update. The fixed-batch already-confirmed proportion is not a statistical confidence lower bound.
- Core search time, per-case time, attributed reused-stage time and batch wall time have different scopes. Logical geometry calls can include cached reuse; they are not the number of actual CPU evaluations. Use each record's timing definition before aggregating.

The historical S1000 geometric 100% result and the current-scene random 6.5% result concern different data/scene conditions. Five, ten and thirty rounds are inspected budgets, not a validated finite-round guarantee of 100% success on unseen trajectories.

## Public copies and preserved originals

Public derivatives retain scientific numeric values, joint/position/orientation and speed arrays, recorded durations, missingness and historical outcome labels. Personal absolute paths, account details, private network/device identifiers and 18 historical `execution_review` authorization objects are removed. Process identifiers may be pseudonymized while their recorded durations are kept. A historical `execution_review_present` flag describes the source archive, not authorization in the public derivative.

Original hashes embedded in records continue to identify historical originals. Public manifests identify the released bytes; different hashes after metadata cleaning are expected. Relative historical identifiers, source-project labels and private-source labels are explained by package indexes and dictionaries. Private source-to-public mappings and unsanitized evidence remain local and are not in the release.

For the preserved original workbooks, privacy cleaning is confined to account/document-location metadata; worksheet values, formulas and chart content are retained. Package03 is rebuilt to isolate the three real observations from the 50 designs. CSV copies expose preserved recorded or cached values, and the workbook notes identify the calculation scope.

## Excluded material and available substitutes

Original application screenshots may contain network or workstation details and are not distributed. The release provides structured transcriptions, original note text where appropriate, and explicit evidence limitations. These transcriptions are not complete raw controller logs.

Native CAD files containing personal paths are retained locally. Exact task parameters, selected author-created previews and available geometric records are public. An image is a model illustration, not a dimensional metrology result. Third-party robot CAD, manufacturer manuals, SDK binaries, commercial software and license files are not redistributed; obtain them from the authorized upstream sources.

New collision-optimization source code, fitted-model training scripts and execution environments are excluded. Saved numerical coefficients and outputs are research data, not a claim that the underlying implementation is open source. Existing public foundation code is linked separately; publication-time software snapshots are not the frozen experimental contracts.

## What this release does not establish

The archive does not provide a training-ready visual-language-action corpus, a completed VLA training study, independently verified task preservation for every geometric pass, or a population-level robot safety guarantee. The mathematical extrapolation scenarios retain their stated assumptions and must not be read as observed hardware outcomes.

## License and attribution

The CC BY 4.0 grant covers the authors' original data, documentation and figures. Third-party references and software retain their own terms. Cite the two-author dataset entry in `CITATION.cff`, its version and the packages used. Software contributors are acknowledged by the relevant upstream projects.

## 中文范围说明

01和04均提供完整基线输入与所有配置结果，失败、超时和空白不删不补。02保留10行原始计时及两处传统耗时缺失。03只把M01、M41、M47三项作为观测，50条提示词另作设计，47条人工随机填充值不公开为测量。05仅为适配和MCP资料。06区分VI.1—VI.3历史研究、当前网页迁移候选与10条已有现场抽样；07为独立随机1000组的六配置离线比较。

100%的S1000几何通过与6.5%的随机组结果不能混写。现场99%含重试，完整轨迹为9/10；未记录的首次通过率不推算。原截图、含私有路径原生CAD和完整私有脱敏映射留在本地，任务参数、精选原像素模型图及结构化证据公开。个人元数据及18个历史执行审核授权对象已移除，研究数值和记录时间保留。数值拟合系数作为VI.3数据提供，但新增优化源码及运行环境不随数据公开。
