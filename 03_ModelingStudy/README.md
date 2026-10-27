# 03 规范与工具组合建模 / Modeling study

[完整数据ZIP / Full package](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/03_ModelingStudy_v1.0.0.zip)

Git仓库目录仅包含说明和精选小表；完整压缩包包含下述全部数据路径。The Git directory contains documentation and selected small tables; download the complete archive for all data paths described below.

[中文与English说明](#数据解释与引用--data-interpretation-and-attribution) · [返回数据总览](../README.md)

本包只公开M01、M41、M47三项原始实填测量，同时公开50项共同提示词作为任务设计。原工作簿另47条“随机补齐（非实测）”的提示次数和耗时已从公开副本全部排除，不能用于实验统计；对应任务文本仍在设计表中，测量可用标志为false。

## 内容 / Contents

- `tables/modeling_study_public.xlsx`：由真实3项测量和50任务设计重新整理的工作簿，含可编辑汇总公式；不复制含人工补值的原表。
- `tables/measured_records_3.csv`和`.json`：真实3项，原值3/13/1/5、4/14/1/5.5、3/17/1/4.5（提示次数/分钟按列）。
- `tables/task_design_50.csv`和`.json`：50条任务编号、名称和原提示词；没有47条人工随机测量值。
- `model_previews/`：M01板件、M41放样体、M47双销装配三张自制模型预览，像素和文件原字节保持。
- `model_records/M47_verification.json`：已有几何/装配信息记录，经路径去标识；不作为独立盲评或所有尺寸已实测的证明。
- `protocol/`：原设计时点的比较与人工提示计数规则。实际结果范围以上述三条为准。

原生IPT/IAM和带软件界面的计时截图暂未分发：原件保留在作者私有档案，需单独处理嵌入路径和账户元数据；本包已保留精确任务参数及纯模型图。三项模型来自本研究指定的简单几何任务，不包含厂家机器人CAD。

配置组同时使用任务规则与InventorBridge接口，对照组不提供该组合，因此测量描述组合条件差异。三项累计提示10→3，耗时44→15 min；这不是50项完成实验、几何质量盲评或单一提示词机制的因果证明。现有接口及安装说明请查阅[InventorBridge](https://github.com/Learn-to-innovate-and-Surpass/InventorBridge)，本数据包不复制软件、许可证、账号配置或新碰撞优化实现。

Only three measured tasks are released as observations. All 50 prompts remain available as designs. Forty-seven artificial fill rows are excluded entirely from measurement tables. Native CAD files and UI screenshots are retained privately pending metadata review; task parameters and three unchanged original previews are supplied.

## 数据解释与引用 / Data interpretation and attribution

数据及作者自制资料按本仓库CC BY 4.0许可使用，引用时注明论文作者、仓库版本及所用数据包。既有软件遵循各自许可证。研究数值、关节/速度数组、测量时间和原备注不因隐私清理而更改；公开副本移除账户、个人主目录、私网设备地址和执行审核授权等元数据。原始文件的研究哈希可能记录去标识前的字节，实际公开文件校验以本目录`manifest.csv`为准。私有清理映射不公开。

JSON为历史研究材料；被移除的执行审核记录不得恢复或据此直接下发运动。几何检查通过仅适用于相应模型、场景与预算。VLA训练尚未实施。

`manifest.csv` lists the SHA-256 of each public file. Existing recorded source hashes refer to historical originals; metadata sanitization can change byte hashes while preserving measured values. Private audit mappings are retained separately. These records carry no execution authorization.

工作簿和历史协议中保留的实验相对路径，可用`data_path_index.csv`查到当前包内位置；该索引不含个人主目录。Historical relative file identifiers in preserved workbooks/protocols are mapped to current public locations by `data_path_index.csv`.
