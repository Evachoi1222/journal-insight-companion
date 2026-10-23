# Journal Insight Companion｜日记洞察伙伴

[简体中文](README.md) | [English](README.en.md)

一个中文优先的 [Agent Skills](https://agentskills.io/) 风格 Skill：支持分段记录日记，仅在用户明确要求后开展深入洞察；触发后默认依次输出**深度洞察 → 适合备忘录保存的 Takeaways → 500 字以内的日记整理**。

## 核心设计

| 原则 | 行为 |
| --- | --- |
| **先倾听，后洞察** | 默认处于记录模式；只有“开始洞察”等明确指令才触发深入分析。 |
| **少而深** | 每轮选择 1–2 个合适视角，不机械套用心理学术语。 |
| **重视证据和反例** | 区分事实、解释和假设；避免一味迎合，也不把环境问题简单归因于个人。 |
| **可沉淀** | 触发“开始洞察”后默认输出三部分；仅在用户明确要求时省略其中部分。 |
| **跨日期比较** | 上下文可用时比较不同日期的记录；不假设模型能自动读取所有历史会话。 |

## 目录

```text
journal-insight-companion/
├── SKILL.md                    # Skill 入口及工作流规则
├── README.md                   # 中文项目说明、安装和使用
├── README.en.md                # 英文项目说明、安装和使用
├── LICENSE                     # MIT 许可证
├── .gitignore
├── examples/
│   └── conversations.md        # 触发示例
└── references/
    └── evaluation-checklist.md # 手工测试清单
```

## 安装

这是一个**提示词型 Skill**，不需要 Python 或其他依赖。将本仓库克隆或下载到本地，并按照 AI Agent 客户端文档，把包含 `SKILL.md` 的目录放入该客户端的 Skills 搜索路径。各客户端的路径、发现机制与权限要求可能不同，以官方说明为准。

```bash
git clone https://github.com/<YOUR_USERNAME>/journal-insight-companion.git
```

> 将 `<YOUR_USERNAME>` 替换为你的 GitHub 用户名。此 URL 仅为示例，不代表仓库已经创建。

如果客户端不支持 Agent Skills，也可以直接将 `SKILL.md` 内容用作自定义指令；自动触发与状态保持效果取决于客户端。

## 使用

| 阶段 | 用户示例 | 助手行为 |
| --- | --- | --- |
| 开始记录 | “开启日记模式” | 进入分段记录模式。 |
| 继续记录 | 继续发送日记内容 | 只作简短回应，不提前深入分析。 |
| 触发洞察 | “开始洞察” | 按顺序输出下方三个部分。 |
| 指定省略 | “开始洞察，但不用整理日记” | 输出洞察与 Takeaways，省略日记整理。 |
| 单项请求 | “整理成500字以内日记” | 只执行日记整理。 |

默认三部分的输出顺序：

1. **深度洞察**
2. **适合备忘录保存的 Takeaways**
3. **500 字以内的日记整理**

详见 [`examples/conversations.md`](examples/conversations.md)。

## 设计边界

| 范围 | 说明 |
| --- | --- |
| 心理健康 | 不是心理治疗或临床诊断工具。 |
| 数据保存 | 不默认保存用户日记；跨会话连续性取决于宿主产品的记忆、文件或上下文能力。 |
| 隐私 | 不向第三方服务上传日记内容；本仓库不含任何个人日记数据。 |
| 平台兼容 | 不保证所有 AI 平台都会自动识别或严格执行 Skill。 |


## License

MIT，详见 [LICENSE](LICENSE)。
