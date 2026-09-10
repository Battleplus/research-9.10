# 科研工具安装与使用状态

## 当前可用范围

已完成选题准备工作台安装：ARIS Codex 适配技能、检索辅助脚本、独立 Python 环境、PDF 与引用处理依赖、研究知识库。当前用于读论文、查新、方向比较与方案审查，没有启动研究实验。

ARIS 来源为 [官方仓库](https://github.com/wanshuiyin/Auto-claude-code-research-in-sleep)，固定安装版本为 `ba0ff54aa837d60163776901d5c7fbffe2cec677`。共安装 59 个技能，覆盖文献、选题、评审、实验、论文与投稿准备，以及依赖项。后续阶段技能仅预装，不代表对应服务已连接或已获执行授权。

## 安装组成

| 组件 | 状态 | 说明 |
|---|---|---|
| ARIS Codex 技能 | 已安装，元数据检查通过 | 项目 `.agents/skills/`，同时安装到用户 Codex 技能目录，下一轮对话可发现 |
| ARIS 辅助脚本 | 已安装 | 项目 `.aris/tools/` 指向本机源码；本机链接不提交 Git |
| Python 3.12 环境 | 已创建 | `.venv/Scripts/python.exe`；依赖版本见 `requirements-tooling.lock.txt` |
| PDF 与引用处理 | 导入及 PDF 读取通过 | pypdf、pdfplumber、PyMuPDF、bibtexparser、PyYAML、requests |
| arXiv | 检索脚本实测成功 | 以基础论文 ID 做连通性检查 |
| OpenAlex | 检索脚本实测成功 | 返回论文元数据 |
| Semantic Scholar | 脚本已安装，服务当前限流 | 本次接口返回 HTTP 429；不能宣称当前可用 |
| 本地文献库 | 已建立 | `literature/` 中保留四篇用户提供的 PDF，Git 忽略 |
| Research Wiki | 已初始化 | `research-wiki/`；目前是空知识库结构，不代表文献已整理入库 |
| Codex / Claude CLI | 已存在且版本命令成功 | 未由本次新安装；未测试模型调用或独立跨模型评审 |
| Exa / Gemini / DeepXiv 等额外来源 | 技能入口已安装，外部依赖未验证 | 需要相应 CLI、账号或密钥时另行接入，当前检索使用已验证来源和会话联网能力 |
| Overleaf、GPU 云服务、完整 LaTeX 编译链 | 本次未配置 | 属于后续阶段能力；安装技能不等于完成服务部署 |
| MAPT 等课题训练框架 | 未安装运行环境 | 当前不进行具体课题实验 |

## 选题阶段入口

- `research-lit`：结合本地 PDF 与网络检索建立文献矩阵。
- `novelty-check`：核查想法与最接近已有工作的差异。
- `idea-creator`：形成可证伪的候选研究问题。
- `research-review`：审查问题意义、难度、实验可行性与证据缺口。
- `research-wiki`：保存文献、想法、决策与关联关系。

本项目的阶段约束见 [AGENTS.md](../AGENTS.md)。调用 `idea-discovery` 时跳过 pilot，记录“仅方案分析、未实验验证”；不得让自动继续默认值触发训练、租用 GPU 或投稿。同模型复核不能标为跨模型独立审查。

## 本机维护

本机 ARIS 源码位于工作区的 `aris-toolkit` 目录。使用其官方 `tools/install_aris.ps1` 管理项目安装。已选组为 `lit-search,ideation,review-loop,experiments,paper-core,submission`，安装器自动补入依赖。

用户技能由 Codex 技能安装器从上述固定提交安装。升级时应同步项目源码与用户技能副本，先检查变更，避免两份技能版本不一致。全局辅助脚本定位指针由 ARIS 安装器维护。

独立环境的包可通过 `uv pip sync --python .venv/Scripts/python.exe requirements-tooling.lock.txt` 恢复。技能内容、源码、Python 环境与外部服务连接是不同层次；本次检查只证明表中列明的能力，不构成完整科研流水线端到端验收。
