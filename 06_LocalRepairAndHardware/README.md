# 06 Local trajectory repair and recorded hardware sample

[下载06完整数据包](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/06_LocalRepairAndHardware_v1.0.0.zip) · [下载01–07完整合包](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/SinoGermanRobot-PaperData_v1.0.0_all.zip)

Git仓库目录仅含说明和精选小表；完整压缩包包含下述全部数据路径。下列完整目录结构以下载并解压后的数据包为准。作者自有数据许可为CC BY4.0。

本包发布S系列1000条输入、适配当前网页场景的1000条候选，以及10条已有现场抽样的动作数据和结构化记录。它不是独立均匀随机1000组；后者位于07包。`historical_studies/`另提供论文VI.1–VI.3的冻结研究记录、历史候选、预算检查点、A/B新变体及数值拟合参数，明确区别于当前网页迁移版本。

查找论文结果可先阅读[历史研究索引](historical_studies/README.md)、[24行关键统计表](historical_studies/summary.csv)及[分阶段数据目录](historical_studies/DATASET_CATALOG.json)。历史随机和S1000原输入通过`input_index.csv`链接01/04包；新增的A200、B200输入共400份位于历史研究目录，避免重复复制共享输入。

## Data and scope

| Directory or file | Contents |
| --- | --- |
| `inputs/` | S-0001–S-1000，五个来源动作各200个有界变体，共1000份输入JSON |
| `candidates/` | WS-0001–WS-1000，当前网页模型/场景下检查的1000份候选JSON |
| `metadata/population_and_sampling.json` | 全部1000例的来源、排序、修正与审核历史，以及10条分层抽样信息 |
| `metadata/scene.json` | 用于本包网页复核的场景、坐标约定和模型版本；仅为研究配置记录 |
| `metadata/current_web_recheck.json` | 归档的当前场景全量/抽样复核状态与证据绑定 |
| `hardware/selection_index.json` | 10条样本指向完整输入、候选及现场保存动作文件的索引 |
| `hardware/actions/` | 现场保存的10份动作文件的研究用副本；执行审核记录已移除 |
| `hardware/summary.json` | 已有现场结果、分母、重试口径与证据冲突的结构化转录 |
| `hardware/operator_notes.json` | 两条异常案例的原备注文字与未确诊状态 |
| `hardware/offline_revalidation.json` | 对既有现场保存文件进行的离线几何复核；不是另一次实机试验 |
| `historical_studies/` | VI.1–VI.3完整选定研究批次的逐例数据、候选、检查点、条件、数值拟合参数及验收记录 |

S系列源动作经插值与有界扰动形成相关变体。1000个文件不代表1000种独立工业任务。当前网页适配候选与VI.3冻结研究输出是不同版本，不能把其场景、参数或通过状态混合统计。来源字段和历史哈希保留这种区分。

## Recorded results

当前网页复核记录为1000/1000条几何通过。几何检查只对应归档的模型与场景，既不等于任务保持，也不等于全部轨迹通过实机验证。

现场抽样采用原输入总关节变化量L的秩正态分位划分：十层、每层100条、每层抽一条，种子20261024。每条候选的纳入概率为1%。这种分层表示不证明原始动作服从正态分布。

已有10条现场样本共计划100个不重复小步，包含重试后的完成数为99，完整轨迹完成数为9/10。99%是计划小步完成比例，90%是完整轨迹比例。它们不是首次执行通过率，不能用于宣称1000条轨迹全部成功。现有资料不足以计算所有尝试的成功率。

- WS-0098记录完成9步。原备注将原因描述为第9至10步转角超过175°；保存文件的最大相邻关节变化为128.33286683038608°，界面历史记录另提示玻璃禁区及软件停止错误。原因存在冲突，保持未确认。
- WS-0265首次报警后重试成功，已计入99个完成小步。传感器问题只是操作者怀疑，未作故障诊断。
- 原截图保留于作者私有证据档案，未在此发布，以避免暴露网络地址、个人信息或工作站细节。公开的是既有记录的结构化转录，不是假定获得了完整原始控制器日志。

## Public derivatives and integrity

本包是研究档案，不授予任何机械臂执行资格。所有现场动作副本中的`execution_review`均已删除；关节数组、速度、位置、姿态、计数和历史结果未改动。JSON中的历史`execution_review_present`等字段描述原始档案状态，不表示公开副本仍带执行授权。实际应用需在使用者自己的模型、场景与设备条件下重新审核。

个人绝对路径、私有网络地址和设备标识从公开副本中清理。`source-project/...`表示原项目中的逻辑档案位置；`private-source/...`表示未随本包发布的本地来源。它们不是可执行路径或本包内文件承诺。`PUBLIC_FILE_MANIFEST.json`给出发布字节的哈希；数据内部原有`*_sha256`仍绑定历史源版本，两者可不同。完整原件到公开副本的路径、哈希和清理记录保留在私有审计中。

本包不附新增碰撞优化实现、拟合脚本、Python环境、凭据或可直接控制硬件的程序。场景JSON是记录计算条件的数据，不是执行脚本。原动作中沿用的生成时间说明或“尚未实测”备注保留其历史含义，后续现场结果另列于`hardware/summary.json`。

## License and attribution

作者自有数据按[Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/)许可发布，允许在适当署名和注明修改的条件下使用，包括商业用途。署名信息以仓库根目录的引用说明为准。第三方资料、软件和引用仍适用各自许可，本包不重新许可第三方内容。

