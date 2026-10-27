# 02 工业动作编排计时 / Programming efficiency

[完整数据ZIP / Full package](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/02_ProgrammingEfficiency_v1.0.0.zip)

Git仓库目录仅包含说明和精选小表；完整压缩包包含下述全部数据路径。The Git directory contains documentation and selected small tables; download the complete archive for all data paths described below.

[中文与English说明](#数据解释与引用--data-interpretation-and-attribution) · [返回数据总览](../README.md)

本包保留从S系列90°几何通过池486条中分层抽取的5个case，以及示教器、JSON微调两类基线共10行人工参与计时。计划经验标签不是经过随机受试者验证的人群分层。

## 内容 / Contents

- `paired_inputs/`与`paired_targets/`：5对原输入和90°旧算法参考目标，case与action_id保持对应。
- `operator_derived_actions/`：另5份实际人工修订/审核来源文件；与历史参考目标分别存放，公开副本移除执行授权记录。
- `records/sampling_design.json`：种子20261017，分层规模97/97/98/97/97，每层1个。
- `tables/programming_efficiency.xlsx`、`成对计时.csv`：全部10行原记录与备注。传统分钟有两项缺失，原有新方法分钟仍保留；缺失不填0、不填60。
- `tables/方法与字段.csv`和`protocol/`：分母、计时范围及历史实验设计。

示教器5项完整配对累计166→49 min（70.5%）；JSON微调仅3项完整配对累计127→23 min（81.9%）。S-0276传统JSON侧仅备注“超过1小时”，S-0070为未能完成；两者不进入完整配对节约率。新流程时间包含人工定位/修订/算法调用，不能等同算法单次核心秒数或VLA训练耗时。

All ten original rows are retained. Only eight rows have complete timing pairs. Missing traditional times remain missing, while recorded new-method times and operator notes remain unchanged. The five unique cases, rather than ten comparison rows, define the independent case count.

## 数据解释与引用 / Data interpretation and attribution

数据及作者自制资料按本仓库CC BY 4.0许可使用，引用时注明论文作者、仓库版本及所用数据包。既有软件遵循各自许可证。研究数值、关节/速度数组、测量时间和原备注不因隐私清理而更改；公开副本移除账户、个人主目录、私网设备地址和执行审核授权等元数据。原始文件的研究哈希可能记录去标识前的字节，实际公开文件校验以本目录`manifest.csv`为准。私有清理映射不公开。

JSON为历史研究材料；被移除的执行审核记录不得恢复或据此直接下发运动。几何检查通过仅适用于相应模型、场景与预算。VLA训练尚未实施。

`manifest.csv` lists the SHA-256 of each public file. Existing recorded source hashes refer to historical originals; metadata sanitization can change byte hashes while preserving measured values. Private audit mappings are retained separately. These records carry no execution authorization.

工作簿和历史协议中保留的实验相对路径，可用`data_path_index.csv`查到当前包内位置；该索引不含个人主目录。Historical relative file identifiers in preserved workbooks/protocols are mapped to current public locations by `data_path_index.csv`.
