# AI 工具

---

## 1 分类简介

大语言模型正在改变开发者的工作方式。从对话式编程助手到智能编码代理，再到 API 中转服务，这个分类收录了当前 AI 开发生态中最实用的工具。

!!! tip ""
    根据场景快速选择：
    - 对话式编程助手 → [ChatGPT](gpt/chatgpt.md) 或 [Claude](claude/claude.md)
    - 用 API 做自动化 → [GPT API](gpt/gpt_api.md) 或 [Claude API](claude/claude_api.md)
    - 编辑器中内嵌 AI 补全 → [GitHub Copilot](agents/github_copilot.md) 或 [Cursor](agents/cursor.md)
    - 多模型统一管理 → [One API](proxy/one_api.md) 或 [Cloudflare AI Gateway](proxy/cloudflare_ai_gateway.md)
    - 国产开源模型 → [DeepSeek](deepseek/deepseek_chat.md)
    - 一次编写多模型切换 → [Vercel AI SDK](proxy/vercel_proxy.md)

---

## 2 为什么需要这些工具

| 场景 | 痛点 | 解决工具 |
|------|------|---------|
| 需要 AI 回答编程问题 | 在浏览器和编辑器之间反复复制粘贴 | 编辑器内嵌 AI 聊天，上下文自动关联当前文件 |
| 写重复性代码（模板、测试） | 手动逐行编写耗时且易出错 | AI 补全和内联编辑自动生成 |
| 多个项目使用不同模型 | 每个模型注册不同的 API Key，接口不统一 | API 中转工具统一接入层 + 用量监控 |
| 海外 API 延迟高 / 不可达 | 直接调用 OpenAI / Claude 被限速 | 中转工具多路转发 + 缓存 + 负载均衡 |
| 想用本地模型但搭建复杂 | 需要配置 GPU 驱动、模型下载、API 服务 | AI 编码代理支持切换本地推理后端 |

---

## 3 子分类速览

### 3.1 GPT / OpenAI

OpenAI 系列模型与平台生态，ChatGPT 对话界面和 GPT API 开发能力。

| 工具 | 一句话 |
|------|--------|
| ChatGPT | OpenAI 官方对话界面，自动代码分析和优化指令 |
| GPT API | 调用 GPT-4o / o1 等模型的通用编程接口 |
| OpenAI Platform | 模型管理、Fine-tuning、用量监控的统一面板 |

> [进入 OpenAI 生态分类](gpt/index.md)

### 3.2 Google AI

Google 推出的 Gemini 系列模型和 AI Studio 开发平台。

| 工具 | 一句话 |
|------|--------|
| Gemini | Google 多模态大模型，原生图像理解能力最强 |
| Gemini API | Google AI 模型的 REST 接口，免梯子直连 |
| Google AI Studio | 在线 Prompt 调试和 API Key 管理的浏览器工作台 |

> [进入 Google AI 生态分类](google/index.md)

### 3.3 Claude / Anthropic

Anthropic 出品的 Claude 系列模型，代码生成和理解能力突出。

| 工具 | 一句话 |
|------|--------|
| Claude | 擅长长上下文 + 代码生成，3.5 Sonnet / 4 Opus 是编码神器 |
| Claude API | Anthropic API，支持 Messages API 和 Tool Use |
| Anthropic Console | Prompt 测试、Workbench 和改进分析的工作台 |

> [进入 Anthropic 生态分类](claude/index.md)

### 3.4 DeepSeek

国产开源大模型，性价比突出，自托管方案成熟。

| 工具 | 一句话 |
|------|--------|
| DeepSeek Chat | DeepSeek 官方对话界面，免费使用 |
| DeepSeek API | 国产竞品中最便宜的 API，兼容 OpenAI 接口格式 |

> [进入 DeepSeek 生态分类](deepseek/index.md)

### 3.5 AI 编码代理

将 AI 嵌入编辑器工作流的编码助手，从自动补全到生成整个文件。

| 工具 | 一句话 |
|------|--------|
| GitHub Copilot | 最早的 AI 代码补全，VS Code / JetBrains 等 IDE 全覆盖 |
| Cursor | AI 原生编辑器，内联编辑 + Composer 多文件生成 |
| Windsurf | 类似 Cursor 的 AI 编辑器，Cascade 模式自动分析 -->
| Cline | VS Code 插件，终端命令自动执行和文件自主编辑 |
| Roo Code | Cline 的增强分支，支持 MCP 工具拓展 |

> [进入 AI 编码代理分类](agents/index.md)

### 3.6 API 中转代理

多模型统一接入层，管理 API Key、监控用量、做负载均衡。

| 工具 | 一句话 |
|------|--------|
| OpenAI Translator | 用 ChatGPT API 做翻译 / 润色的 Chrome 扩展 |
| Vercel AI SDK | 前端一键接入多模型 AI 的 React Hooks 库 |
| Cloudflare AI Gateway | Cloudflare 全球边缘网关托管 AI API 路由 |
| One API | 自托管的多模型 API 网关，统一 OpenAI / Claude / 国内模型 |

> [进入 API 中转代理分类](proxy/index.md)

---

> [回到工具首页](../index.md)
