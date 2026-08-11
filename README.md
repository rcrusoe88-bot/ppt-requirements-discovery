# ppt-requirements-discovery

<p align="center">
  <img src="https://img.shields.io/github/license/rcrusoe88-bot/ppt-requirements-discovery?style=flat-square" alt="License">
  <img src="https://img.shields.io/github/stars/rcrusoe88-bot/ppt-requirements-discovery?style=flat-square" alt="Stars">
  <img src="https://img.shields.io/github/last-commit/rcrusoe88-bot/ppt-requirements-discovery?style=flat-square" alt="Last Commit">
  <img src="https://img.shields.io/github/repo-size/rcrusoe88-bot/ppt-requirements-discovery?style=flat-square" alt="Repo Size">
</p>

<p align="center">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api/pin/?username=rcrusoe88-bot&repo=ppt-requirements-discovery&theme=vue&show_owner=true" alt="ppt-requirements-discovery 仓库数据">
</p>

> 动手做 PPT 之前，先花几分钟把需求聊清楚。

**ppt-requirements-discovery** 是一个「PPT 需求访谈」技能（Skill）：通过结构化、多轮对话，把用户头脑中模糊的 PPT 想法，转化为一份经过确认、可直接交给 PPT 制作 Agent 执行的 **Presentation Brief**。

它刻意只做「需求发现」这一件事——不排版、不写演讲稿、不选模板。目的是在动手前把方向定准，避免「做完才发现方向错了」的高成本返工。

## 为什么需要它

大多数 PPT 需求开始时是模糊的：用户只知道「做一个关于 X 的 PPT」，却说不清给谁看、讲多久、希望听众记住什么。直接进入制作通常会导致：

- **方向偏差**：内容深度与听众水平不匹配；
- **结构松散**：缺主线，靠堆素材；
- **频繁返工**：做完才发现页数、时间、重点对不上。

本技能通过一次有结构的访谈（通常 5–10 分钟），在动手前把关键问题问清楚，并**主动诊断需求冲突**（例如：15 分钟演讲 vs 30 页实验数据），给出可选方案让用户确认。

## 核心特性

- **多轮对话，不投长问卷**：每轮只问一组最关键的问题，循序渐进；
- **先问为什么，再问怎么做**：先澄清场景、听众、目标，再谈页数与风格；
- **主动诊断冲突**：用「现状 → 风险 → 建议 → 确认」的格式指出需求矛盾；
- **输出标准化 Brief**：固定九段式结构，制作 Agent 可直接执行；
- **尊重用户节奏**：允许跳过问题，不确定项在 Brief 中标记为「待确认」；
- **边界清晰**：只做需求发现，不越界制作。

## 工作流程

访谈按 7 步推进，用户已提供的信息可直接跳过：

1. **捕捉初始想法** —— 一句话说明任务边界，确认使用场景与演讲目标；
2. **明确听众** —— 核心/次要听众、专业水平、关心的三个问题；
3. **明确核心信息** —— 帮用户完成「如果听众只能记住一句话，我希望他们记住：____」；
4. **确定内容边界与叙事结构** —— 明确必须保留/可省略的内容，从 5 种结构模板中推荐并说明理由；
5. **确定交付约束** —— 演讲时间、页数、风格、品牌、输出格式；
6. **需求诊断** —— 对照冲突清单，发现问题并给出选项供用户确认；
7. **输出 Presentation Brief** —— 先给简短摘要请用户确认，再输出完整 Brief。

输出物 `Presentation Brief` 包含 9 个部分：项目概况、目标听众、演讲目标、核心信息、内容范围、叙事方案、表达与视觉方向、风险与待确认事项、交给 PPT 制作 Agent 的执行指令。

## 安装与使用

支持两种安装方式：**💬 自然语言安装**（推荐，直接把话术说给 AI，让 AI 帮你装）与 **🖥️ 命令行安装**（手动执行命令）。

### 💬 自然语言安装（推荐）

直接把下方话术复制到对应工具的对话窗口发送即可，AI 会按指引完成安装并告诉你如何生效。

**WorkBuddy**

在 WorkBuddy 对话窗口粘贴：

```
帮我在 WorkBuddy 上安装 ppt-requirements-discovery 技能。
技能文件在 https://github.com/rcrusoe88-bot/ppt-requirements-discovery 仓库的 workbuddy/ 子目录下，
请装到我的个人技能目录（Windows：%USERPROFILE%\.workbuddy\skills\ppt-requirements-discovery，
macOS/Linux：~/.workbuddy/skills/ppt-requirements-discovery），装完告诉我重启 WorkBuddy 生效。
```

如果你的 WorkBuddy 版本支持「导入技能」，也可以直接对它说“导入技能”，然后把 `workbuddy/SKILL.md` 文件拖给它。

**Claude Code**

在 Claude Code 对话窗口粘贴：

```
帮我在 Claude Code 上安装 ppt-requirements-discovery 技能。
请把 https://github.com/rcrusoe88-bot/ppt-requirements-discovery 克隆到我的个人技能目录
~/.claude/skills/ppt-requirements-discovery（Windows 对应 %USERPROFILE%\.claude\skills\ppt-requirements-discovery）。
仓库根目录的 SKILL.md 就是 Claude Code 版。
```

AI 会执行 git clone 放到上述目录。仓库自带的 `workbuddy/`、`agents/` 子目录在 Claude Code 中会被忽略，不影响使用。安装后重启或新开会话即可自动加载。

### 🖥️ 命令行安装

**Claude Code**

将本仓库复制到 Claude Code 的 skills 目录：

```bash
# 个人级（所有项目可用）
git clone https://github.com/rcrusoe88-bot/ppt-requirements-discovery.git \
  ~/.claude/skills/ppt-requirements-discovery

# Windows 用户：~/.claude/skills 对应 %USERPROFILE%\.claude\skills
```

之后当用户提出「帮我做一个关于 X 的 PPT」这类需求时，Claude 会自动调用本技能开始需求访谈，也可手动唤起。

**OpenAI Agent（agents/openai.yaml）**

仓库附带 `agents/openai.yaml`，可作为 OpenAI 生态的自定义 Agent 配置，支持隐式调用（`allow_implicit_invocation: true`），默认提示词：

> 使用 $ppt-requirements-discovery 帮我梳理这次PPT的真实需求，并输出 Presentation Brief。

**WorkBuddy**

```bash
# Windows (PowerShell)
xcopy /E /I workbuddy %USERPROFILE%\.workbuddy\skills\ppt-requirements-discovery

# macOS / Linux
cp -r workbuddy ~/.workbuddy/skills/ppt-requirements-discovery
```

安装后重启 WorkBuddy 生效。也可在 WorkBuddy 对话框中输入「导入技能」选择 `workbuddy/SKILL.md`。

## 项目结构

```
ppt-requirements-discovery/
├── SKILL.md            # 技能主文件：访谈流程、工作原则、Brief 模板（codex / Claude Code 版）
├── agents/
│   └── openai.yaml     # OpenAI Agent 接口配置
├── workbuddy/
│   ├── SKILL.md        # WorkBuddy 适配版技能主文件
│   └── README.md       # WorkBuddy 版安装说明
└── README.md           # 本说明
```

## 适用场景

- 用户提出模糊的 PPT 想法；
- 要求制作 PPT 但需求不完整（场景 / 听众 / 目标不明）；
- 需要先梳理演示目标再动手；
- 演示需求存在冲突，需要先厘清。

## 不做什么（MVP 边界）

- 不生成或排版 PPT 文件；
- 不编写完整演讲稿；
- 不选择具体模板；
- 不做网页搜索。

以上工作请在访谈完成后，交由其他适合的技能接手。

## 参与贡献

欢迎提交 Issue / Pull Request，扩充访谈问题库、补充冲突诊断维度，或改进 Brief 模板。

## License

[MIT](./LICENSE) © 2026 Reginald Crusoe

---

## 📊 作者 GitHub 数据

<p align="center">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api?username=rcrusoe88-bot&show_icons=true&theme=vue" alt="rcrusoe88-bot 的 GitHub 统计">
  <img src="https://github-readme-stats-eight-theta.vercel.app/api/top-langs/?username=rcrusoe88-bot&layout=compact&theme=vue" alt="rcrusoe88-bot 的常用语言">
</p>
