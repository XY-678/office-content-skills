# Office Content Skills

面向日常办公与内容创作的中文 Agent Skills 合集。把会议记录整理成行动项，把工作日志写成周报，把现有素材变成可审阅的邮件与内容稿件。

首批包含 **6 个独立技能**。每个技能都有自己的 `SKILL.md`，可以按需单独安装；无需 API Key，也不依赖特定付费服务。读取外部网页或本地文件的能力取决于你使用的 Agent 环境。

## 技能目录

| 技能 | 独立文件 | 适合处理什么 |
| --- | --- | --- |
| 会议纪要与行动项 | [meeting-minutes](skills/meeting-minutes/SKILL.md) | 从会议转写、笔记中提取决策与行动项，区分已确认变更和待确认冲突 |
| 工作周报 | [weekly-report](skills/weekly-report/SKILL.md) | 将工作日志整理为成果、进行中事项、风险和下周计划，区分新增量与累计量 |
| 商务邮件草稿 | [business-email](skills/business-email/SKILL.md) | 起草进度同步、催办、邀约、婉拒等邮件 |
| 文章选题与大纲 | [article-outline](skills/article-outline/SKILL.md) | 明确读者问题、中心观点、章节结构与材料缺口 |
| 多平台内容改写 | [content-repurpose](skills/content-repurpose/SKILL.md) | 将原文改写成公众号摘要、社交笔记、短视频口播等 |
| 资料摘要与对比 | [source-brief](skills/source-brief/SKILL.md) | 汇总指定资料的核心结论、差异、依据与信息缺口 |

这些技能默认提供中文 Markdown 内容，遵循用户指定的语言、格式和篇幅。它们用于形成可审阅的内容，不会自行发送邮件、发布文章或替他人承诺事项。

## 快速开始

### 1. 获取仓库

下载本仓库 ZIP，或执行：

```bash
git clone https://github.com/XY-678/office-content-skills.git
```

### 2. 按需安装

以 Codex 本地技能为例，将所需技能的**整个目录**复制到以下任一位置：

| 使用范围 | 目标目录 |
| --- | --- |
| 当前项目 | 项目根目录下的 `.agents/skills/` |
| 当前用户的所有项目 | 用户主目录下的 `.agents/skills/` |

例如只安装会议纪要技能，安装后的结构应为：

```text
你的项目/
└── .agents/
    └── skills/
        └── meeting-minutes/
            └── SKILL.md
```

Windows 用户目录示例为 `%USERPROFILE%\.agents\skills\`；macOS / Linux 为 `~/.agents/skills/`。若同名目录已存在，先查看内容并备份，再决定替换。不要把整个仓库当成一个技能复制进去。

本地路径和调用方式依据 [OpenAI 技能文档](https://learn.chatgpt.com/docs/build-skills)。如果安装后没有显示，重启会话再查看。其他支持 Agent Skills 的工具，可按其文档导入技能目录；各工具的安装入口可能不同。

### 3. 调用技能

在支持 `$skill-name` 的 Codex 环境中，可直接输入：

```text
使用 $meeting-minutes 将下面的会议笔记整理成纪要。
请区分已经确认的决策、建议和行动项，缺失的负责人或日期标注待确认。
会议笔记：
……
```

也可以用自然语言描述任务，让支持自动匹配的 Agent 选择技能。支持技能选择器的界面可在选择器中选取对应技能。

## 使用示例

| 目标 | 可复制的请求 |
| --- | --- |
| 会议纪要 | 使用 $meeting-minutes 整理下面的会议记录，提取行动项并保留未决问题。 |
| 工作周报 | 使用 $weekly-report 根据下面的工作日志写给主管的周报，不超过 600 字。 |
| 商务邮件 | 使用 $business-email 根据下面的背景起草一封礼貌的催办邮件，给出主题和正文。 |
| 文章大纲 | 使用 $article-outline 为“如何建立个人知识库”设计面向职场新人的文章大纲，目标 1500 字。 |
| 内容复用 | 使用 $content-repurpose 将下面的文章改写为公众号摘要、小红书笔记和一分钟口播稿。 |
| 资料摘要 | 使用 $source-brief 对比下面两份材料，列出共同结论、冲突与来源依据。 |

调用时附上实际材料、目标读者和必要约束。完整的示例输入及检查要点见 [使用场景](examples/requests.md)。

## 仓库结构

```text
office-content-skills/
├── README.md
├── LICENSE
├── CONTRIBUTING.md
├── examples/
│   └── requests.md
└── skills/
    ├── meeting-minutes/
    ├── weekly-report/
    ├── business-email/
    ├── article-outline/
    ├── content-repurpose/
    └── source-brief/
```

每个技能目录均包含一个独立的 `SKILL.md`，其中定义技能名称、触发描述、输入处理方式和交付要求。

所有核心工作说明都在对应的 `SKILL.md` 中。仓库示例用于演示和维护，不是运行依赖。

## 编写原则

- **事实有依据**：不补造业绩、决策、数据、引用或亲身体验。
- **缺失信息可见**：将重要信息缺口标为待确认，保留原文中的不确定性。
- **尊重任务范围**：大纲保持为大纲，摘要围绕指定资料，改写不自动扩展为发布。
- **结果便于使用**：优先输出可复制、可审阅的稿件，把补充说明放在成稿之外。

这些指令帮助约束工作方式，实际表现仍取决于模型和输入材料。使用前应复核重要事实、数字、日期和承诺。

## 参与贡献

欢迎通过 Issue 提交使用反馈，或通过 Pull Request 增加和改进技能。新增技能请保持独立目录和独立 `SKILL.md`，补充真实使用场景及检查要点，详见 [贡献指南](CONTRIBUTING.md)。

本仓库为社区技能集合，不是 OpenAI 官方项目。

## 许可证

采用 [MIT License](LICENSE)。使用、修改或分发时保留许可证中的版权与许可声明。
