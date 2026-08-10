# ppt-requirements-discovery

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

### Claude Code

将本仓库复制到 Claude Code 的 skills 目录：

```bash
# 个人级（所有项目可用）
git clone https://github.com/rcrusoe88-bot/ppt-requirements-discovery.git \
  ~/.claude/skills/ppt-requirements-discovery

# Windows 用户：~/.claude/skills 对应 %USERPROFILE%\.claude\skills
```

之后当用户提出「帮我做一个关于 X 的 PPT」这类需求时，Claude 会自动调用本技能开始需求访谈，也可手动唤起。

### OpenAI Agent（agents/openai.yaml）

仓库附带 `agents/openai.yaml`，可作为 OpenAI 生态的自定义 Agent 配置，支持隐式调用（`allow_implicit_invocation: true`），默认提示词：

> 使用 $ppt-requirements-discovery 帮我梳理这次PPT的真实需求，并输出 Presentation Brief。

## 项目结构

```
ppt-requirements-discovery/
├── SKILL.md            # 技能主文件：访谈流程、工作原则、Brief 模板
└── agents/
    └── openai.yaml     # OpenAI Agent 接口配置
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
