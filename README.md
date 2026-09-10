# 科研工作流与选题规划

围绕计算机、AI 与数据科学，建立从文献和主题输入、选题筛选、研究假设、可复现实验，到论文草稿与投稿准备的工作流。现有计算资源为 RTX 4060 与 H200；首篇研究以 A−／A 为目标，具体档位以所在单位认定为准。

**当前状态：规划与选题阶段。尚未安装科研代理或运行研究实验，没有已验证的新颖性、实验提升或录用承诺。**

## 采用哪些开源项目

- **流程层拟采用 [ARIS](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)**：作为研究流程组织的参考和接入起点，实际执行能力需安装后验证。
- **主线实验层拟采用 [OG-MARL](https://github.com/instadeepai/og-marl)**：优先复现离线多智能体基线，再实现研究假设；数据格式与版本兼容性需先检查。
- **扩展评估候选 [MangoBench](https://github.com/SYSU-SAIL/mangobench-locomotion)**：在最小实验成立之后评估接入。
- **备选流程 [AutoResearchClaw](https://github.com/aiming-lab/AutoResearchClaw)**：保留作流程对照，首阶段不同时维护两套编排系统。

奖励机器、表格基础模型是候选研究方向，各有自己的实验代码；并非把所有框架同时装入一个项目。

## 文档导航

1. [执行规划](docs/plan.md)：阶段、交付物、实验门槛与投稿准备。
2. [候选项目与讨论清单](docs/project-shortlist.md)：三个优先方向、两个备选及必读论文。
3. [离线多智能体任务书](docs/offline-marl-brief.md)。
4. [奖励机器任务书](docs/reward-machines-brief.md)。
5. [科研自动化开源项目调研](docs/workflow-survey.md)：主要系统与组件的广泛调研，不代表穷尽全网。
6. [资源讨论记录模板](templates/resource-intake.md)。

下一步先收集候选方向的核心论文、可运行代码与已有实验，再据此确定主线。公开仓库只存可公开的规划和后续研究材料，内部原始选题表与个人联系信息在本地保存。调研时间：2026-09-10。
