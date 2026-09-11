# 科研工作流与选题规划

围绕计算机、AI 与数据科学，建立从文献和主题输入、选题筛选、研究假设、可复现实验，到论文草稿与投稿准备的工作流。现有计算资源为 RTX 4060 与 H200；各阶段以 A− 档及以上为研究目标，具体档位以所在单位认定为准。

**当前状态：选题准备阶段。已安装 ARIS 科研技能与文献处理环境，未运行研究实验。没有已验证的新颖性、实验提升或录用承诺。**

工具与验证范围见[安装记录](docs/tooling-setup.md)。

**工作流怎样调用：[调用手册](WORKFLOW.md)**，包含技能顺序、可复制提示、输入输出、断点恢复和选题模式限制。

**当前研究核心：多智能体偏好学习。** 已确认做过偏好强化学习和世界模型；当前规划为 A2 偏好反馈查询作为首篇候选、A1 时空信用分配作为后续、B 约束学习条件成熟后拓展、C 多目标适应备选。A2 有条件推进，仍待问题证据与可复用资源确认。

**交给另一个 AI 执行：先读 [HANDOFF.md](HANDOFF.md)，再按[选题阶段执行规划](docs/direction-selection-execution-plan.md)开展阅读、查新和方向比较。** 交付方向决策，不启动训练实验。

## 采用哪些开源项目

- **流程层已安装 [ARIS](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)**：已安装 Codex 适配技能和辅助工具；当前仅使用选题与文献能力，完整流水线尚未验证。
- **离线多智能体备选实验层拟采用 [OG-MARL](https://github.com/instadeepai/og-marl)**：优先复现离线多智能体基线，再实现研究假设；数据格式与版本兼容性需先检查。
- **离线多智能体扩展评估候选 [MangoBench](https://github.com/SYSU-SAIL/mangobench-locomotion)**：在最小实验成立之后评估接入。
- **备选流程 [AutoResearchClaw](https://github.com/aiming-lab/AutoResearchClaw)**：保留作流程对照，首阶段不同时维护两套编排系统。

当前偏好与约束学习主线的实验框架待现有代码、反馈来源和环境明确后再选型。OG-MARL 不再是当前主线的默认框架。奖励机器与表格基础模型保留为备选。

## 文档导航

**最新决策：[方向决策](direction-selection/DECISION.md)与[当前状态](direction-selection/STATUS.md)。**

- [学长学姐视角的实践判断](direction-selection/SENIOR-PEER-ASSESSMENT.md)
- [导师一页讨论稿](direction-selection/MENTOR-ONE-PAGER.md)
- [导师讨论与资源确认清单](direction-selection/MENTOR-DISCUSSION-RESOURCE-CHECKLIST.md)
- [最近邻对照](direction-selection/NEAREST-NEIGHBORS.md)与[证据记录](direction-selection/EVIDENCE.md)

[选题阶段执行规划](docs/direction-selection-execution-plan.md)与[连续研究路线](docs/continuous-research-roadmap.md)保留工作流和衔接背景，方向次序以最新决策为准。

1. [执行规划](docs/plan.md)：阶段、交付物、实验门槛与投稿准备。
2. [候选项目与讨论清单](docs/project-shortlist.md)：早期独立课题备选及必读论文；优先级以连续路线为准。
3. [离线多智能体任务书](docs/offline-marl-brief.md)。
4. [奖励机器任务书](docs/reward-machines-brief.md)。
5. [科研自动化开源项目调研](docs/workflow-survey.md)：主要系统与组件的广泛调研，不代表穷尽全网。
6. [资源讨论记录模板](templates/resource-intake.md)。

下一步索取可复现基线、可解释轨迹与偏好数据、具体协作失败案例，核实主动查询闭环与世界模型的必要性。公开仓库只存可公开的规划和后续研究材料，内部原始选题表与个人联系信息在本地保存。调研时间：2026-09-10。
