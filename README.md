# astro-talk-slides — 天文学学术报告 PPT Agent Skill

专业方向：从天文学论文 / NASA ADS 文献 / 观测数据构建简洁、科研严谨、图表驱动的口头报告。

## 文件结构

- `SKILL.md`：Agent 主要工作流、触发条件、质量门禁。
- `references/`：权威来源、设计参数、天文学绘图准则、长短报告叙事模板、QA Rubric。
- `assets/`：brief 和逐页 slide manifest 模板。
- `scripts/check_pptx.py`：PowerPoint 静态质检器。

## 让 Agent 自动安装（直接复制 Prompt）

先把本项目的 `astro-talk-slides-skill.zip`（或解压后的 `astro-talk-slides/` 文件夹）放进当前工作区，或作为附件提供给有文件访问权限的 Codex / 编程 Agent，然后**把下面整段提示词交给 Agent**。Agent 应执行文件操作，而不是只告诉你如何手动安装。

```text
请你担任 Agent Skills 安装助手，直接在我的计算机 / 当前开发环境中完成 astro-talk-slides Skill 的安装，不要只输出安装教程。

任务与规则：
1. 检查当前工作区和我提供的附件，寻找 astro-talk-slides-skill.zip 或 astro-talk-slides/ 文件夹。不要臆造源文件路径；如果确实无法访问安装包，明确告诉我需要把 ZIP 或文件夹放在哪里，再停止。
2. 检查安装包内容。ZIP 内应包含 astro-talk-slides/SKILL.md、references/、assets/、scripts/check_pptx.py。先检查压缩包路径，避免 Zip Slip（路径穿越）；不要执行安装包里的陌生脚本。
3. 默认进行【用户级安装】，目标位置为 ~/.agents/skills/astro-talk-slides/（Windows 使用用户主目录下的 .agents/skills/astro-talk-slides/）。如果我已经明确要求“仅当前项目使用”，则改装到当前项目根目录 .agents/skills/astro-talk-slides/。如果当前 Agent 不支持这些路径，先查明该 Agent 官方支持的 Skill 目录，使用兼容路径并向我说明。
4. 由你自行创建目录、解压或复制全部文件，保证目标目录下直接是 SKILL.md、references/、assets/、scripts/，不能产生 astro-talk-slides/astro-talk-slides/ 的重复嵌套。不要只复制 SKILL.md。
5. 如果目标已经存在，先检查原版本并备份到旁边带时间戳的目录，再更新；不要未经备份覆盖用户修改，也不要删除无关 Skill。
6. 完成后验证：
   - 目标 SKILL.md 确实存在且开头包含 YAML frontmatter；
   - frontmatter 的 name 为 astro-talk-slides、description 非空；
   - references/、assets/ 和 scripts/check_pptx.py 等文件完整可读；
   - 若环境允许，执行基础静态检查；仅在需要运行 PPTX 质检器时才安装 python-pptx，不要为安装 Skill 擅自安装大量依赖。
7. 检查当前 Agent 是否已经能发现 astro-talk-slides。若需要重启会话或刷新 Skill 列表，明确告知，不要假称已经在当前会话激活。
8. 安装完成后给我一份简洁报告：安装位置、安装/更新结果、文件完整性检查、是否需要重启，以及一条我可以直接用于测试 Skill 的 Prompt。

验收测试 Prompt：
“使用 astro-talk-slides Skill，把我提供的天文学论文及科研图表整理为 15 分钟英文会议报告。先给出科学叙事与逐页设计方案，核实来源，再生成 PPTX、PDF、speaker notes 和 QA 报告。”

现在开始自行安装和验证，不需要再次向我确认默认安装位置。
```

> **默认全局安装**：`~/.agents/skills/astro-talk-slides/`，可供支持该目录的 Codex 会话跨项目使用。**项目安装**：`<项目根目录>/.agents/skills/astro-talk-slides/`，适合随项目一起管理。具体扫描位置以你正在使用的 Agent 官方文档为准。

## 手动安装与使用

将**整个** `astro-talk-slides` 文件夹置于 Agent 可扫描的 skills 目录，例如项目内 `.agents/skills/astro-talk-slides/`，确保 `SKILL.md` 位于其根目录。若 Skill 没有出现，可刷新列表或重新开启会话。无需把每个 reference 文件粘贴进提示词。

在 Agent/Codex 中示例请求：

> 使用 `astro-talk-slides` Skill，把我的论文和科研图生成一套 15 分钟英文 AAS 风格学术报告：结果为主，最多三条主结论，附 PPTX、PDF、演讲备注和 QA 报告；学术引用以 NASA ADS/原论文核实。

也可以用于检查已有文件：

> 使用 `astro-talk-slides` 评审这份报告的天文学术准确性、图表、引用、无障碍和时长。提供逐页问题清单，并修复已确认的版式问题。

## 依赖（运行静态质检器才需要）

```bash
pip install python-pptx
python scripts/check_pptx.py /path/to/talk.pptx --output qa-static.md
```

## 关于“标准”的透明说明

AAS 等学会**没有全领域统一的 36pt 字号 / 5 bullets / 每页 1min 强制标准**。本 Skill 中的推荐字号、画布布局、配色及页数是基于投影观看和清晰叙事的可调整设计准则。以本届会议真实 presenter instructions 为最高优先级。所有可核实资料集中在 `references/standards-and-sources.md`。

## 规范资料

- [Agent Skills 规范](https://agentskills.io/specification)
- [OpenAI Codex Agent Skills](https://developers.openai.com/codex/skills)
