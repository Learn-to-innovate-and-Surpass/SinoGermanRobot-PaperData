# MCP与既有接口 / MCP and existing interfaces

## 既有公开项目

- [SinoGermanRobot](https://github.com/Learn-to-innovate-and-Surpass/SinoGermanRobot)：网页仿真、动作文件审核、独立执行基础界面与模型适配指南。
- [InventorBridge](https://github.com/Learn-to-innovate-and-Surpass/InventorBridge)：通过MCP向客户端提供Inventor本地建模接口，包含安装、依赖和工具使用说明。

MCP负责客户端与工具接口之间的结构化调用。InventorBridge由独立工作进程调用Inventor COM API，提供参数化板件与固定模板概念装配、几何信息检查及模型预览等操作。安装Inventor及其商业许可由复现者自行负责，本数据包不分发软件或授权文件。

03记录的比较条件同时改变任务约定与接口可用性。旧“技能包”是规则与工具资源组合，不是50种任务均已具有现成一键接口的证据，也不等同于单独改变提示词。复现者需记录所用公开仓库版本、依赖、工具列表及同一任务的实际调用与人工消息。

建议先在独立副本完成只读连接/工具发现、指定目录中的小型测试建模、原生文件与预览核验，再用于已列出的任务设计。具体工具名称和参数以选定版本的仓库文档与服务端工具清单为准。机器人实机适配是独立环节，MCP建模接口不赋予机器人执行授权。

## English

The two existing repositories provide the public foundation system and the Inventor MCP bridge. MCP supplies a structured client–tool interface; Inventor modeling uses an isolated COM worker. Record the repository version, dependencies, available tool schemas and actual interaction counts when reproducing the three-task study. The configuration comparison changes both task rules and tool access. No claim of 50 completed tasks or universal one-click modeling is made.

This data release includes no new collision-optimization implementation, robot SDK, Inventor installer, account configuration or software license file. Obtain third-party resources from their original authorized sources.
