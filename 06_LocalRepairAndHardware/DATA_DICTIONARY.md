# Data dictionary for package 06

| Field or object | Meaning and unit |
| --- | --- |
| `action_id` | 原动作标识；文件名WS表示当前网页候选，内部action_id可保持S编号 |
| `waypoints` | 按执行顺序排列的动作点；每条10点 |
| `waypoints[].joint` | J1–J6关节角，弧度；不得当作角度值直接读取 |
| `waypoints[].pos` | 保存的笛卡尔位置，米；来源和坐标约定须结合场景记录 |
| `waypoints[].ori` | WXYZ顺序四元数 |
| `speed.joint_maxvelc` | 原动作文件六轴速度参数，rad/s；保留原值 |
| `speed.joint_maxacc` | 原动作文件六轴加速度参数，rad/s²；不宣称为厂商最大加速度 |
| `s_series_generation` | 来源动作、扰动种子、来源观察包络、冻结关节等生成条件 |
| `raw_L_deg` | 从约定零位到原始10点，六轴绝对关节变化总和，度；不取模 |
| `rank`, `u`, `z`, `stratum` | L排序名次、分位、逆正态分位表示和抽样层；不是正态分布验证 |
| `current_web_default_geometry_passed` | 对归档当前网页几何条件的通过记录 |
| `historical_*` | 冻结研究版本的历史状态，与当前网页适配文件分开解释 |
| `model_revision`, `*_sha256` | 版本/证据绑定；内部哈希保留历史原件定义 |
| `planned_unique_steps` | 每条轨迹计划的不重复小步数，通常10 |
| `completed_unique_steps` | 包含已报告重试后完成的不重复计划小步数；重试不重复增加成功分子 |
| `complete_trajectory` | 全部计划小步是否完成 |
| `retry_reported` | 现有记录是否明确提到重试；false不证明从未发生未记录重试 |
| `first_pass_steps`, `actual_attempt_count` | 原始资料缺失时为null，不用0填补 |
| `cause_status`, `cause_confirmed` | 对备注原因的证据状态；操作者怀疑与确诊分开 |
| `physical_calls`, `new_execution_reviews` | 离线复核时实际物理调用和新增授权数，均为0 |

文件内部的真假/null标签按原历史语义保留。缺失值代表资料不足，不代表失败或零耗时。公开副本不含`execution_review`授权对象；发布文件哈希查`PUBLIC_FILE_MANIFEST.json`。

## Historical studies VI.1–VI.3

`historical_studies/`保留阶段当时的字段命名，不把不同场景强行合并为同一schema。VI.1的`checkpoints`包含baseline或5/10/30预算，其`geometric_success`是完整路径几何结果；VI.2的`success`、`union_success`分别对应冻结分级搜索和保留旧通过的事后并集。VI.3的`geometric_pass`、`research_feature_pass`、`strict_S_pass`分别记录三类验收，不能用一个布尔值替代。

`regression_A200`对应源码档案中的`inputs/fresh200`，为拟合偏置试验的新同源变体；`local_B200`对应`inputs/fresh200_local`，为局部策略冻结后生成的新同源变体。两者各200条，不合并为一个测试集，也不称为400项新工业任务。实际编号以各自manifest为准。

`input_index.csv`给出2400行输入索引（1000随机、1000历史S、200 A、200 B）。`public_path`相对整个数据发布根；`source_sha256`为原档案字节哈希，`public_sha256`为脱敏后发布字节哈希。历史gzip候选已展开为JSON，原`candidate_gzip_sha256`继续表示压缩原件，发布JSON哈希查总清单。

`VI3/model_data/fitted_offsets.json`是回归系数、特征中心、开发样本标签、原型、试验结果和公式说明的数值研究记录。它不包含训练、推理、控制或优化执行程序。逐次二次拟合系数、预测偏置与测量损失同样作为实验记录保留，所有原数值/真假/null/数组内容保持不变。源码、冻结源码副本、环境和编译缓存未发布。


