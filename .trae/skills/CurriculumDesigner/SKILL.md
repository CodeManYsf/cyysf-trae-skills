---
name: CurriculumDesigner
description: 将教程内容转化为分步学习路书 (book/roadmap.md)。
---

# 触发条件
被 `TutorialLoader` 调用，或用户明确要求“制定计划”。

# 核心文件
- **路书**: `book/roadmap.md`

# 执行逻辑

## Step 1: 分析与拆解
阅读输入的教程内容，将其拆解为 3-10 个合理的学习阶段（Phase）。

## Step 2: 创建路书 (Initialize Roadmap)
在 `book/` 目录下创建（或覆盖）`roadmap.md` 文件。
**必须严格遵守以下 Checkbox 格式**，以便 ProgressManager 读取：

```markdown
# 🗺️ 学习路书：[教程标题]

## Phase 1: 基础概念
- [ ] 01. [知识点名称] - [简短描述]
- [ ] 02. [知识点名称] - [简短描述]

## Phase 2: 核心实战
- [ ] 03. [知识点名称]...

## Step 3: 启动第一课
告知用户：“路书已生成。根据计划，我们先开始第一部分：[Task 01 名称]。请看以下说明...”

---
