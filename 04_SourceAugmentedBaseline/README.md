# 04 来源增强轨迹旧基线 / Source-augmented baseline

[完整数据ZIP / Full package](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/04_SourceAugmentedBaseline_v1.0.0.zip)

Git仓库目录仅包含说明和精选小表；完整压缩包包含下述全部数据路径。The Git directory contains documentation and selected small tables; download the complete archive for all data paths described below.

[中文与English说明](#数据解释与引用--data-interpretation-and-attribution) · [返回数据总览](../README.md)

本包补齐五个已有动作来源各200条、共1000条S系列原输入，以及35°、45°、90°三档全部3000次旧基线结果。每条输入含10步。S系列由索引插值、共同偏移和受来源范围约束的逐点扰动生成，J6原插值被冻结；它不是01完全独立均匀随机集。

## 内容 / Contents

- `source_actions/`：五个种子动作及来源清单、零位设置；不包含厂家SDK或CAD。
- `data/inputs/`：S-0001至S-1000原输入。
- `data/results/`：三档共3000条结果。YS文件为完整几何代理通过输出；F结果文件为失败诊断，二者保持原始文件类型，不把失败报告伪装成动作。
- `data/records/range_qualification/`：全部3000条来源范围/规则资格记录。
- `data/records/`：全量CSV/JSONL、场景与生成规则、源组统计、原运行绑定及检查记录。
- `tables/source_augmented_baseline_3000.xlsx`：原9表工作簿，除账户元数据外保留全部单元格、公式和图表原XML；附CSV缓存值和41字段原基线表。

35°通过0/1000，45°通过30/1000，90°通过486/1000，共516个通过配置—样例与2484个失败配置—样例。全部516条几何通过均未满足原来源观察范围/冻结轮廓规则，严格规则合格数为0。几何通过不意味着原任务保持或实机验证。02的5个case来自90°的486条几何通过池。

1000条输入由五个来源生成，不是1000项独立工业任务。三档重复评价也不产生3000项独立任务。所有失败、空白质量字段及未标定标志保留；统计以既定计划分母计算。

All 1000 source-augmented inputs, 3000 baseline results, and 3000 range-qualification records are included. Geometric passes are 0, 30 and 486 at 35°, 45° and 90° respectively. All 516 passing configurations fail the strict source-range/locked-profile qualification. This baseline is separate from later local-repair experiments.

## 数据解释与引用 / Data interpretation and attribution

数据及作者自制资料按本仓库CC BY 4.0许可使用，引用时注明论文作者、仓库版本及所用数据包。既有软件遵循各自许可证。研究数值、关节/速度数组、测量时间和原备注不因隐私清理而更改；公开副本移除账户、个人主目录、私网设备地址和执行审核授权等元数据。原始文件的研究哈希可能记录去标识前的字节，实际公开文件校验以本目录`manifest.csv`为准。私有清理映射不公开。

JSON为历史研究材料；被移除的执行审核记录不得恢复或据此直接下发运动。几何检查通过仅适用于相应模型、场景与预算。VLA训练尚未实施。

`manifest.csv` lists the SHA-256 of each public file. Existing recorded source hashes refer to historical originals; metadata sanitization can change byte hashes while preserving measured values. Private audit mappings are retained separately. These records carry no execution authorization.

工作簿和历史协议中保留的实验相对路径，可用`data_path_index.csv`查到当前包内位置；该索引不含个人主目录。Historical relative file identifiers in preserved workbooks/protocols are mapped to current public locations by `data_path_index.csv`.
