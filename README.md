# 科研工作流与选题规划

围绕计算机、AI 与数据科学，建立从文献和主题输入、选题筛选、研究假设、可复现实验，到论文草稿与投稿准备的工作流。现有计算资源为 RTX 4060 与 H200；各阶段以 A− 档及以上为研究目标，具体档位以所在单位认定为准。

**当前状态：选题准备阶段。已安装 ARIS 科研技能与文献处理环境，未运行研究实验。没有已验证的新颖性、实验提升或录用承诺。**

工具与验证范围见[安装记录](docs/tooling-setup.md)。

**当前优先路线：[偏好强化学习 → 约束强化学习 → 世界模型](docs/continuous-research-roadmap.md)。** 以课题连续性、资产复用和就业技能积累安排主副课题；尚待个人已有积累、指导和实验资源确认。

## 采用哪些开源项目

- **流程层已安装 [ARIS](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)**：已安装 Codex 适配技能和辅助工具；当前仅使用选题与文献能力，完整流水线尚未验证。
- **离线多智能体备选实验层拟采用 [OG-MARL](https://github.com/instadeepai/og-marl)**：优先复现离线多智能体基线，再实现研究假设；数据格式与版本兼容性需先检查。
- **离线多智能体扩展评估候选 [MangoBench](https://github.com/SYSU-SAIL/mangobench-locomotion)**：在最小实验成立之后评估接入。
- **备选流程 [AutoResearchClaw](https://github.com/aiming-lab/AutoResearchClaw)**：保留作流程对照，首阶段不同时维护两套编排系统。

当前偏好与约束学习主线的实验框架待现有代码、反馈来源和环境明确后再选型。OG-MARL 不再是当前主线的默认框架。奖励机器与表格基础模型保留为备选。

## 文档导航

**先读：[连续研究路线](docs/continuous-research-roadmap.md)，这是当前决策依据。**

1. [执行规划](docs/plan.md)：阶段、交付物、实验门槛与投稿准备。
2. [候选项目与讨论清单](docs/project-shortlist.md)：早期独立课题备选及必读论文；优先级以连续路线为准。
3. [离线多智能体任务书](docs/offline-marl-brief.md)。
4. [奖励机器任务书](docs/reward-machines-brief.md)。
5. [科研自动化开源项目调研](docs/workflow-survey.md)：主要系统与组件的广泛调研，不代表穷尽全网。
6. [资源讨论记录模板](templates/resource-intake.md)。

下一步整理个人项目积累，并确认偏好与约束课题的共享代码、数据和指导，确定第一阶段的独立研究问题。公开仓库只存可公开的规划和后续研究材料，内部原始选题表与个人联系信息在本地保存。调研时间：2026-09-10。
