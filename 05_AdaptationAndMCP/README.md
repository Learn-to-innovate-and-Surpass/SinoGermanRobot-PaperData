# 05 适配与MCP资料 / Adaptation and MCP

[完整数据ZIP / Full package](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot-PaperData/releases/download/v1.0.0/05_AdaptationAndMCP_v1.0.0.zip)

Git仓库目录仅包含说明和精选小表；完整压缩包包含下述全部数据路径。The Git directory contains documentation and selected small tables; download the complete archive for all data paths described below.

[中文与English说明](#数据解释与引用--data-interpretation-and-attribution) · [返回数据总览](../README.md)

本目录是方法与接口资料，不是第五组实测实验，不具有样本数或通过率。

- [中文适配指南](guides/README.md)
- [English adaptation guide](guides/README_EN.md)
- [MCP与既有接口说明 / MCP and existing interfaces](MCP_INTERFACES.md)

指南讨论既有公开基础软件的模型适配、坐标约定、资料准备及后续多模态采集。论文01—07数据的公开不表示新增碰撞优化源代码同时公开，也不表示其他机械臂已经完成实机适配。第三方CAD、厂商说明书、SDK与商业软件不随本包再分发；通过原厂/上游来源获取并遵守其授权。

This directory contains adaptation guidance and public-interface pointers, not experimental measurements. The existing public repositories provide their own source and licenses. New collision-optimization code, robot SDKs, commercial software and third-party CAD are not included.

## 数据解释与引用 / Data interpretation and attribution

数据及作者自制资料按本仓库CC BY 4.0许可使用，引用时注明论文作者、仓库版本及所用数据包。既有软件遵循各自许可证。研究数值、关节/速度数组、测量时间和原备注不因隐私清理而更改；公开副本移除账户、个人主目录、私网设备地址和执行审核授权等元数据。原始文件的研究哈希可能记录去标识前的字节，实际公开文件校验以本目录`manifest.csv`为准。私有清理映射不公开。

JSON为历史研究材料；被移除的执行审核记录不得恢复或据此直接下发运动。几何检查通过仅适用于相应模型、场景与预算。VLA训练尚未实施。

`manifest.csv` lists the SHA-256 of each public file. Existing recorded source hashes refer to historical originals; metadata sanitization can change byte hashes while preserving measured values. Private audit mappings are retained separately. These records carry no execution authorization.

工作簿和历史协议中保留的实验相对路径，可用`data_path_index.csv`查到当前包内位置；该索引不含个人主目录。Historical relative file identifiers in preserved workbooks/protocols are mapped to current public locations by `data_path_index.csv`.
