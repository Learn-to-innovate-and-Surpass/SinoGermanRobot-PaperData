# SinoGermanRobot 论文数据

[English](README.md) · [公开范围](DATA_SCOPE.md) · [引用信息](CITATION.cff) · [许可](LICENSE)

本仓库整理任皓琛、刘春平论文《面向VLA数据准备的工业机械臂可视化建模与碰撞引导轨迹修正》的研究记录。版本 **v1.0.0**，发布日期 **2026-10-28**。

内容包括轨迹原输入、离线几何检查、通过与失败候选、小样本工程比较及已有现场抽样记录。**它不是可直接训练的完整VLA数据集**，未提供完整同步多模态回合或VLA训练成绩。

## 下载方式

Git仓库仅保存说明、精选小型CSV/XLSX和校验索引；**全量数据通过Release压缩附件提供**。下方目录链接用于阅读指南及小表，不表示Git目录已包含其中说明的全部原始数据路径。GitHub自动生成的“Source code”压缩包也只含仓库正文。

- [打开v1.0.0发布页](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/tag/v1.0.0)
- [下载01—07合并完整包](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/SinoGermanRobot-PaperData_v1.0.0_all.zip)
- [包索引](PACKAGE_INDEX.csv)与[压缩附件SHA-256](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/SHA256SUMS)

| 目录说明与精选表格 | 数据内容 | 完整分包 |
| --- | --- | --- |
| [01_RandomBaseline](01_RandomBaseline/) | 1000条输入、全部3000条旧基线失败诊断及30条人工复核。 | [完整ZIP](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/01_RandomBaseline_v1.0.0.zip) |
| [02_ProgrammingEfficiency](02_ProgrammingEfficiency/) | 5个case、10行计时；不完整配对和原备注保留。 | [完整ZIP](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/02_ProgrammingEfficiency_v1.0.0.zip) |
| [03_ModelingStudy](03_ModelingStudy/) | 3项真实测量、50项任务设计；47条人工随机补值不进入测量表。 | [完整ZIP](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/03_ModelingStudy_v1.0.0.zip) |
| [04_SourceAugmentedBaseline](04_SourceAugmentedBaseline/) | 五来源共1000条S输入，全部3000条旧基线结果及来源范围检查。 | [完整ZIP](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/04_SourceAugmentedBaseline_v1.0.0.zip) |
| [05_AdaptationAndMCP](05_AdaptationAndMCP/) | 模型适配指南及既有接口链接；不是独立实测组。 | [完整ZIP](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/05_AdaptationAndMCP_v1.0.0.zip) |
| [06_LocalRepairAndHardware](06_LocalRepairAndHardware/) | VI.1—VI.3历史研究数据、当前网页S1000候选及10条已有现场样本。 | [完整ZIP](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/06_LocalRepairAndHardware_v1.0.0.zip) |
| [07_RandomTrajectoryComparison](07_RandomTrajectoryComparison/) | 1000条完全随机输入，6000例最终结果、4347检查点、77个通过方法/案例对。 | [完整ZIP](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/07_RandomTrajectoryComparison_v1.0.0.zip) |

下载后以`SHA256SUMS`核对压缩包字节。完整分包中，01—05使用`manifest.csv`记录逐文件公开哈希，06—07使用`PUBLIC_FILE_MANIFEST.json`。精确大小及附件信息以`PACKAGE_INDEX.csv`和发布页清单为准。

## 结果应如何理解

![按数据集和场景划分的方法比较](figures/method_comparison.png)

图左为来源增强S1000的历史实验，图右为当前场景的独立随机输入。历史S1000最终配置的几何通过率为100%，几何与研究特征联合通过率为40%，严格来源保持通过率为0%；当前完全随机1000组最高为65/1000，即6.5%。两组数据的来源、场景及搜索成本不同，不能合并成“同一随机1000组从0%提高至100%”的结论。

已有10条分层现场样本共计划100个不重复小步，**包含重试后完成99步，完整轨迹为9/10条**。首次通过率及全部尝试通过率因记录不足而未知，不能据此宣布1000条轨迹均能完成或给出总体安全保证。

所有失败、超时和未观测状态保留。检查点`held`表示沿用已知状态，不是又执行了一轮；缺失值不补成零、通过或失败。各包数据字典分别定义几何、研究特征、来源保持及现场记录口径。

## 复查与代码范围

数据可用于复核计数、重算汇总、追踪逐例结果和检查已保存的场景/参数。VI.3历史数据包含已保存的数值模型系数。**新增碰撞优化源代码及其运行环境不公开**，因此本仓库不承诺提供重跑全部优化器的完整程序。

既有基础项目仍分别发布：

| 软件 | 发布时参考快照 | 用途 |
| --- | --- | --- |
| [SinoGermanRobot](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot) | [`becefb26f2d5c9d4ad79d2e7ae50a046dbae47fd`](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot/tree/becefb26f2d5c9d4ad79d2e7ae50a046dbae47fd) | 基础仿真、文件审核与执行界面 |
| [InventorBridge](https://github.com/Learn-to-innovate-and-Surpass/InventorBridge) | [`0495e040775f2e273115498058d3ece01cbe5972`](https://github.com/Learn-to-innovate-and-Surpass/InventorBridge/tree/0495e040775f2e273115498058d3ece01cbe5972) | 本地CAD建模接口 |

上述是发布时的公开参考快照，**不是论文实验冻结版本的替代品**。具体实验版本应查看各包contract及历史哈希。

[InventorBridge架构说明](https://github.com/Learn-to-innovate-and-Surpass/InventorBridge/blob/0495e040775f2e273115498058d3ece01cbe5972/README.md)采用“MCP客户端—本地stdio MCP服务—独立COM工作进程—已授权Inventor”的流程。它让客户端调用结构化建模和检查操作；机器人执行资格仍由独立审核条件决定。详见[05适配与MCP资料](05_AdaptationAndMCP/)。本数据仓库不打包第三方软件、机械臂SDK或商业许可证。

## 去标识与署名

公开副本清除了个人主目录、私网设备地址、设备标识、账户元数据及18个历史执行审核授权对象。研究数值、关节与速度数组、记录时间及结果标签保留。数据中的历史哈希仍对应原档，去标识后的公开文件哈希以发布清单为准；完整私有清理映射不公开。

原始界面截图和含个人路径的原生CAD保留在作者本地证据档案；公开包提供任务参数、精选原像素模型预览和结构化记录。详细范围见[DATA_SCOPE.md](DATA_SCOPE.md)。

作者自有的数据、文档和图表采用**CC BY 4.0**许可，允许按许可署名、注明修改后使用。既有软件及第三方材料仍遵循各自许可证，数据许可不包含未公开优化源码或第三方软件。

建议引用：任皓琛，刘春平. SinoGermanRobot Paper Data（版本1.0.0）[数据集]. GitHub，2026. https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData

机器可读信息见[CITATION.cff](CITATION.cff)。请同时注明所用发布版本、数据包及case编号。
