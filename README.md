# 🎓 Trae Tutor (Ultimate Edition) - 你的 AI 专属学习导师

> **架构版本**: V6.0 (Cloud-Native + Web-Aware + State-Persistent)
> **维护者**: CodeManYsf

这是一个基于 **Trae IDE** + **MCP (Model Context Protocol)** 构建的自进化学习智能体配置。它不仅仅是一个聊天机器人，而是一个拥有“手”（GitHub同步）、“眼”（联网读取）、“脑”（自动规划）和“记忆”（进度追踪）的全能导师。

---

## 🌟 核心特性 (Features)

### 1. 🧠 动态大脑 (Cloud Sync)
- **零配置启动**：只需一句“初始化环境”，智能体自动从 GitHub 仓库 (`master` 分支) 拉取最新的技能 SOP。
- **技能侧载 (Sideloading)**：支持直接将 `.md` 技能文件拖入对话框，实现能力的实时热更新。

### 2. 👁️ 全网知识获取 (Web-Aware Learning)
- **智能路由**：集成 `Fetch` (轻量)、`Playwright` (抗反爬) 和 `Context7` (官方文档)。
- **一键挂载**：发送 URL（如博客、教程）或关键词（如 "React Docs"），智能体自动抓取清洗，转化为学习素材。

### 3. 🗺️ 自动化课程设计 (Curriculum Designer)
- **路书生成**：根据抓取的内容，自动生成分步学习计划 `book/roadmap.md`。
- **断点续学**：智能维护学习状态。下次回来只需说“继续”，它自动检查 `[x]` 标记，带你进入下一章。

### 4. 📚 知识闭环 (Knowledge Loop)
- **实战演练**：引导在 `test/` 目录编写代码，提供 Code Review。
- **自动归档**：学习结束后自动生成 Markdown 笔记存入 `book/`，并更新路书进度。

---

## 📂 目录结构 (Directory Structure)

```text
.
├── .trae/
│   └── skills/                 # [核心] 智能体的技能库
│       ├── TutorialLoader/     # 爬虫与文档加载器
│       ├── CurriculumDesigner/ # 课程规划师
│       ├── ProgressManager/    # 进度与状态管理器
│       └── KnowledgeArchivist/ # 笔记归档员
├── book/                       # [自动生成] 存放学习路书(roadmap.md)和笔记
├── test/                       # [用户空间] 用于编写练习代码
└── README.md                   # 项目说明文档

```

---

## 🚀 快速开始 (Quick Start)

### 1. 环境准备

确保你的 Trae IDE 已安装并配置好以下 MCP 工具：

* ✅ **GitHub** (用于同步技能)
* ✅ **Fetch** (基础网页抓取)
* ✅ **Playwright** (高级网页抓取)
* ✅ **Context7** (官方文档检索)

### 2. 启动智能体

在 Trae 对话框中输入：

> **"初始化环境"**

智能体将自动检查本地状态，并从 `CodeManYsf/cyysf-trae-skills` 下载核心技能。

### 3. 开始学习

**方式 A：基于现有教程**

> "我想学这篇文章：https://www.google.com/search?q=https://example.com/python-tutorial"

**方式 B：基于关键词（查文档）**

> "教我 Python Pandas 的基础用法"

**方式 C：继续之前的进度**

> "我学到哪了？继续学习。"

---

## 🛠️ 技能清单 (Skills Matrix)

| 技能名称 | 触发条件 | 核心职责 |
| --- | --- | --- |
| **TutorialLoader** | 输入 URL 或 "教我..." | 路由 Fetch/Playwright/Context7，清洗数据并移交规划。 |
| **CurriculumDesigner** | 接收清洗后的文本 | 生成或追加 `book/roadmap.md`，拆解学习阶段。 |
| **ProgressManager** | "继续学习" / 任务完成 | 读取/更新 `roadmap.md` 中的 Checkbox 状态。 |
| **KnowledgeArchivist** | "学会了" / 代码跑通 | 生成总结笔记，并触发进度打钩。 |

---

## 📝 License

MIT License © 2026 CodeManYsf

```