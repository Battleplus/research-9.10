# 科研工作流调用手册

## 总入口

本手册说明如何调用已安装的 ARIS 技能完成研究工作。它是供 AI 读取的执行约定，不是可在终端直接运行的程序。本项目当前模式为 **选题准备**，交付物是方向决策，不是实验结果或论文。

直接给执行 AI 以下指令：

> 请从 WORKFLOW.md 开始，读取 AGENTS.md、HANDOFF.md 和 docs/direction-selection-execution-plan.md。先检查已有 direction-selection/STATUS.md 与知识库，从未完成步骤继续。按照“文献整理 → 候选生成 → 查新 → 方案审查 → 方向决策 → 知识沉淀”调用适用技能。结合已有偏好强化学习和世界模型经历，比较课题连续性、A− 以上目标、难度与就业。仅阅读、检索、静态代码分析和方案撰写，跳过所有 pilot、训练和自动实验。每步保存来源和状态，最后交付有条件与反证的主副课题推荐并停止。

技能在 Codex 中可通过 `$research-lit` 等名称显式引用；其他宿主可能使用 `/research-lit`。这些是对 AI 的技能调用请求，不是 shell 命令，也不代表存在同名可执行程序。未安装技能的执行器应先说明能力差异，再按手册步骤完成可做部分。

## 调用顺序与产物

| 步骤 | 调用能力 | 必需输入 | 保存结果 | 通过条件 |
|---|---|---|---|---|
| 0 恢复上下文 | 读取项目文件与已有状态 | 用户目标、已有成果、安装记录 | 更新 STATUS.md 的事实与未知项 | 不重复已完成工作，不把假设当个人经历 |
| 1 文献阅读 | research-lit；PDF；按需 arxiv、openalex、semantic-scholar | 四篇基础论文、三条候选路线 | EVIDENCE.md：阅读卡、查询与来源记录 | 原文支持关键摘要；记录版本、页码／节号 |
| 2 候选生成 | idea-creator，覆盖为仅方案分析 | 文献证据、已有积累、资源约束 | OPTIONS.md：最多四个候选问题卡 | 每个问题说明现有方法、可能差异、简单替代方案与资产复用 |
| 3 查新 | novelty-check | 候选问题及核心差异 | EVIDENCE.md 中的逐项对照，更新 OPTIONS.md | 比较最接近方法，不用“未搜到”证明首次提出 |
| 4 审查 | research-review；必要时 research-refine 的方案部分 | 问题卡、原始证据、查新结果 | OPTIONS.md 的反对意见、修订与未解决项 | 排除模块拼接、评价循环和不切实际的资源前提 |
| 5 方向决策 | 执行 AI 综合判断 | 三条路线的证据、成本和审查 | DECISION.md | 一个主课题、一个关联副课题、条件替代与关键待确认问题 |
| 6 沉淀 | research-wiki；需要补全笔记时 wiki-enrich | 已核验文献和决策 | Wiki、STATUS.md | 标明来源、结论状态与未实验验证，停止在选题阶段 |

上表文件统一位于 `direction-selection/`。技能自身可能产生 `idea-stage/`、`refine-logs/` 等原生文件，保留其原始记录，在最终文件链接或归纳，不伪造技能已经输出指定格式。不把草稿、失败审查或未验证候选改名为已通过结论。

## 每一步可复制的调用提示

### 文献整理

> 使用 research-lit，先核对本地四篇 PDF 和已有阅读卡，再补充最近工作。主题为多智能体偏好奖励学习及其与世界模型、约束、多目标适应的连续关系。默认来源为本地 PDF 和可用网络检索，arXiv／OpenAlex 按需补充。区分脚本教师与人类偏好、离线奖励数据与离线 RL、作者主张与实验支持。把来源和页码写入 direction-selection/EVIDENCE.md；本轮不执行论文代码。

### 候选生成

> 使用 idea-creator 的文献与候选生成部分。覆盖其默认行为：不调用 run-experiment、monitor-experiment，不跑 pilot，不安装训练环境。基于 EVIDENCE.md 比较三条连续路线，最多保留四张问题卡，每卡写明复用资产、最近方法、待验证差异、最简单替代方案、未来验证设想和停止条件。结果为方案假设，不是验证完成的创新。

### 查新

> 使用 novelty-check，逐项检查 OPTIONS.md 中候选差异。记录执行日期和实际检索范围，阅读最近方法原文，不只凭摘要判断。分别标注“明显重合”“存在待核实差异”“资料不足”。允许删除候选；不为了凑方向保留已被充分解决的问题。只查新，不运行实验。

### 审查与修订

> 使用 research-review 审查问题意义、证据、个人积累的复用、资源难度和就业关联。先提出最强反对意见，再决定保留、收窄或淘汰。存在独立评审工具时如实记录身份和输入输出；不可用时完成本地自查并明确缺少独立评审。最多两轮方案修订，仍有缺口就记录，不追逐 AI 分数。research-refine 仅在问题已足够明确时用于收窄机制，本轮不接 experiment-plan 的执行或 experiment-bridge。

### 决策与归档

> 输出 DECISION.md，明确推荐主副课题、为何连续、什么条件会改变排序，以及不超过五个负责人问题。目标刊会以当时核验的范围和单位档位为准，没有实验不预测录用概率。更新 Research Wiki 和 STATUS.md，注明“选题分析完成／条件待确认，未运行实验”。完成后停止。

## 调用边界与失败处理

- **idea-creator 和 idea-discovery 都可能自动触发 pilot。** 当前用户要求优先于这些默认行为；两者都必须跳过实验阶段，不能声称走完上游的 pilot 验证。
- 当前不调用完整 research-pipeline、experiment-bridge、run-experiment 或云 GPU 工具。预装技能不是执行授权。
- 技能提到的工具名按当前宿主实际能力映射；工具缺失时不得编造调用记录。联网可以使用当前会话检索能力，Python 辅助脚本只是补充。
- Semantic Scholar 限流时记录状态，使用 arXiv、OpenAlex、作者主页和官方会议页面继续；不反复请求造成无效等待。额外付费服务未配置时不擅自注册或购买。
- 新鲜上下文中的同模型审查记为 same-family／provisional；没有独立调用则记为 self-review。审查为 BLOCKED 时保留该状态，可以完成普通分析，但不能伪造审查 PASS。
- 技能调用参数以实际 SKILL.md 为准。本文的“仅方案分析”“跳过实验”是自然语言范围约束，不是声称存在 `--no-pilot` 等 CLI 参数。
- 没有个人代码时继续文献和条件化推荐；没有访问过原表时不猜测当前项目行号。
- 每阶段在 STATUS.md 写明输入、真实使用的技能／工具、产物路径、结论状态、缺失项和下一步。下次接手先读状态及实际产物，不能仅凭状态文字认定完成。
- 提交时只暂存本次拥有的文件；保留其他 AI 或用户的改动。公开发布遵循既有明确授权，不能把阅读或安装授权当作所有后续发布授权。

## 本机工具入口

从仓库根目录运行以下命令，可查看辅助脚本真实接口；执行检索属于选题工作，不会启动训练：

```powershell
.\.venv\Scripts\python.exe .\.aris\tools\arxiv_fetch.py --help
.\.venv\Scripts\python.exe .\.aris\tools\openalex_fetch.py --help
.\.venv\Scripts\python.exe .\.aris\tools\semantic_scholar_fetch.py --help
.\.venv\Scripts\python.exe .\.aris\tools\research_wiki.py --help
```

本机源码、技能链接和 `.venv` 不随 GitHub 克隆自动出现。其他机器先检查 `docs/tooling-setup.md` 并安装相应组件；网络连通性与账号状态也需要重新检查。本地 PDF 位于 Git 忽略的 `literature/`。

## 将来进入研究阶段时

用户明确确认方向并要求实验后，才另行建立计算预算与实验协议：research-refine → experiment-plan → experiment-bridge／run-experiment → experiment-audit → analyze-results／result-to-claim → 必要消融与补实验 → paper-plan／paper-write → 论断和引用审查 → 编译及投稿准备。这是后续路线图，本次没有执行。

工具能组织工作、保存证据和辅助审查，不能保证创新、A− 档成果或录用。论文结论必须来自真实实验或可核验文献，不能从选题阶段的推测直接生成结果。
