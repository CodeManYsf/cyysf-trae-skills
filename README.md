# 🎓 Trae Tutor (V8.0 Ultimate) - 全栈 AI 学习导师

> **架构版本**: V8.0 (Zero-Dependency + Cloud-Native + Context-Aware)
> **维护者**: CodeManYsf

**Trae Tutor** 是一个运行在 Trae IDE 中的自进化学习智能体。它突破了传统 AI 聊天的限制，拥有**自主联网获取知识**、**持久化管理学习进度**以及**零门槛一键部署**的能力。

---

## 🌟 核心特性 (Core Features)

### 1. ⚡ 零依赖极速启动 (Zero-Dependency Bootstrap)
- **无门槛**：不需要用户预装 Git，不需要手动 Clone 仓库。
- **一键部署**：智能体检测到新环境时，会自动提供系统原生指令（PowerShell/Curl），**一键拉取并配置**所有核心技能。

### 2. 👁️ 全网智能感知 (Intelligent Web-Awareness)
- **多模态读取**：集成了三大 MCP 工具，自动路由最佳方案：
  - **Fetch**: 秒级抓取轻量级博客/文档。
  - **Playwright**: 攻克动态渲染和反爬虫严重的复杂网页。
  - **Context7**: 直接连接官方文档库（如 React, Python 官方文档），获取最权威解释。

### 3. 🗺️ 动态路书系统 (Dynamic Roadmap)
- **自动规划**：扔给它一个 URL，它自动生成分阶段的 `book/roadmap.md` 学习计划。
- **状态追踪**：内置 `ProgressManager`，自动记录 `[x]` 完成状态。哪怕隔了一周再回来，只需说“继续学习”，它也能精准接上进度。

### 4. 🧩 技能热插拔 (Skill Sideloading)
- 支持将 `.md` 格式的技能文件直接拖入对话框，智能体可实时解析并安装新能力，无需重启。

---

## 📂 技能架构 (Skill Matrix)

我们的智能体由以下 4 个原子化技能驱动：

| 技能名称 | 路径 | 核心职责 | 依赖工具 |
| :--- | :--- | :--- | :--- |
| **TutorialLoader** | `.trae/skills/TutorialLoader` | **[入口]** 联网抓取教程/文档，清洗数据。 | Fetch, Playwright, Context7 |
| **CurriculumDesigner** | `.trae/skills/CurriculumDesigner` | **[大脑]** 将清洗后的文本转化为结构化路书。 | (Native) |
| **ProgressManager** | `.trae/skills/ProgressManager` | **[记忆]** 读取/更新 `roadmap.md` 的 Checkbox 状态。 | (Native) |
| **KnowledgeArchivist** | `.trae/skills/KnowledgeArchivist` | **[归档]** 生成学习笔记，触发进度打钩。 | (Native) |

---

## 🚀 快速开始 (Quick Start)

### Step 1: 准备环境
确保你的 Trae IDE 已开启 **MCP 功能**，并建议开启以下工具以获得最佳体验：
- ✅ `github.com` (可选，仅用于高级同步)
- ✅ `fetch` (必须)
- ✅ `playwright` (强烈推荐)
- ✅ `context7` (推荐，用于查官方文档)

### Step 2: 唤醒导师
在 Trae 的对话框中输入：
> **"初始化环境"**

*智能体将检测你的环境。如果是新电脑，它会提供一行代码，点击运行即可完成部署。*

### Step 3: 开始学习流程
**场景 A：我要学这个网页**
> "帮我制定这个教程的学习计划：https://example.com/learn-python"

**场景 B：我要查官方文档**
> "教我 Pandas 的数据清洗功能" (智能体将自动调用 Context7 查阅文档)

**场景 C：继续昨天的进度**
> "继续学习" (智能体将读取 `roadmap.md` 并发布今天的任务)

---

## 📝 目录规范
- `book/` : 存放自动生成的 `roadmap.md` 和学习笔记。
- `test/` : 你的代码练习场（智能体会在此目录下 Review 你的代码）。
- `.trae/skills/` : 智能体的技能库（请勿手动修改，除非通过侧载更新）。

---

## 📜 License
MIT License © 2026 CodeManYsf