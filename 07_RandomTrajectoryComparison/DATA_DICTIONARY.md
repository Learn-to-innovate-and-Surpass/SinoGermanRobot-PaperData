# Data dictionary for package 07

## Input and candidate JSON

| Field | Definition |
| --- | --- |
| `case_id` | 四位原始输入编号0001–1000；按文本读取以保留前导0 |
| `method`, `method_id` | 逻辑方法/实际实现配置；M3实现名称可带cached，不能与不同场景实验混为同一次运行 |
| `document.waypoints[].joint` or `waypoints[].joint` | 10×6关节角数组，弧度；J1–J6顺序 |
| `pos`, `ori` | 原保存位置与WXYZ四元数；相关坐标和几何版本见contract/scene |
| `speed.joint_maxvelc`, `speed.joint_maxacc` | 原文件六轴速度rad/s和加速度rad/s²参数，不代表实测值或厂商极限 |
| `geometric_proxy_safe`, `geometric_pass` | 指定场景完整离线路径的几何通过标签 |
| `research_feature_pass`, `feature_pass` | 几何与研究动作特征联合通过；仅特征内部阈值通过不等于此联合通过 |
| `strict_S`, `strict_S_pass`, `strict_S_success` | 按各历史schema原值保存；独立随机输入没有来源包络，须结合source_rule_applicable=false解释 |
| `task_success`, `VLA_qualified` | 未验证时为null或原历史值，不能推断为实测训练/任务通过 |
| `physical_tests_performed` | 本包为0；不借用06样本的实测结果 |
| `input_sha256`, `contract_sha256`, `*_document_sha256` | 原始档案的版本绑定，不自动改成清理后文件哈希 |

## Per-case records and CSV

| Field | Definition and unit |
| --- | --- |
| `status` | 归档的终止状态，如safe/success、search_failed、stalled、round_limit、time_budget、witness_unavailable |
| `actual_rounds`, `actual_attempted_rounds`, `actual_round` | 相应schema记录的实际轮次；不得把预设预算当成实际执行次数 |
| `first_success_round` | 首次完整路径通过的轮次，未成功或未记录时保持空/null |
| `elapsed_s`, `search_wall_s`, `elapsed_case_s` | 不同实现的记录时间，秒；含义以具体字段与cost_note为准 |
| `new_search_stage_s`, `baseline_attributed_search_s` | 本阶段新增搜索耗时与归属既有阶段的耗时，分开记录 |
| `geometry_calls_executed`, `geometry_calls_search_executed` | 实际执行的几何调用数 |
| `geometry_calls_logical`, `geometry_calls_search_logical` | 包括缓存复用所对应的逻辑调用数，不能当作实际CPU工作量 |
| `geometry_calls_attributed`, `baseline_attributed_geometry_calls` | 归属于复用阶段的调用统计，不能再次相加造成重复计数 |
| `time_budget_exhausted` | 达到局部搜索时间限制；最终检查及序列化时间可能另计 |
| `max_delta_deg`, `rms_delta_deg` | 候选相对原始输入的角度改变量，度 |
| `max_absolute_joint_deg` | 输出最大绝对关节角，度 |
| `relative_increment_error` | 相邻关节增量误差比，不是机器人末端定位误差 |
| `edited_waypoints`, `edited_joint_cells` | 被修改的点数和关节单元数 |
| `J6_max_delta_deg`, `j6_preserved` | 第六关节改变及保持情况；以原文件逐点比较定义 |
| `research_feature_gate` | 研究特征条件记录；不是实机资格或最终联合通过率 |
| `candidate_sampling_budget_rejected`, `search_sampling_budget_rejected` | 采样预算触发情况，与碰撞失败分开 |

## Checkpoint table

`budget`是比较预算；`applicable`指该配置是否适用。`observed`表示有记录状态，`held`表示沿用已终止状态，`early_success`表示提前成功。`actual_round`保留已执行轮次。`checkpoint_file`为空表示没有该文件，不能用最终状态伪造一个缺失检查点。

`round_curves.csv`中的`confirmed_pass_rate_lower_bound`以全部计划1000条为分母，未观测轨迹不计为已确认成功；它是固定批次在存在未观测状态时的已确认比例下界，不是统计置信区间下限。`state_coverage_rate`描述状态覆盖，不能替代通过率。缺失值不是0。

## Pointer and hash conventions

`success_index`中的`candidate_public_sha256`和`record_public_sha256`核对公开文件字节；其`input_sha256`保留输入来源证据。完整发布文件清单以`PUBLIC_FILE_MANIFEST.json`为准。内部历史路径可能是已去除个人前缀的来源标签，实际阅读入口见本包README与公开索引。

