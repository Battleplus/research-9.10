# 候选项目筛选与论文资源讨论清单

## 建议先谈三个方向

排序是当前资源信息下的判断，不是对新颖性或成果档位的认证。优先选择能获得可复现代码、已有实验与持续指导的方向。H200 支持扩大实验，但不会自动解决研究问题不明确或数据不可得的问题。

| 顺序 | 原有主题 | 建议收窄的问题 | 难度判断 | 当前建议 |
|---|---|---|---|---|
| 1 | 面向任务结构认知的离线多智能体协同决策 | 不完备结构先验下的组合泛化与负迁移控制 | 较高：数据覆盖、任务划分与强基线成本大 | 首选主线，先问是否有现成离线数据和复现代码 |
| 2 | 奖励机器 | 异步、延迟与乱序事件下的任务状态修订 | 中高：实验较轻，但需严谨证明与既有噪声模型的差异 | 优先做快速验证；有相关积累时可升为主线 |
| 3 | 自进化表格基础模型 | 缺失模式变化下的预算受限上下文选择 | 中高：启动容易，竞争强、查新和跨数据集公平评价较难 | 应用与数据科学备选，避免直接承接过大的“自进化”目标 |

## 1. 离线多智能体：先确认结构与覆盖问题

**候选问题：** 离线数据只覆盖部分协作组合时，结构先验何时有效？先验错误或过时时，能否减少负迁移？先在仓储、协同搬运、资源收集等通用民用任务上诊断，再决定是否引入先验可靠性控制。

**实验项目：** [OG-MARL](https://github.com/instadeepai/og-marl)；后续候选 [MangoBench locomotion](https://github.com/SYSU-SAIL/mangobench-locomotion)。两者不是相同任务和协议，接入前需检查数据、依赖与评价方式，不能将框架原始成绩混为同一对照。

**先读与索要：**

- [Exploiting Structure in Offline Multi-Agent RL: The Benefits of Low Interaction Rank，ICLR 2025](https://proceedings.iclr.cc/paper_files/paper/2025/hash/9a55d80ab23017cf7094824c03a25843-Abstract-Conference.html)：结构收益已有直接先例。
- [Out-of-Distribution Generalisation with Sequence Models in Offline Multi-Agent Reinforcement Learning，2026 预印本](https://arxiv.org/abs/2609.03667)：对照任务泛化及容量／数据关系，进一步确认代码可得性。
- [Offline Multi-task Transfer RL with Representational Penalization，AISTATS 2025](https://proceedings.mlr.press/v258/bose25a.html)：相邻的迁移、覆盖与表征不确定性方法，不应误称为同一 MARL 基准。
- [Variational Offline Multi-agent Skill Discovery，IJCAI 2025](https://www.ijcai.org/proceedings/2025/538)：核对技能发现与组合方面的已有贡献。

**向相关同学重点询问：** 任务结构是人工标注还是轨迹推断？现有代码做到哪一层？是否已有相同任务下的离线基线、数据质量分档与训练／测试任务划分？最接近论文是哪篇？有没有已尝试失败的结构化方法？

**首轮继续条件：** 基线能跑通；能够明确构造覆盖不足和结构错配；简单固定权重或增加模型容量不能轻易解释全部现象。如果只是在某个种子上提升，暂不扩大方法。

## 2. 奖励机器：适合先做可人工核算的实验

**候选问题：** 事件发生顺序与观测到达顺序不同，有限窗口修订是否改善任务进度估计与完成率？必须只使用当时已经到达的信息，不能把未来观测泄漏给策略。

**实验项目：** [reward-machines-noisy-environments](https://github.com/andrewli77/reward-machines-noisy-environments)；环境可考虑 [MiniGrid](https://github.com/Farama-Foundation/Minigrid)。

**先读与索要：** [Reward Machines for Deep RL in Noisy and Uncertain Environments](https://arxiv.org/abs/2406.00120)、[PROB-IRM，KR 2024](https://proceedings.kr.org/2024/85/kr2024-0085-parac-et-al.pdf)、[Active Reward Machine Inference From Raw State Trajectories，2026 预印本](https://arxiv.org/abs/2604.07480)。第一项代码对应论文已研究噪声与相关误差；不能把“加入记忆处理噪声”当成全新贡献。

**向相关同学重点询问：** 目前处理的是事件分类错误、丢失，还是到达延迟？是否已有奖励机器定义、事件检测器和基线实现？哪些部分理论上可证明？是否有真实异步日志或机器人任务？

**首轮继续条件：** 在可手工验证的序列上确认问题；比较排序缓存、固定延迟处理、固定滞后平滑、同窗口 RNN 与既有 IBU／TDM 方法。如果简单缓存就解决，需收窄贡献或停题。

## 3. 表格基础模型：需要完整跨数据集评价

**候选问题：** 训练与推理阶段缺失模式发生变化时，有限推理预算下如何选择上下文样本／特征？“自进化”先落到可度量的适应机制，避免一开始训练全新的基础模型。

**实验项目：** [TabPFN](https://github.com/PriorLabs/TabPFN)、[TabFSBench](https://github.com/LAMDA-NeSy/TabFSBench)。代码、模型权重和数据许可分别检查。

**先读与索要：** [TabFSBench，ICML 2025](https://proceedings.mlr.press/v267/cheng25e.html)、[IJCAI 2025 特征减少条件下测试时适应工作](https://www.ijcai.org/proceedings/2025/0550.pdf)、[DistPFN，2026 预印本](https://arxiv.org/abs/2605.04363)。DistPFN 的标签分布变化与缺失模式变化不同，只在相应设置下作比较。

**向相关同学重点询问：** 已用哪个 TabPFN 版本？“自进化”具体指上下文选择、参数更新还是数据生成？有多少数据集、如何排除预训练污染？是否有完整树模型和测试时适应基线？能否给出推理延迟／显存预算下的公平比较？

**首轮继续条件：** 在多个独立数据集和缺失机制上出现一致问题，并在同预算下优于简单插补、随机上下文和树模型。仅单一数据集提升不够形成可靠结论。

## 另外两个备选

| 主题 | 收窄方向与开源起点 | 应先要的资源 | 暂缓原因 |
|---|---|---|---|
| 多源异构数据融合与交互式故障诊断 | 工况变化／传感器缺失与少量反馈；[TSB-AD](https://github.com/TheDatumOrg/TSB-AD)、[TAB](https://github.com/decisionintelligence/TAB) | 有许可的过程数据、故障标签、工况划分、现有基线 | 没有故障因果证据时，异常检测结果不能冒充根因诊断 |
| 约束强化学习 | 通用民用机器人约束与安全学习；[OmniSafe](https://github.com/PKU-Alignment/omnisafe)、[Safety Gymnasium](https://github.com/PKU-Alignment/safety-gymnasium) | 约束定义、代价指标、理论积累、完整训练日志 | 难度较高；局部实验安全率不能推广为普遍安全保证 |

学习型机器人操作和人形机器人协调搬运，在有成熟平台、演示数据、仿真和指导时可重新提高优先级；单靠算力暂不足以优先选择。

## 讨论后怎样定主线

先用三个硬条件筛选：论文问题能说清、核心基线可复现、数据可合法获得。再比较指导与已有积累、两周验证可行性、创新空间和目标投稿适配。优先选能尽快验证假设的方向，不按题目大小排序。

三个方向均以 A−／A 作为努力目标，现阶段没有结果，不能评估实际录用层级。使用[资源讨论模板](../templates/resource-intake.md)回收信息后，再锁定唯一主线与第一批实验。
