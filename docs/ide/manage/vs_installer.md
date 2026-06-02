# Visual Studio Installer
*Visual Studio 的模块化安装引导工具，负责工作负载选择、组件管理与版本切换*


---

## 前言

Visual Studio 的安装流程与大多数软件不同：你从官网下载的不是 Visual Studio 本体，而是一个约 2 MB 的引导程序，名为 **Visual Studio Installer**。这个安装器负责下载、更新和管理 Visual Studio 的各个工作负载和组件。理解 Visual Studio Installer 的运作方式，是管理 VS 安装的第一步。

由于 Visual Studio 的安装体积高达 4-20 GB，在磁盘空间紧张的笔记本电脑上，正确使用 Installer 选择最小必要组件，可以节省大量磁盘空间。

**本机版本：** Visual Studio 2022  
**平台：** Windows（Visual Studio Installer 仅 Windows 平台）  
**许可证：** 免费

---

## 1 概述

### 1.1 为什么要用 Installer 而非 exe 安装包

Visual Studio 不是一款"安装即用"的软件。它支持数十种开发场景（工作负载），每个场景下又包含一系列组件。如果提供一个包含所有场景的巨型安装包，体积将超过 60 GB。Visual Studio Installer 的思路是：

1. 下载一个极小的引导程序
2. 由你在引导中选择工作负载
3. 安装器仅下载你选中的组件

这种模式与 JetBrains Toolbox、Unity Hub 等现代工具的安装逻辑一致。

### 1.2 关键界面

Visual Studio Installer 的主界面分为三个区域：

- **已安装标签**：列出已安装的 Visual Studio 版本（2017/2019/2022）及其工作负载
- **可用标签**：检测到但未安装的版本
- **产品卡右下角的"更多"菜单**：修改、更新、修复、卸载、导出配置等操作

## 2 核心功能

### 2.1 工作负载选择

工作负载是 Visual Studio Installer 的核心概念。每个工作负载对应一种开发类型，包含该类型所需的编译器、SDK、设计器和工具集。

最常用的工作负载：

| 工作负载名称 | 包含的核心组件 | 安装体积 |
|-------------|--------------|---------|
| ASP.NET 和 Web 开发 | .NET SDK、ASP.NET Core、IIS Express | ~2 GB |
| 使用 C++ 的桌面开发 | MSVC 编译器、Windows SDK、CMake 支持 | ~4 GB |
| .NET 桌面开发 | WinForms、WPF 设计器、.NET 桌面运行时 | ~1.5 GB |
| Python 开发 | Python 解释器、Anaconda 集成 | ~1 GB |
| 使用 Unity 的游戏开发 | Unity Hub、.NET 游戏工具链 | ~1 GB |
| 使用 C++ 的游戏开发 | Unreal 引擎集成 | ~5 GB |

!!! tip "不必勾选所有工作负载"
    许多开发者会在初次安装时勾选所有看起来"可能用得到"的工作负载。这是 Visual Studio 安装体积失控的直接原因。建议只勾选当前项目必须的工作负载。后续需要额外组件时，随时可以通过 Installer 添加。

### 2.2 单个组件管理

在工作负载之外，Installer 允许手动添加或移除"单个组件"。这在工作负载的预选集不能满足需求时非常有用。常用独立组件：

- Git for Windows
- GitHub Extension for Visual Studio
- Windows 10 SDK（特定版本）
- SQL Server Data Tools（SSDT）
- Linux 开发（C++ 交叉编译）
- .NET Framework 目标包（4.6.2 / 4.7.2 / 4.8 等）

### 2.3 版本管理

Visual Studio Installer 支持在同一台机器上同时安装多个版本：

- Visual Studio 2017（保留旧项目不兼容的风险）
- Visual Studio 2019（迁移过渡期）
- Visual Studio 2022（主力版本）

每个版本的安装和工作负载完全独立，互不干扰。

### 2.4 配置文件导入/导出

在企业团队中，IT 管理员可以使用 Installer 的配置导出功能创建一个 `.vsconfig` 文件，团队所有成员通过该文件安装相同的工作负载集，确保开发环境一致。

**导出：** Visual Studio Installer → 已安装的产品卡 → 更多 → 导出配置 → 生成 `.vsconfig`

**导入：** 使用命令行：

```bash
# 使用 .vsconfig 文件以静默模式安装
vs_community.exe --config "C:\team\team.vsconfig" --passive --norestart --wait
```

## 3 操作指南

### 3.1 初次安装

1. 访问 [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/)
2. 下载 Community / Professional / Enterprise 的引导程序
3. 运行引导程序 → 在"工作负载"页面勾选需要的选项
4. 在安装详细信息面板中，可以查看每个工作负载包含的组件

5. 点击"安装"→ 等待下载完成（时间和网络速度、选择的组件数量相关）

### 3.2 安装后添加或移除组件

```
1. 启动 Visual Studio Installer（通常在开始菜单）

2. 找到已安装的产品卡 → 点击"修改"（Modify）

3. 在工作负载和单个组件标签中勾选或取消

4. 点击"修改"确认 → 自动下载缺失的组件并移除多余的
```

### 3.3 更新版本

```
1. 打开 Installer → 已安装卡片

2. 如果有可用更新，卡片上会显示"可更新"按钮

3. 点击更新 → Installer 下载该版本的增量更新补丁

4. 更新完后重新启动 Visual Studio 即可
```

### 3.4 修复损坏的安装

当 Visual Studio 出现启动崩溃、模板缺失或编译错误时：

```
1. 打开 Installer → 已安装卡片

2. 点击"更多"→ 选择"修复"（Repair）

3. Installer 将重新下载并覆盖所有工作负载组件

4. 修复通常需要 20-60 分钟
```

### 3.5 完全卸载

```
1. 打开控制面板 → 程序和功能

2. 找到 Visual Studio 2022 → 右键卸载

3. 运行 InstallCleanup.exe（位于 Visual Studio Installer 安装目录）
   以清理共享组件和缓存

4. 手动删除以下残余文件夹（可选）：
   - C:\Program Files\Microsoft Visual Studio\2022\Community
   - C:\ProgramData\Microsoft\VisualStudio\Packages
   - C:\Users\<用户名>\AppData\Local\Microsoft\VisualStudio
```

!!! danger "InstallCleanup 会级联删除所有 VS 版本"
    InstallCleanup.exe 有一个已知行为：它默认删除系统中所有版本的 Visual Studio 共享组件，包括 2017/2019/2022。如果你只是替换版本而不是完全放弃 VS，建议只在的崩溃排查的关键时刻使用带 `-i` 标志的窄范围清理。

## 4 命令行用法（自动化部署）

在企业场景或 CI/CD 构建服务器中，Visual Studio Installer 支持静默安装：

```bash
# 使用默认工作负载自动安装 Community 版
vs_community.exe --quiet --add Microsoft.VisualStudio.Workload.CoreEditor --wait

# 添加指定工作负载
vs_community.exe --quiet ^
    --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
    --add Microsoft.VisualStudio.Workload.NetWeb ^
    --includeRecommended --wait

# 列出已安装的工作负载
vs_community.exe --list
```

```bash
# PowerShell 自动化脚本示例
$SetupPath = Join-Path $env:TEMP "vs_setup.exe"
Invoke-WebRequest -Uri "https://aka.ms/vs/17/release/vs_community.exe" -OutFile $SetupPath

$Args = @(
    "--quiet"
    "--add", "Microsoft.VisualStudio.Workload.NetWeb"
    "--add", "Microsoft.VisualStudio.Workload.ManagedDesktop"
    "--includeRecommended"
    "--wait"
    "--norestart"
)

Start-Process -FilePath $SetupPath -ArgumentList $Args -Wait
Remove-Item $SetupPath
```

## 5 同类对比

| 对比维度 | Visual Studio Installer | JetBrains Toolbox | 包管理器（scoop/brew） |
|---------|-----------------------|-------------------|----------------------|
| 管理对象 | Visual Studio 版本和组件 | JetBrains 全系 IDE | Node.js / Python 等单个运行时 |
| 安装方式 | 引导器在线下载 | 统一管理面板 | 命令行 |
| 工作负载 | 原生支持（核心概念） | 不支持 | 不支持 |
| 多版本共存 | 支持 2017/2019/2022 | 支持多版本 | 需 nvm/pyenv 配合 |
| 脚本自动化 | 支持（CLI 参数） | 不支持 | 纯命令行 |
| 配置文件 | .vsconfig 导入导出 | JetBrains Account 同步 | 无 |
| 离线安装 | 支持（布局功能） | 不支持 | 不支持 |

---

## 参考资源

- [Visual Studio Installer 文档](https://docs.microsoft.com/zh-cn/visualstudio/install/)
- [Visual Studio 工作负载与组件 ID 参考](https://docs.microsoft.com/zh-cn/visualstudio/install/workload-and-component-ids)
- [命令行参数参考](https://docs.microsoft.com/zh-cn/visualstudio/install/use-command-line-parameters-to-install-visual-studio)
