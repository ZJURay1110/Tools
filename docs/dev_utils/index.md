# 开发辅助工具

---

## 1 分类简介

IDE 之外，一个高效的开发者工作站还需要一系列辅助工具：版本控制、终端、文件对比、虚拟机和文档生成。这些工具不直接参与代码编写，但少了它们开发效率会明显下降。

!!! tip ""
    根据场景快速选择：
    - 版本控制 → [Git](vcs/git.md)（必装），GUI 用 [Sourcetree](vcs/sourcetree.md) 或 [Lazygit](vcs/lazygit.md)
    - 终端美化 → [Windows Terminal](terminal/windows_terminal.md) 或 [Warp](terminal/warp.md)
    - 对比代码差异 → [Beyond Compare](diff/beyond_compare.md)
    - 跨平台开发 → [WSL](vm/wsl.md) 或 [VMware Workstation](vm/vmware_workstation.md)
    - 查看硬件信息 → [HWiNFO](sys_mon/hwinfo.md) 或 [CPU-Z](sys_mon/cpu_z.md)
    - 代码注释转文档 → [Doxygen](doc/doxygen.md)

---

## 2 为什么需要这些工具

| 场景 | 痛点 | 解决工具 |
|------|------|---------|
| 多人协作开发 | 文件互相覆盖、改了什么看不到 | 版本控制逐行记录历史、分支合并 |
| 使用命令行 | 默认 CMD 太丑、不支持分屏、配色难看 | 终端模拟器 GPU 加速 + 分屏 + 主题 |
| 合并代码冲突 | 手动比对费眼力、容易漏掉差异 | 差异对比工具三栏合并 + 文件夹递归对比 |
| 开发环境与生产环境不同 | 不同 OS 导致的兼容性问题 | 虚拟机 / WSL 隔离环境，不污染宿主机 |
| 电脑卡顿不知道原因 | 不知道 CPU / 内存 / 磁盘是否瓶颈 | 系统监控工具实时查看硬件状态和进程 |
| 项目代码没有文档 | 新成员接手要读完整的源代码 | 文档生成工具从注释提取自动生成 API 文档 |

---

## 3 子分类速览

### 3.1 版本控制

团队协作的基础设施，每一行代码的增删改都记录在案。

| 工具 | 一句话 |
|------|--------|
| Git | 分布式版本控制系统的事实标准 |
| GitHub Desktop | 最简的 Git 图形界面，适合入门 |
| Sourcetree | Atlassian 出品的免费 Git GUI，分支可视化清晰 |
| Lazygit | 终端下的 Git TUI，键盘流开发者的最爱 |

> [进入版本控制分类](vcs/index.md)

### 3.2 终端模拟器

比系统自带终端更快、更美、功能更丰富的命令行界面。

| 工具 | 一句话 |
|------|--------|
| Windows Terminal | 微软官方多标签终端，支持 GPU 加速 |
| Cmder | Windows 上的便携终端套装，自带 Unix 命令 |
| Warp | 内置 AI 和协作功能的 Rust 编写的现代终端 |
| Tabby | Electron 终端，跨平台 + 插件体系 |

> [进入终端模拟器分类](terminal/index.md)

### 3.3 差异对比与合并

文件级和文件夹级的差异分析工具，Code Review 和解决冲突的利器。

| 工具 | 一句话 |
|------|--------|
| Beyond Compare | 最强的文件/文件夹对比工具，支持 FTP 直连对比 |
| Meld | Linux 上最流行的开源差异对比 GUI |
| WinMerge | Windows 免费开源的文件比较和合并工具 |

> [进入差异对比与合并分类](diff/index.md)

### 3.4 虚拟机与环境

创建隔离的开发环境，不影响宿主机系统配置。

| 工具 | 一句话 |
|------|--------|
| VMware Workstation | 商业虚拟机，3D 加速和快照功能最强 |
| VirtualBox | Oracle 开源虚拟机，跨平台免费方案 |
| WSL | Windows 内置 Linux 子系统，启动秒级、集成最紧密 |

> [进入虚拟机与环境分类](vm/index.md)

### 3.5 系统监控

实时查看 CPU / 内存 / 硬盘 / GPU / 传感器信息。

| 工具 | 一句话 |
|------|--------|
| Process Explorer | Sysinternals 出品的进程管理器，替代任务管理器 |
| HWiNFO | 最全面的硬件传感器信息监控工具 |
| CPU-Z | 轻量 CPU / 主板 / 内存详细信息查看 |

> [进入系统监控分类](sys_mon/index.md)

### 3.6 文档生成

从代码注释中自动提取并生成可阅读的 API 文档。

| 工具 | 一句话 |
|------|--------|
| Doxygen | C/C++ / Java / Python 文档生成标准工具 |
| Sphinx | Python 项目文档的标配，支持 reST 和 Markdown |

> [进入文档生成分类](doc/index.md)

---

> [回到工具首页](../index.md)
