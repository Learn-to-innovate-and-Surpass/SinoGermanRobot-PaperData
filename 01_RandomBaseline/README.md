# 01 完全随机轨迹旧基线 / Independent-random baseline

[完整数据ZIP / Full package](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/01_RandomBaseline_v1.0.0.zip)

Git仓库目录仅包含说明和精选小表；完整压缩包包含下述全部数据路径。The Git directory contains documentation and selected small tables; download the complete archive for all data paths described below.

[中文与English说明](#数据解释与引用--data-interpretation-and-attribution) · [返回数据总览](../README.md)

本包提供全部1000个原输入与35°、40°、90°三档各1000个失败诊断，另含30条分层复核及操作者保留的派生动作。每条原输入10步、每步6轴，60角度独立均匀取自[−150°,150°]，仅按24000路径采样预算筛选；从1059个候选中保留1000条。它与04的来源增强S系列不同。

## 内容 / Contents

- `data/inputs/`：1000条原输入，关节弧度、WXYZ姿态、速度和生成种子保留。
- `data/results/deg35/`、`deg40/`、`deg90/`：3000条完整失败诊断，包含未提交修改及其几何检查；所有档位整轨迹几何通过均为0/1000。
- `data/records/`：全量CSV/JSONL、场景选项、生成及运行绑定、计时定义与已有控制检查。运行源代码只保留来源名称/哈希，不附算法实现。
- `sample_review/`：固定种子20261016的30条分层抽样信息，以及从失败记录恢复的30个未提交候选。11个候选有23步关节修改，19个候选关节未改变；30条离线复验仍全部未通过。
- `manual_reconstructions/`：0224、0715、0878的操作者派生JSON，和原十步输入分开。0224六步重构的完成记录不计为原十步自动修正成功。
- `tables/`：原工作簿的单元格、公式与图表保持不变，仅移除私有文档账户信息；附CSV缓存值供读取。
- `protocol/`：历史设计说明，日期和当时的“待填”含义保留；实际后续30条备注以公开表格为准。

30条排查中的“未通过”和备注同时含仿真观察、人工修订和现场异常，不能统计成30次真实机器人运动失败。备注中“扭矩不合理”等是操作者原文，不是力矩测量或确定故障诊断。原始界面截图留在私有证据档案，公开数据不因截图暂未发布而改写结论。

The release includes all 1000 inputs and all 3000 unsuccessful baseline diagnostics, not a success-selected subset. The 30-case review retains operator notes and manual reconstructions separately. Geometric outcomes are model/scene-specific; no VLA training or population-level robot safety result is implied.

## 数据解释与引用 / Data interpretation and attribution

数据及作者自制资料按本仓库CC BY 4.0许可使用，引用时注明论文作者、仓库版本及所用数据包。既有软件遵循各自许可证。研究数值、关节/速度数组、测量时间和原备注不因隐私清理而更改；公开副本移除账户、个人主目录、私网设备地址和执行审核授权等元数据。原始文件的研究哈希可能记录去标识前的字节，实际公开文件校验以本目录`manifest.csv`为准。私有清理映射不公开。

JSON为历史研究材料；被移除的执行审核记录不得恢复或据此直接下发运动。几何检查通过仅适用于相应模型、场景与预算。VLA训练尚未实施。

`manifest.csv` lists the SHA-256 of each public file. Existing recorded source hashes refer to historical originals; metadata sanitization can change byte hashes while preserving measured values. Private audit mappings are retained separately. These records carry no execution authorization.

工作簿和历史协议中保留的实验相对路径，可用`data_path_index.csv`查到当前包内位置；该索引不含个人主目录。Historical relative file identifiers in preserved workbooks/protocols are mapped to current public locations by `data_path_index.csv`.
