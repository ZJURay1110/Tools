# 通用 IDE
*跨语言集成开发环境，通过插件生态覆盖多语言开发工作流*


---

## 前言

通用 IDE 是指不绑定单一编程语言的集成开发环境。它们的共同特征是：提供编辑器核心 + 插件系统 + 统一的工作区管理，由用户按需安装语言支持。与"单语言专用 IDE"（如 PyCharm 仅面向 Python）不同，通用 IDE 的设计目标是在一个窗口中完成前端、后端、数据库、脚本等各种语言的混合开发。

这类工具是大多数开发者的日常工作台。选择一个合适的通用 IDE，并投入时间熟悉它的快捷键和插件生态，是提高编码效率最具性价比的投资之一。

!!!

## 1 本类目收录工具

| 工具名称 | 一句话描述 | 平台 | 许可证 |
|---------|-----------|------|--------|
| [Visual Studio Code](visual_studio_code.md) | 微软开源跨平台编辑器，拥有全球最大的插件生态 | Windows / macOS / Linux | MIT（免费） |
| [Visual Studio](visual_studio.md) | 微软 Windows 平台旗舰 IDE，深度绑定 .NET 和 C++ | Windows / macOS（减配） | Community 免费 |
| [Eclipse](eclipse.md) | 老牌 Java IDE，OSGi 插件架构奠基者，企业级广泛使用 | Windows / macOS / Linux | EPL（免费） |
| [Code::Blocks](code_blocks.md) | 轻量 C/C++ IDE，启动极快，面向教学和算法竞赛 | Windows / macOS / Linux | GPLv3（免费） |
| [Cursor](cursor.md) | AI 原生编辑器，基于 VS Code，深度集成 LLM 代码辅助 | Windows / macOS / Linux | 免费 + Pro $20/月 |

## 2 快速选择指南

### 2.1 按使用场景推荐

| 场景 | 推荐工具 | 理由 |
|------|---------|------|
| 前端开发（React / Vue / TS） | VS Code | 最快启动 + 最丰富的 Web 插件 |
| .NET / C# 企业开发 | Visual Studio 2022 | 顶级 .NET 调试 + XAML 设计器 |
| Java 大型企业应用 | Eclipse 或 IntelliJ IDEA Ultimate | Jakarta EE 原生态支持 |
| C++ 大型项目（Unreal 引擎等） | Visual Studio 2022 | MSVC 编译器的原生集成 |
| 同时使用多种 JetBrains IDE | JetBrains Toolbox | 统一版本和授权管理 |
| 希望 AI 深度参与编码 | Cursor | AI 内联编辑 + 多文件生成 |
| 学生初学 C/C++ | Code::Blocks | 体积极小、启动快、免费 |
| 跨平台 Java 开发 | VS Code + Extension Pack for Java | 速度优于 Eclipse |

### 2.2 按技术栈推荐

```
Web 全栈（JS/TS + Node.js）  →  VS Code
.NET 全栈（C# + ASP.NET）     →  Visual Studio 2022
Java 企业（Spring Boot）     →  VS Code 或 IntelliJ IDEA
C++ 系统开发（Windows）       →  Visual Studio 2022
C++ 跨平台（Linux/macOS）    →  CLion（JetBrains）或 VS Code + Clangd
C/C++ 教学 / ACM 竞赛        →  Code::Blocks
```

## 3 各工具详细对比

| 对比维度 | VS Code | Visual Studio | Eclipse | Code::Blocks |
|---------|---------|--------------|---------|-------------|
| 安装体积 | ~300 MB | 4-20 GB | ~500 MB | ~150 MB |
| 启动时间（冷启动） | 2-4 秒 | 10-30 秒 | 10-20 秒 | 1-2 秒 |
| 代码补全（语义级） | LSP（需配置） | IntelliSense（优秀） | JDT（Java 优秀） | 标签解析（基础） |
| Git 集成 | 内置 | 内置 | EGit（内置） | 需插件 |
| 内置终端 | 有 | 有 | 有 | 无 |
| 调试器 | 基础（可扩展） | 顶级 | 良好 | GDB 前端 |
| 内存占用（空项目） | 300-800 MB | 800-2000 MB | 500-800 MB | 40-80 MB |
| 学习曲线 | 低 | 中 | 陡 | 低 |

!!! note "关于 Cursor 的说明"
    Cursor 没有单独出现在上面的对比表中，因为就编辑体验而言它和 VS Code 基本一致（基于同一代码库）。Cursor 的差异在 AI 能力上，详见 [Cursor](cursor.md) 页面。

---

## 相关资源

- [Stack Overflow 2024 Developer Survey](https://survey.stackoverflow.co/2024/)
- [JetBrains 开发者生态系统调查](https://www.jetbrains.com/lp/devecosystem-2024/)
