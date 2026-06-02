# 代码编写


---

## 1 分类简介

无论是构建 Web 应用、嵌入式系统还是简单的脚本，**代码编写**是开发者最基础的工作。这个分类覆盖了从通用编辑器到环境管理再到语言专用 IDE 的全链路。

!!! tip ""
    如果你还不确定该从哪里开始：
    - 新手学 C/C++ → [Code::Blocks](gen_ide/code_blocks.md) 或 [Dev-C++](lang_ide/dev_cpp.md)
    - 学生学 Python → [Thonny](lang_ide/thonny.md) 或 [PyCharm](lang_ide/pycharm.md)
    - Web 全栈开发 → [VS Code](gen_ide/visual_studio_code.md)
    - .NET / C# / C++ 大型项目 → [Visual Studio](gen_ide/visual_studio.md)
    - 跨平台 C++ 专业开发 → [CLion](lang_ide/clion.md)
    - AI 辅助编码 → [Cursor](gen_ide/cursor.md)
    - 数值计算与算法仿真 → [MATLAB](lang_ide/matlab.md)



## 2 为什么需要这些工具

| 场景 | 痛点 | 解决工具 |
|------|------|---------|
| 在多种语言间切换 | 需要为不同语言配置不同的工作台环境 | 通用 IDE（VS Code 等）一套走天下，专用 IDE 无缝衔接 |
| 新机器装开发环境 | JDK / Node / Python / MinGW 逐个安装配置，版本冲突 | 环境配置工具一键管理 |
| 主攻一门语言 | 通用 IDE 能用但不够深入 | 专用 IDE 在该语言的调试、重构和框架集成上显著优胜 |



## 3 子分类速览

### 3.1 通用 IDE

不分语言，用插件武装的全功能编辑器。适合：**全栈开发 / 多语言 / 前端工程师**。

| 工具 | 一句话 |
|------|--------|
| VS Code | 全球最流行的代码编辑器，插件生态 40000+ |
| Visual Studio | Windows 上 .NET/C++ 的王者，调试器无可替代 |
| Eclipse | 老牌 Java 企业开发环境，Jakarta EE 首选 |
| Code::Blocks | 轻量级 C/C++，教学竞赛经典 |
| Cursor | 将 AI 聊天、智能补全和内联编辑融入编辑器的原生体验 |

> [进入通用 IDE 分类](gen_ide/index.md)

### 3.2 环境配置

IDE 之外的运行时和安装器，决定项目从克隆到运行需要几步。

| 工具 | 一句话 |
|------|--------|
| Node.js | JavaScript 运行时，npm/pnpm/yarn 包管理器的依赖根基 |
| VS Installer | Visual Studio 的模块化安装器，只装你需要的工作负载 |
| JetBrains Toolbox | 集中管理 PyCharm / CLion 等 IDE 的安装、更新和授权 |
| Anaconda | Python 数据科学环境管理器，NumPy / Pandas 一键配齐 |

> [进入环境配置分类](manage/index.md)

### 3.3 单语言专用 IDE

为特定语言深度定制，调试器和框架集成超越通用 IDE。

| 工具 | 语言 | 一句话 |
|------|------|--------|
| PyCharm | Python | Django / Jupyter / 科学计算深度内置 |
| CLion | C/C++ | CMake 原生集成，Sanitizer 可视化 |
| MATLAB | MATLAB / Simulink | 数值计算、算法仿真、控制系统的学术/工业标准 |
| Dev-C++ | C/C++ | C 语言入门教学经典，体积极小 |
| Thonny | Python | Python 零基础教学 IDE，变量可视化步进调试 |
| Arduino IDE | C++ (Arduino) | 嵌入式入门首选，一键编译上传 |

> [进入单语言专用 IDE 分类](lang_ide/index.md)



## 4 按语言推荐 IDE

| 开发语言 | IDE 推荐 |
|---------|---------|
| C / C++（Windows） | Visual Studio → CLion → Code::Blocks |
| C / C++（Linux / macOS） | CLion → VS Code + Clangd |
| C / C++（教学 / 竞赛） | Code::Blocks → Dev-C++ |
| Python（Web / 通用） | PyCharm → VS Code |
| Python（入门 / 教学） | Thonny → PyCharm |
| Python（数据科学） | PyCharm Professional → VS Code + Jupyter |
| .NET / C# | Visual Studio（Windows）/ Rider（跨平台） |
| Java / Spring | VS Code + Extension Pack → IntelliJ IDEA |
| JavaScript / TypeScript | VS Code（无争议） |
| MATLAB / Simulink | MATLAB（无替代） |
| Arduino / 嵌入式 | Arduino IDE → PlatformIO |
| 纯教学 / 入门学习 | Thonny → Code::Blocks → Dev-C++ |

---

> [回到工具首页](../index.md)
