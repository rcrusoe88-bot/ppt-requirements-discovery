# ppt-requirements-discovery · WorkBuddy 版

> 动手做 PPT 之前，先花几分钟把需求聊清楚。

这是同一个「PPT 需求访谈」技能的 **WorkBuddy 原生版本**。它与仓库根目录的 codex / Claude Code 版共用同一套访谈流程与 `Presentation Brief` 模板，仅针对 WorkBuddy 做了三点适配：

1. frontmatter 增加 `agent_created: true`，标记为 AI 创建的技能，WorkBuddy 后续可直接修改更新；
2. `description` 中补充中文触发词，让 WorkBuddy 能更准确地自动唤起；
3. 移除 codex 特有的 `agents/openai.yaml` 与 `$` 调用语法（WorkBuddy 不识别），目录遵循 WorkBuddy 的技能包约定。

## 安装

**方式一：💬 自然语言安装（推荐）**

在 WorkBuddy 对话窗口中直接粘贴以下话术：

```
帮我在 WorkBuddy 上安装 ppt-requirements-discovery 技能。
文件来自 https://github.com/rcrusoe88-bot/ppt-requirements-discovery 仓库的 workbuddy/ 子目录，
请装到我的个人技能目录（Windows：%USERPROFILE%\.workbuddy\skills\ppt-requirements-discovery，
macOS/Linux：~/.workbuddy/skills/ppt-requirements-discovery），装完告诉我重启 WorkBuddy 生效。
```

也可以对 WorkBuddy 说「导入技能」，然后把本目录的 `SKILL.md` 文件拖给它。

**方式二：🖥️ 命令行安装**

```bash
# Windows (PowerShell)
xcopy /E /I workbuddy %USERPROFILE%\.workbuddy\skills\ppt-requirements-discovery

# macOS / Linux
cp -r workbuddy ~/.workbuddy/skills/ppt-requirements-discovery
```

安装后重启 WorkBuddy 即可生效，之后可在对话中手动指定 `@ppt-requirements-discovery` 调用。

## 触发

当你说「帮我做一个关于 X 的 PPT」、需求不完整、或需要先梳理演示目标时，WorkBuddy 会自动调用本技能开始需求访谈。也可手动指定：`@ppt-requirements-discovery`。

## 目录结构

```
workbuddy/
├── SKILL.md            # 技能主文件：访谈流程、工作原则、Brief 模板（WorkBuddy 适配版）
└── README.md           # 本说明
```

## 与根目录 codex/Claude 版的差异

| 项目 | 根目录（codex / Claude Code） | workbuddy/（WorkBuddy） |
|---|---|---|
| frontmatter | `name` + `description` | `name` + `description` + `agent_created: true`，描述含触发词 |
| 附属配置 | `agents/openai.yaml`（OpenAI Agent 接口） | 无（WorkBuddy 不识别 codex 的 agents/） |
| 调用语法 | 支持 `$ppt-requirements-discovery` | 用技能面板或 `@` 手动指定 |
| 通用部分 | SKILL.md 正文完全一致 | 同上 |

## License

[MIT](../LICENSE) © 2026 Reginald Crusoe
