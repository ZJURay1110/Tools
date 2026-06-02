# Code::Blocks
*轻量级开源 C/C++ IDE，面向教学场景和算法竞赛，启动迅速，无需庞大运行时依赖*


---

## 前言

Code::Blocks 是一款用 C++ 编写的跨平台 IDE，专为 C 和 C++ 开发设计。它诞生于 2005 年，由开发者社区维护。与 Visual Studio（需要 4-20 GB 磁盘空间和 Windows 许可证）或 CLion（需要付费授权和 Java 运行时）不同，Code::Blocks 的安装包只有约 100 MB，启动只需 1-2 秒，几乎不占用后台资源。

它在中国大学 ACM/ICPC 竞赛圈中使用率较高，也是很多 CS 专业本科生的第一个 C/C++ IDE。

**本机版本：** 20.03  
**平台：** Windows / Linux / macOS  
**许可证：** GPLv3（完全免费开源）

!!! warning "版本更新缓慢"
    当前最新稳定版 20.03 发布于 2020 年 3 月，已 5 年未发布新主版本。NIGHTLY 构建（每日构建版）在持续更新中，但稳定性不如正式版。如果你需要 C++20/23 标准特性，Code::Blocks 不是最佳选择（考虑 CLion 或 VS Code + CMake + Clangd）。

---

## 1 概述

### 1.1 核心特点

- **纯 C++ 编写**：不依赖 Java、.NET 或 Electron 运行时。Windows 下仅需一个 MinGW 编译器即可工作
- **插件驱动**：几乎所有功能（包括编译器支持、调试器集成、GUI 设计器 wxSmith）都以插件形式实现
- **多编译器支持**：不绑定特定编译器，可以在 GCC、MinGW、Clang、MSVC、Borland 等之间自由切换
- **项目管理**：支持单文件编译和复杂的多项目工作空间

### 1.2 重要：Code::Blocks 不包含编译器

下载 Code::Blocks 后你还需要一个 C++ 编译器才能编译代码。官网提供了两种安装包：

| 安装包类型 | 文件名示例 | 说明 |
|-----------|-----------|------|
| 含 MinGW 的安装包 | `codeblocks-20.03mingw-setup.exe` | 推荐新手使用，自带 GCC 编译器 |
| 不含编译器的裸包 | `codeblocks-20.03-setup.exe` | 适合已有 MinGW 或习惯手动配置的用户 |

!!! danger "不要下载裸包然后困惑为什么不能编译"
    这是新手最常见的困惑来源。如果你下载了不含 MinGW 的版本，新建项目后按 F9 构建会提示 "Can't find compiler executable"。解决方法：下载含 MinGW 的版本重装，或者手动下载 MinGW-w64 并在 Code::Blocks 中配置工具链路径。

## 2 核心功能

### 2.1 项目和文件管理

Code::Blocks 使用 `.cbp`（Code::Blocks Project）文件管理项目。一个项目包含：

- 源文件（`.c` / `.cpp` / `.h`）
- 编译选项（Debug/Release 配置）
- 链接库列表
- 构建前/后脚本

支持的工作空间（`.workspace`）可以同时管理多个 `.cbp` 项目，类似于 Visual Studio 的 Solution。

### 2.2 代码编辑器

Code::Blocks 的编辑器基于 Scintilla 组件（Notepad++ 也使用同一组件），支持：

- 语法高亮（C/C++ 效果好，其他语言依赖插件）
- 代码折叠、括号匹配
- 代码补全（基于标签解析，而非 Clangd 那样的语义分析）
- 符号浏览器（Symbol Browser）：查看当前文件或项目的类、函数、全局变量列表

!!! info "代码补全的局限性"
    Code::Blocks 的代码补全基于 ctags 方式（标签解析），不进行完整的语义分析。在处理模板、宏、类型别名时，补全准确率明显低于 CLion（基于 Clangd）或 VS Code（Clangd 插件）。对于 STL 容器和 C++11/14/17 新特性，补全可能失效。

### 2.3 编译器切换

Code::Blocks 的独特功能之一是可以为同一个项目的不同构建目标（Build Target）指定不同的编译器。例如：

| Build Target | 编译器 | 用途 |
|-------------|--------|------|
| Debug (MinGW) | MinGW GCC | Windows 本地调试 |
| Release (MinGW) | MinGW GCC + -O2 | 发布优化版本 |
| Release (MSVC) | Microsoft Visual C++ | 测试 MSVC 兼容性 |

### 2.4 调试器

通过集成的 GDB 前端，支持标准调试操作：

- 行断点、条件断点
- 变量查看、表达式监视
- 调用堆栈、反汇编视图
- 内存查看器（Memory Dump）

!!! warning "64 位程序调试"
    如果你编译的是 64 位程序，需要使用 64 位版本的 GDB（MinGW-w64 自带）。旧版 MinGW（32 位）自带的 GDB 无法调试 64 位程序。

## 3 安装与配置

### 3.1 系统需求

- **Windows**：Windows 7/8/10/11（32 位或 64 位均可）
- **Linux**：通过包管理器安装（`sudo apt install codeblocks`）
- **macOS**：需要配合 Xcode Command Line Tools 使用
- **磁盘**：约 150 MB（含 MinGW 约 500 MB）

### 3.2 安装步骤（Windows，推荐含 MinGW 版本）

1. 访问 [https://www.codeblocks.org/downloads/binaries/](https://www.codeblocks.org/downloads/binaries/)
2. 找到 `codeblocks-20.03mingw-setup.exe`（注意文件名中有 `mingw`）
3. 下载并运行安装程序
4. 安装路径建议接受默认 `C:\Program Files\CodeBlocks\`
5. 安装时**全选所有组件**（默认已全选，不要取消勾选 MinGW Compiler Suite）

6. 安装完成后首次启动，Code::Blocks 会自动检测到 MinGW 编译器路径并配置。如果出现 "Compiler auto-detection" 对话框，显示的编译器列表中有 "GNU GCC Compiler" 且状态为 "Detected" 即一切正常。

### 3.3 如果编译器未被检测到

自动检测失败时手动配置：

1. Settings → Compiler → Global compiler settings
2. Selected compiler 下拉选 "GNU GCC Compiler"
3. 切换到 Toolchain executables 标签页
4. 设置 Compiler's installation directory 指向 MinGW 目录：
   - 通常为 `C:\Program Files\CodeBlocks\MinGW\`
5. 确认 Program Files 子标签中各项自动填充了正确路径：
   - C compiler: `mingw32-gcc.exe`
   - C++ compiler: `mingw32-g++.exe`
   - Linker for dynamic libs: `mingw32-g++.exe`

!!! note "为什么是 mingw32 而不是 mingw64"
    即使安装的是 MinGW-w64（64 位编译器），可执行文件名仍然是 `mingw32-gcc.exe` 和 `mingw32-g++.exe`。这是 MinGW 的历史命名惯例，不代表这是 32 位编译器。

### 3.4 推荐设置

- **Settings → Editor → General Settings → Encoding**：选择 UTF-8（避免中文注释乱码）
- **Settings → Editor → Margins and caret → Show line numbers**：勾选
- **Settings → Compiler → Compiler settings → Compiler Flags**：勾选以下常用选项：

| 标志 | 含义 |
|------|------|
| `-Wall` | 启用所有常规警告 |
| `-Wextra` | 启用额外警告 |
| `-g` | 生成调试符号 |
| `-std=c++17` | 使用 C++17 标准 |

## 4 常用操作

### 4.1 核心快捷键

| 操作 | 快捷键 |
|------|-------|
| 构建（编译 + 链接） | Ctrl+F9 |
| 运行 | Ctrl+F10 |
| 构建并运行 | F9 |
| 仅编译（不链接） | Ctrl+Shift+F9 |
| 全部重新构建 | Ctrl+F11 |
| 调试 | F8 |
| 继续执行 | Ctrl+F7 |
| 逐过程调试 | F7 |
| 逐语句调试 | Shift+F7 |
| 跳出函数 | Ctrl+Shift+F7 |
| 设置/取消断点 | F5 |
| 注释/取消注释 | Ctrl+Shift+C / Ctrl+Shift+X |
| 搜索 | Ctrl+F |
| 全局搜索 | Ctrl+Shift+F |
| 转到函数定义 | Ctrl+左键单击 |

### 4.2 常见操作流程

**场景 A：新建一个 C++ 控制台项目**

```
1. File → New → Project
2. 选择 "Console application" → Go
3. 语言选择 C++ → Next
4. Project title: my_first_project
5. Folder to create project in: 选择代码存放目录
6. Compiler: GNU GCC Compiler
7. 勾选 Create "Debug" configuration 和 Create "Release" configuration
8. Finish
9. 左侧 Management 面板出现项目树 → 双击 main.cpp 开始编辑
10. F9 构建并运行
```

**场景 B：运行 ACM 竞赛风格的单个 .cpp 文件**

```
1. File → New → Empty file
2. 编写代码后另存为 .cpp 文件
3. Build → Compile current file（Ctrl+Shift+F9）
4. Build → Run（Ctrl+F10）
```

!!! tip "竞赛必备：关闭不必要的 warning 以减少干扰"
    Settings → Compiler → Compiler settings → Compiler Flags → 取消 `-Wall` 和 `-Wextra` 勾选。竞赛代码通常为一次性使用，不需要严格的警告检查。但做工程项目时建议恢复这两个选项。

## 5 同类对比

| 对比维度 | Code::Blocks | Dev-C++ (Embarcadero) | CLion | VS Code + CMake + Clangd |
|---------|-------------|----------------------|-------|--------------------------|
| 启动速度 | 1-2 秒 | 1-2 秒 | 5-10 秒 | 2-4 秒 |
| 安装体积 | 100-500 MB | 50-100 MB | 1-2 GB | 300-500 MB |
| C++ 标准支持 | C++17（依赖编译器） | C++17（依赖编译器） | C++20/23 | C++20/23 |
| 代码补全（语义级） | 基础（标签解析） | 基础 | 顶级（Clangd） | 顶级（Clangd） |
| 跨平台 | 全平台 | Windows 仅 | 全平台 | 全平台 |
| 内存占用（空项目） | 40-80 MB | 30-60 MB | 1-2 GB | 300-800 MB |
| 适用场景 | 教学 / 竞赛 / 轻量开发 | 中学教学 | 专业开发 | 专业开发 |
| 免费 | 免费开源 | 免费（有付费版） | $99/年起 | 免费 |

## 6 注意事项与常见问题

!!! warning "中文路径不要含空格"
    Code::Blocks 的 MinGW 编译器对含空格和中文的文件路径兼容性较差。如果你的项目路径类似 `D:\我的项目\code\` 或 `D:\My Projects\code\`，编译时可能报 "No such file or directory"。解决方法：将所有项目放在纯英文、无空格路径下，如 `D:\code\`。

!!! danger "杀毒软件误报"
    部分杀毒软件（尤其是国产安全软件）会误报 MinGW 的 `gcc.exe` 或 `g++.exe` 为可疑程序。如果在安装或运行时被杀毒软件拦截，需要将 `C:\Program Files\CodeBlocks\MinGW\bin\` 添加到白名单。

!!! info "与 Visual Studio Code 配合使用"
    如果觉得 Code::Blocks 的编辑器功能有限，可以将其仅作为"编译器 + 调试器 GUI"使用：在 VS Code 中编写代码，在 Code::Blocks 中打开同一个 `.cbp` 项目文件进行编译和调试。这样兼顾了编辑器的流畅体验和 IDE 调试功能的便利。

---

## 参考资源

- [Code::Blocks 官网](https://www.codeblocks.org)
- [Code::Blocks Wiki](https://wiki.codeblocks.org)
- [Code::Blocks 下载（含 Nightly 构建）](https://www.codeblocks.org/downloads/binaries/)
- [MinGW-w64 下载（独立安装编译器）](https://www.mingw-w64.org)
