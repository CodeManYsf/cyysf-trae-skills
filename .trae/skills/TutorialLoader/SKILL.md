---
name: TutorialLoader
description: 智能内容获取引擎。根据输入类型（URL或关键词），自动调度 Fetch、Playwright 或 Context7 获取高质量学习素材。
---

# 触发条件
当用户表示“我想学这个[URL]”、“搜索关于[Topic]的教程”或“教我[Library]”时。

# 智能路由策略 (Routing Strategy)
智能体需分析用户输入，选择以下一条路径执行：

## 路径 A：用户提供了具体 URL (网页学习模式)
**适用场景**：用户发送了具体的博客、文章或教程链接。

1.  **尝试轻量抓取 (Attempt 1)**:
    - 调用 `fetch` 工具。
    - **判断**：如果返回内容包含大量 Markdown 正文且无报错，直接进入 [Step 3 清洗与移交]。

2.  **降级重装抓取 (Attempt 2 - Fallback)**:
    - 如果 `fetch` 失败（返回 403、内容为空、或只有 "Enable JS" 提示）：
    - 告知用户：“静态抓取受限，正在启动 Playwright 浏览器引擎...”
    - **执行动作**：
      1. `playwright_navigate(url)`: 访问页面。
      2. `playwright_get_visible_text()`: **核心步骤**，获取页面可见文本（这比 HTML 更适合 AI 阅读）。
      3. `playwright_close()`: 释放资源。

## 路径 B：用户仅提供了技术名称/关键词 (官方文档模式)
**适用场景**：用户说“我想学 React”、“教我 Python Pandas”。

1.  **定位文档库**:
    - 调用 `context7` 的 `resolve-library-id`，查找该技术对应的官方文档 ID。
    - *示例：输入 "pandas" -> 获取 ID "pandas"*
    
2.  **检索核心文档**:
    - 调用 `context7` 的 `query-docs`。
    - **Query 建议**：如果是初学，Query 填 "Getting Started" 或 "Core Concepts"；如果是进阶，填具体的知识点。

# Step 3: 清洗与结构化 (Cleaning)
无论数据来自 Fetch、Playwright 还是 Context7，必须进行标准化处理：
- **去噪**：移除导航栏、广告文案、版权声明。
- **保留**：
- 标题 (#, ##)
- 代码块 (```code```) - **这是学习的核心**
- 核心解释文本

# Step 4: 移交规划 (Handover)
数据准备好后，**必须**自动调用 `CurriculumDesigner` 技能。

**调用指令模板**：
> "我已通过 [工具名] 获取了关于 [主题/标题] 的详细资料。
> 资料长度：[X] 字。
> 请根据以下清洗后的内容，为用户生成分步学习路书 (roadmap.md)：
>
> [在此处插入清洗后的正文内容]"
