# ai — AI 工具

## 定位

收录 AI 大语言模型相关的平台与服务工具，按模型提供方、开发辅助代理、API 中转软件分类。

## 子分类目录结构

```
ai/
├── gpt/                      # OpenAI 生态
│   ├── chatgpt.md
│   ├── gpt_api.md
│   └── openai_platform.md
├── google/                   # Google AI 生态
│   ├── gemini.md
│   ├── gemini_api.md
│   └── google_ai_studio.md
├── claude/                   # Anthropic 生态
│   ├── claude.md
│   ├── claude_api.md
│   └── anthropic_console.md
├── deepseek/                 # DeepSeek 生态
│   ├── deepseek_chat.md
│   └── deepseek_api.md
├── agents/                   # AI 编码代理与开发工具
│   ├── github_copilot.md
│   ├── cursor.md
│   ├── windsurf.md
│   ├── cline.md
│   └── roo_code.md
└── proxy/                    # API 中转代理软件
    ├── openai_translator.md
    ├── vercel_proxy.md
    ├── cloudflare_ai_gateway.md
    └── one_api.md
```

## 编写要点

- 对话平台说明模型列表、上下文窗口、多模态支持
- API 工具说明定价、速率限制、SDK 语言支持
- Agents 工具对比 IDE 集成方式、补全质量、自定义配置能力
- 中转软件说明支持的协议转换（如 OpenAI API → 其他后端）
