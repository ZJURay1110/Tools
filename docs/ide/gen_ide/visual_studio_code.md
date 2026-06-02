# Visual Studio Code
*微软开源跨平台代码编辑器，通过插件生态覆盖全语言开发*


---

## 前言

Visual Studio Code（简称 VS Code）是目前全球开发者中使用率最高的代码编辑器。它由 Microsoft 开发和维护，基于 Electron 框架构建，采用 MIT 许可证完全开源。尽管本质是一个 Web 技术构建的桌面应用，但通过 **LSP（Language Server Protocol，语言服务协议）** 和 **DAP（Debug Adapter Protocol，调试适配器协议）**，它能提供逼近传统重型 IDE 的代码补全、重构与调试体验。

VS Code 的核心理念是 **"编辑器即平台"**：本体保持轻量（约 200-300 MB 安装后），所有语言支持和扩展功能通过 Marketplace 的插件按需安装。这让它能同时胜任一个简单的 Markdown 笔记编辑器，和一个包含数十个微服务的大型 TypeScript 工程主开发环境。

**本机版本：** 1.98.2  
**平台：** Windows / macOS / Linux  
**许可证：** MIT（免费开源）  

!!!

## 1 概述

### 1.1 历史与定位

VS Code 于 2015 年 4 月 29 日在 Build 大会上首次发布。彼时前端编辑器市场由 Sublime Text 和 Atom 主导，但 Sublime 的更新节奏缓慢、Atom 性能欠佳。VS Code 的快速迭代（每月一个大版本）和 TypeScript 原生支持迅速赢得了开发者社区。

至 2024 年，Stack Overflow 开发者调查显示超过 74% 的受访者将 VS Code 作为首选编辑器。

!!! note "VS Code 不等于 Visual Studio"
    Visual Studio 是微软的全功能 IDE（见本目录下 `visual_studio.md`），体积达 4-20 GB，深度绑定 .NET/C++ 工作流。VS Code 则是轻量编辑器，侧重"可组装"的灵活性。

## 2 核心功能

### 2.1 IntelliSense 智能代码补全

VS Code 的代码补全系统叫 IntelliSense。它不只是简单的关键字匹配，而是通过语言服务协议在后台运行对应语言的 Language Server，实时分析项目代码结构，提供以下能力：

- **基于语义的补全**：理解变量类型、函数签名、类继承关系
- **参数提示**：调用函数时显示参数名称和类型
- **快速信息**：悬停变量/函数时显示文档注释
- **导入自动管理**：使用未导入的类型时自动添加 import 语句

在 TypeScript 项目中，这个体验尤为突出。对于 Python，安装 Pylance 插件后能获得同等级别的智能提示。

### 2.2 调试器集成

VS Code 内置了图形化调试系统，支持以下调试操作：

- 断点（行断点、条件断点、日志点、命中计数断点）
- 单步执行（逐过程 / 逐语句 / 跳出）
- 变量查看器（局部变量 / 全局变量 / 监视表达式）
- 调用堆栈查看与导航
- 调试控制台（交互式 REPL）

内置支持 Node.js / JavaScript / TypeScript 调试。通过扩展可支持：

| 语言 | 推荐调试扩展 |
|------|-------------|
| Python | Python Debugger |
| C / C++ | C/C++ (Microsoft) |
| Java | Debugger for Java |
| Go | Go |
| Rust | rust-analyzer（内建） |

### 2.3 内置 Git 集成

VS Code 的源代码管理面板提供了图形化的 Git 操作界面，不需要打开终端：

- 查看文件修改状态（M / A / D / U 标记）
- 逐行 staged 修改（Stage Selected Ranges）
- 差异对比编辑器（Side-by-Side Diff View）
- 内联 blame 注释（通过 GitLens 插件）
- 分支创建、切换、合并
- 远程仓库推送与拉取
- 冲突解决（3-way merge editor）

!!! tip "增强 Git 体验"
    强烈推荐安装 **GitLens** 插件。它可以在每一行末尾显示该行最后的提交者和时间，精确到每一次 commit 的责任追溯。

### 2.4 集成终端

在 VS Code 中按 `` Ctrl+` `` 可以打开内嵌终端。这个终端与操作系统的 Shell 一致：

- Windows 下默认 PowerShell，可切换为 Git Bash 或 WSL
- 支持多终端实例分屏
- 终端的输出可以被选中复制
- 终端中的文件路径和错误信息可以 Ctrl+Click 跳转

常用终端操作：

| 操作 | 快捷键 |
|------|-------|
| 打开终端 | Ctrl+` |
| 新建终端 | Ctrl+Shift+` |
| 切换终端 | Ctrl+PageUp / PageDown |
| 增大字号 | Ctrl+数字键盘+ |
| 减小字号 | Ctrl+数字键盘- |

### 2.5 远程开发

这是 VS Code 最具差异化竞争力的功能之一。通过 3 个官方扩展，开发者可以在不同环境中编码，但编辑体验完全一致：

- **Remote-SSH**：通过 SSH 连接远程 Linux 服务器，所有代码在远端运行，本地只需 VS Code 的 UI
- **Remote-Containers**：项目代码在 Docker 容器中编译运行，通过 `devcontainer.json` 定义环境，实现"克隆即就绪"的开发体验
- **Remote-WSL**：在 Windows 上的 WSL（Linux 子系统）中运行代码，比虚拟机更轻量

## 3 安装与配置

### 3.1 系统需求

- **操作系统**：Windows 10/11、macOS 11+、Linux（Debian / Ubuntu / RHEL / Fedora / openSUSE）
- **内存**：最低 1 GB（推荐 4 GB 以上）
- **磁盘**：安装约 300 MB，插件和缓存额外占用视使用而定

### 3.2 安装步骤

**Windows 安装（推荐 System Installer）**

1. 访问 [https://code.visualstudio.com/download](https://code.visualstudio.com/download)
2. 下载 **System Installer** 64-bit 版本（User Installer 安装到 AppData，不方便被其他用户使用）
3. 运行安装程序，在 "选择其他任务" 页面，**强烈建议勾选以下选项**：

   - `将 "通过 Code 打开" 操作添加到 Windows 资源管理器文件上下文菜单`
   - `将 "通过 Code 打开" 操作添加到 Windows 资源管理器目录上下文菜单`
   - `将 Code 注册为受支持的文件类型的编辑器`
   - `添加到 PATH（需要重新启动 shell）`

4. 安装完成后，在任意目录右键 → "通过 Code 打开" 即可启动

!!! warning "安装路径注意事项"
    System Installer 默认安装到 `C:\Program Files\Microsoft VS Code\`。如果磁盘空间紧张，也可以选择 Portable 模式：下载 `.zip` 版本解压到任意位置，在根目录手动创建 `data` 文件夹，所有配置和插件都会保存在该文件夹下，方便 U 盘携带。

### 3.3 必备插件推荐

插件市场入口：左侧活动栏 → Extensions 图标（`Ctrl+Shift+X`）

| 类别 | 插件名 | 用途 |
|------|--------|------|
| 语言 | Pylance | Python 类型检查与智能补全 |
| 语言 | C/C++ (Microsoft) | C/C++ IntelliSense 与调试 |
| 格式 | Prettier | 代码格式化，保存时自动触发 |
| 代码质量 | ESLint | JavaScript/TypeScript Linting |
| Git | GitLens | Git 历史追溯，行级 blame |
| 图标 | Material Icon Theme | 文件/文件夹图标美化 |
| 协作 | Live Share | 实时结对编程 |
| 容器 | Dev Containers | Docker 容器内开发 |
| 远程 | Remote-SSH | 远程服务器开发 |
| 颜色 | Color Highlight | CSS 颜色值可视化 |

### 3.4 常用配置

打开 Settings UI（`Ctrl+,`）或 Settings JSON（`Ctrl+Shift+P` → 搜索 `settings.json`）：

```jsonc
{
    // 编辑器基础
    "editor.fontSize": 14,
    "editor.fontFamily": "'Cascadia Code', Consolas, 'Courier New', monospace",
    "editor.tabSize": 2,
    "editor.insertSpaces": true,
    "editor.formatOnSave": true,
    "editor.minimap.enabled": false,        // 建议关闭小地图节省空间
    "editor.renderWhitespace": "boundary",   // 仅显示单词间多余空格
    "editor.bracketPairColorization.enabled": true,

    // 文件管理
    "files.autoSave": "afterDelay",          // 1秒后自动保存
    "files.exclude": {                       // 搜索时排除的目录
        "**/node_modules": true,
        "**/dist": true,
        "**/build": true
    },

    // 搜索排除
    "search.exclude": {
        "**/node_modules": true,
        "**/dist": true
    },

    // 工作区外观
    "workbench.colorTheme": "Default Dark Modern",
    "workbench.iconTheme": "material-icon-theme",
    "workbench.startupEditor": "none",       // 启动时不打开欢迎页

    // 终端
    "terminal.integrated.fontSize": 13,
    "terminal.integrated.defaultProfile.windows": "PowerShell"
}
```

!!! tip "关于字体"
    Cascadia Code 是微软专为开发者设计的等宽字体，支持连字（ligatures），将 `=>`、`!=`、`>=` 等符号渲染为更美观的合字。如果不习惯也可以使用 Fira Code、JetBrains Mono、Source Code Pro 等替代。

### 3.5 命令行入口

安装完成后，在任意终端中：

```bash
# 打开当前目录
code .

# 打开指定文件
code app.js

# 对比两个文件
code -d file1.txt file2.txt

# 安装指定插件（CI/CD 场景常用）
code --install-extension ms-python.python
```

## 4 常用操作

### 4.1 核心快捷键速查

| 操作 | Windows / Linux | macOS |
|------|----------------|-------|
| 命令面板 | Ctrl+Shift+P | Cmd+Shift+P |
| 快速打开文件 | Ctrl+P | Cmd+P |
| 全局搜索 | Ctrl+Shift+F | Cmd+Shift+F |
| 切换侧边栏 | Ctrl+B | Cmd+B |
| 打开终端 | Ctrl+` | Ctrl+` |
| 代码格式化 | Shift+Alt+F | Shift+Option+F |
| 多光标（鼠标） | Alt+Click | Option+Click |
| 多光标（键盘） | Ctrl+Alt+Up/Down | Cmd+Option+Up/Down |
| 选中所有相同词 | Ctrl+Shift+L | Cmd+Shift+L |
| 批量重命名符号 | F2 | F2 |
| 注释切换 | Ctrl+/ | Cmd+/ |
| 缩进 / 反缩进 | Tab / Shift+Tab | Tab / Shift+Tab |
| 转到定义 | F12 | F12 |
| 查找所有引用 | Shift+F12 | Shift+F12 |
| 打开 Settings | Ctrl+, | Cmd+, |
| 禅模式 | Ctrl+K Z | Cmd+K Z |

### 4.2 多光标与批量编辑（进阶）

这是 VS Code 最强大的编辑特性之一：

```javascript
// 场景：已有以下三个变量的赋值语句，需要在每个变量前加 const
// 原始代码：
a = 1;
b = 2;
c = 3;

// 操作：按住 Alt，分别点击 a、b、c 前的位置
// 然后输入 const
// 结果：
const a = 1;
const b = 2;
const c = 3;

// 或者用 Ctrl+Shift+L 一次性选中所有出现的 "= " 进行替换
```

### 4.3 用户代码片段（Snippet）

定义常用的代码模板以提高效率。以 JavaScript 为例，新建 `javascript.json` 片段文件：

```jsonc
{
    "Define Function": {
        "prefix": "Func",               // 触发词
        "body": [
            "function ${1:Name}(${2:args}) {",
            "\t${3: // 函数体}",
            "\treturn ${4:result};",
            "}"
        ],
        "description": "创建具名函数"
    }
}
```

在 `.js` 文件中输入 `Func` 然后 Tab，自动展开为函数模板。

## 5 高级功能

### 5.1 Tasks（任务自动化）

任务允许在 VS Code 内直接调用外部工具（编译器、打包器、测试运行器），替代在终端中手动输入命令。

配置 `.vscode/tasks.json`：

```jsonc
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "TypeScript Build",
            "type": "typescript",
            "tsconfig": "tsconfig.json",
            "problemMatcher": ["$tsc"],
            "group": {
                "kind": "build",
                "isDefault": true
            }
        },
        {
            "label": "Run Tests",
            "type": "shell",
            "command": "npm test",
            "group": "test",
            "presentation": {
                "reveal": "always",
                "panel": "new"
            }
        }
    ]
}
```

之后按 `Ctrl+Shift+B` 触发默认构建任务。

### 5.2 Multi-root Workspaces（多根工作区）

当需要同时编辑多个不相关的项目时（如前端和后端代码分属两个仓库），可以创建 `.code-workspace` 文件：

```jsonc
{
    "folders": [
        { "name": "Frontend (React)", "path": "./frontend" },
        { "name": "Backend (Express)", "path": "./backend" }
    ],
    "settings": {
        // 工作区级别的设置
        "typescript.tsdk": "./frontend/node_modules/typescript/lib"
    }
}
```

这个功能是 VS Code 区别于大多轻量编辑器的关键差异化特性。

### 5.3 Setting Sync（设置同步）

登录 Microsoft 或 GitHub 账号后，VS Code 的配置、插件、快捷键和代码片段会自动在多台设备间同步。

!!! warning "敏感项目注意"
    Setting Sync 会将插件列表和配置同步，但不会同步项目源代码。如果你的 settings.json 中包含服务器 IP、密钥等敏感信息，建议使用 `Settings Profile`（设置配置文件）分离个人设置和工作设置。

## 6 同类对比

| 对比维度 | VS Code | Sublime Text 4 | Vim / Neovim | 重量级 IDE（IntelliJ 等） |
|---------|---------|--------------|-------------|-------------------------|
| 启动速度 | 2-4 秒 | 接近瞬时 | 瞬时 | 10-30 秒 |
| 内存占用 | 300-800 MB | 100-300 MB | 10-50 MB | 1-4 GB |
| 代码补全 | 优秀（LSP） | 基础（需插件） | 需配置 LSP | 顶尖（专有引擎） |
| Git 集成 | 内置 | 无（插件） | 无/终端 | 优秀（内置） |
| 远程开发 | 原生支持 | 不支持 | SSH 终端 | 部分支持 |
| 插件生态 | 极丰富（4 万+） | 丰富 | 丰富（Lua 脚本） | 较丰富 |
| 学习曲线 | 低 | 中 | 高 | 中 |
| 免费 / 付费 | 免费 | $99（可无限试用） | 免费 | Community 免费 / $249/年 |

## 7 注意事项

!!! warning "C/C++ 项目注意事项"
    如果你的 C++ 项目使用 Visual Studio 编译（MSVC），建议直接在 Visual Studio 中编辑。VS Code 的 C++ IntelliSense 需要手动配置 `c_cpp_properties.json` 中的 include path，且在大型模板项目（如 UE 引擎）中容易索引不完整。

!!! danger "中文路径编码问题"
    VS Code 的终端在 Windows 下如果使用 GBK 编码（CMD 默认）可能在集成终端中显示中文乱码。解决方法：`Ctrl+Shift+P` → "Terminal: Select Default Profile" → 选择 PowerShell（UTF-8）。

!!! info "Portable 模式"
    如果需要在没有管理员权限的电脑上使用，或者想将完整环境放在 U 盘。下载 `.zip` 版本，解压后在根目录创建 `data` 文件夹。之后所有安装的插件、修改的设置都保存在 `data` 下，不影响宿主机。

---

## 参考资源

- [VS Code 官网](https://code.visualstudio.com/)
- [VS Code 文档](https://code.visualstudio.com/docs)
- [VS Code Marketplace](https://marketplace.visualstudio.com/vscode)
- [GitHub 仓库](https://github.com/microsoft/vscode)
- [LSP 协议规范](https://microsoft.github.io/language-server-protocol/)
