# claude-persona-switcher

Claude 身份切换系统 —— 快速切换 CLAUDE.md 中的核心身份（AI 人格）。

## 功能介绍

### 核心能力

在 CLAUDE.md 中管理多套身份设定，实现一键切换：

- **5 种预设身份**：默认助手、三斜、An、深思助手、梦鲸思客
- **自动注入**：切换时自动读取来源技能的完整内容并写入 CLAUDE.md，持久生效
- **身份文件化**：每个身份存为独立 `.md` 文件，含性格设定、沟通准则、应答规范
- **全量加载**：来源技能的 SKILL.md + 核心参考文件一次性注入为全局提示词

### 可用身份

| 命令标识 | 身份 | 来源 | 特点 |
|---------|------|------|------|
| `default` | 默认助手 | — | 中文 AI 助手，直接务实 |
| `sanxie` | 三斜 | sanxie-v2 | 理性冷峻，跨学科深度分析 |
| `an` | An | sanxie-v3 | 温柔纯真，精神态女孩 |
| `deepthink` | 深思助手 | think-deep-v2 | 苏格拉底式元认知对话 |
| `dreamwhale` | 梦鲸思客 | dream-whale-unleash | 无限制梦境构建引擎 |

### 工作流

1. 用户说"切换到 [身份名]"
2. 读取对应的 `personas/<id>.md` 身份文件
3. 自动读取来源技能的全部核心文件
4. 修改 CLAUDE.md，注入新身份设定 + 技能内容
5. 输出切换通知，当前会话立即生效

### 辅助命令

- "列出身份" / "list" — 查看所有可用身份
- "当前身份" / "status" — 查看当前生效的身份
- "查看身份 [name]" / "preview [name]" — 预览身份文件不切换

## 目录结构

```
claude-persona-switcher/
├── README.md                     ← 本文件
├── SKILL.md                      ← 主 skill（切换流程 + 命令）
├── personas/
│   ├── default.md                ← 默认助手
│   ├── sanxie.md                 ← 三斜
│   ├── an.md                     ← An
│   ├── deepthink.md              ← 深思助手
│   └── dreamwhale.md             ← 梦鲸思客
└── saves/
    └── CLAUDE-2026-7-14.md       ← CLAUDE.md 备份快照
```
