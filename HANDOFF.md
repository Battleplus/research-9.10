# 给执行 AI 的任务

调用入口：先读 [WORKFLOW.md](WORKFLOW.md)，其中定义技能顺序、逐步提示、输入输出、失败处理及阶段停止条件。

请接手本仓库的选题规划。目标是在 A− 档及以上成果目标下，结合研究连续性、难度与就业，推荐一个主课题、一个关联副课题及后续路线。当前只定方向，没有开始具体研究实验。

先读 `AGENTS.md`、`docs/direction-selection-execution-plan.md`、`docs/continuous-research-roadmap.md`、`docs/tooling-setup.md`，以最新明确要求为准。请实际完成规划中的资料阅读、查新、代码静态分析、候选比较和反向审查，不只复述一个计划。

背景：我已经做过偏好强化学习和世界模型，有 RTX 4060 和 H200。具体实现与实验成绩尚未核对，不能虚构我的水平或已有成果。请优先比较“偏好学习与世界模型”“偏好学习与约束”“偏好学习与多目标适应”三条连续路线，允许基于证据改变顺序。不要只对孤立课题排名，也不要强行把所有方法堆到一起。

我提供了四篇论文：Christiano 的 Deep Reinforcement Learning from Human Preferences、AAAI 2024 的 MAPT、Kaufmann 的 RLHF 综述、Zhong 的奖励模型综述。版本和链接在执行规划内。先区分直接相关方法与背景材料，再补查最新工作。MAPT 官方仓库是 https://github.com/catezi/MAPT 。重点核查脚本教师偏好、奖励训练与策略交互的区别，以及时间和协作依赖已经被研究的事实。

本机仓库路径为 `E:\工作流\research-9.10`；四篇 PDF 位于本机 `literature/`，不会随 Git 克隆下载。MAPT 源码位于 `E:\工作流\科研工作流调研-2026-09-10\paper-reading\MAPT`。若在另一台机器上工作，使用公开论文和官方仓库；不能访问私有资料时标记缺失，继续不依赖它的工作。

本机已装 ARIS Codex 技能和独立 Python 环境。可以使用 research-lit、novelty-check、idea-creator、research-review、research-wiki；其他环境可按相同方法执行，不要假装工具已经安装。arXiv 和 OpenAlex 曾通过测试，Semantic Scholar 曾限流，使用时重新确认。没有跨模型服务时如实标注自查，不伪造独立评审。

限制：仅阅读、网络检索、静态代码检查、写笔记和方案。不要安装具体训练框架，不运行 pilot／GPU 训练，不连接远程 GPU、不租算力、不投稿、不联系他人。ARIS 的默认自动继续不能覆盖这些限制。使用 idea-discovery 时明确跳过实验。不要上传 PDF、原始选题表、个人联系信息、未发表资料或凭据。

请交付 `direction-selection/EVIDENCE.md`、`OPTIONS.md`、`DECISION.md`、`STATUS.md`，并同步关键资料到 Research Wiki。主推荐必须说明最接近工作、研究差异的证据与不确定性、能复用哪些积累、未来怎样证伪、目标 venue 的适配与差距、以及就业能力如何积累。不要承诺录用或把未经实验的想法称为已验证创新。

必要澄清集中为不超过五个关键问题，同时完成独立工作。完成后停止在方向决策阶段，汇报成果路径和仍缺的资料，等待我确定方向。研究结果可以在本地形成可审查提交；本交接不额外授权向 GitHub 推送执行阶段的新结果。
