# 07 Fully random trajectories and multi-method offline comparison

[下载07完整数据包](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/07_RandomTrajectoryComparison_v1.0.0.zip) · [下载01–07完整合包](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/SinoGermanRobot-PaperData_v1.0.0_all.zip)

Git仓库目录仅含说明和精选小表；完整压缩包包含下述全部数据路径。下列完整目录结构以下载并解压后的数据包为准。作者自有数据许可为CC BY4.0。

本包提供独立均匀随机1000组输入，以及六种配置的全部6000例最终结果、候选和4347份实际保存的检查点。成功索引只是全量数据的检索入口，不以成功子集替代失败、超时或未观测记录。

## Input and computation scope

输入对应原始`random_actions/0001–1000`。每组10步，每步六轴，共60个角度独立均匀抽取于[-150°,150°]。生成1059组后，仅按24000采样预算保留1000组；没有在输入生成阶段按碰撞通过状态筛选。它不是06包的S1000来源动作变体。

所有试验为离线仿真。记录使用同一当前几何场景，并检查约定零位至首点和全部相邻过渡，不包含重复闭合回程。最大绝对关节角为±175°。方法的修正预算、计算调用量和时间机制并不相等，结果不构成严格等计算预算的算法优越性证明。

| Configuration | Final records | Geometric passes | Actual saved checkpoint files |
| --- | ---: | ---: | ---: |
| M0_90 | 1000 | 0 | 0 |
| M0_180 | 1000 | 5 | 0 |
| M0_360 | 1000 | 0 | 0 |
| M1_180 | 1000 | 0 | 2357 |
| M2_180 | 1000 | 7 | 0 |
| M3_raw_local360 | 1000 | 65 | 1990 |
| Total | 6000 | 77 method/case pairs | 4347 |

77对方法/案例对应72个不同输入编号。M3最高几何通过率为65/1000，即6.5%；所有配置的几何与研究特征联合通过数均为0。独立随机输入不存在可用的来源包络，严格来源保持不适用。仿真几何通过不等于任务、实机或VLA训练合格。

M3记录状态包括65个safe、913个time_budget、21个round_limit和1个witness_unavailable。其上限为30轮和60秒局部搜索预算，时间在轮次边界检查，单例总耗时还可能包含最终复验，因此可能超过60秒。M1实际保存2357份检查点；M3保存1990份，缺失检查点不能当作已经执行后失败。

## Files

| Path | Contents |
| --- | --- |
| `inputs/` | 1000份原始随机输入JSON；无须清理的原件保持原字节 |
| `results/<method>/candidates/` | 每种配置1000份最终候选，包括未通过候选 |
| `results/<method>/records/` | 每种配置1000份完整逐例记录，含失败、超时、轮次、调用量及验证信息 |
| `results/<method>/checkpoints/` | 归档中实际存在的检查点文件；仅M1/M3具有此目录 |
| `tables/case_details.csv` | 6000行逐例比较表 |
| `tables/checkpoint_details.csv` | 计划检查点及其observed/held/early_success状态，不只列有文件的检查点 |
| `tables/method_summary.csv` | 六配置汇总与计时口径 |
| `tables/round_curves.csv` | 轮次状态覆盖、已确认通过及未观测数 |
| `tables/historical_results.csv` | 历史设置的对照摘要，场景标签须保留 |
| `tables/*.xlsx` | 原归档统计工作簿，包含现有图表及跨VI.1–VI.4的汇总；未将原始资料缺项补写为测量值 |
| `evidence/` | 冻结计算条件、输入审核、独立验证和抽查证据JSON；不含算法源码 |
| `figures/` | 与统计表对应的英文汇总图，PNG及PDF |
| `success_index.json`, `success_index.csv` | 77对成功方法/案例的索引，直接指向上述全量目录，无重复成功候选副本 |

`evidence/`中的输入绑定、场景选项、模型指纹、方法范围、并行工作数、时间预算及独立检查记录，可用于核对数据版本和重新统计结果。数据公开不表示完整算法实现已公开，本包没有可直接重跑新增优化器的程序或依赖环境。

## Interpretation and integrity

`observed=true`表示对应状态有归档依据。`held=true`表示提前结束后沿用已有状态，不等同于额外执行了一轮。未观测状态不填作几何失败或成功。5、10、30是比较预算，不是对未知轨迹100%成功所需轮数的预测。

每条结果保留原计数、关节、速度、耗时和历史真假/null标签。对私有路径、网络地址或设备标识进行的清理只发生在公开副本。发布文件均为研究档案，不包含`execution_review`授权对象。`physical_tests_performed=0`等标签按原离线试验含义保留；本包没有实机或VLA训练成绩。

内部原有`*_sha256`绑定历史源版本。隐私清理或JSON序列化可能改变公开字节，因此请以`PUBLIC_FILE_MANIFEST.json`核对实际发布文件。`source-project/...`是原项目的逻辑档案标签；`private-source/...`是未公开的本地来源标识，它们不是可执行路径。以包名开头的路径相对整个数据发布根，其余公开数据路径相对本包。

原ZIP、成功subset副本、缓存/环境和优化脚本均未重复打包。原始文件到公开文件的完整路径及哈希映射由作者私有保存。

## License and attribution

作者自有数据使用[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)许可，包括允许商业使用；使用时请按仓库根目录的引用说明署名并注明修改。第三方引用、资料及软件仍按各自许可处理，数据许可不表示新增优化源码已公开。

