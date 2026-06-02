# JetBrains Toolbox
*JetBrains 全系列 IDE 的统一管理面板，覆盖安装、更新、授权与项目快速启动*


---

## 前言

JetBrains 公司于 2000 年在捷克布拉格成立，以 IntelliJ IDEA（Java IDE）起家，逐渐推出了覆盖几乎所有主流编程语言的专用 IDE 产品线。然而，管理七八个 IDE 安装包的版本、授权和项目切换曾非常繁琐。

JetBrains Toolbox App 就是为了解决这个问题而生。它是 JetBrains 生态的"控制中心"，虽然本身不是 IDE，但通过它你可以集中安装、更新、回退和启动全部 JetBrains 产品。

**本机版本：** 2.5.x  
**平台：** Windows / macOS / Linux  
**许可证：** Toolbox App 本身免费（管理的 IDE 需单独获取授权，部分提供社区免费版）

---

## 1 概述

### 1.1 定位

Toolbox App 与 JetBrains 各 IDE 的关系，类似 **Steam 客户端与游戏** 的关系。Steam 负责游戏的购买、下载、版本管理和启动，Toolbox 则负责 IDE 的安装、更新、授权和项目导航。

### 1.2 管理的 IDE 列表

通过 Toolbox 可以安装和管理的 JetBrains IDE 包括（但不限于）：

| IDE 名称 | 用途 | 社区版是否免费 |
|---------|------|-------------|
| IntelliJ IDEA | Java / Kotlin / Scala / Groovy | Community 免费 |
| PyCharm | Python / Django / Flask / Jupyter | Community 免费 |
| WebStorm | JavaScript / TypeScript / HTML/CSS / 前端框架 | 需付费 |
| PhpStorm | PHP / Laravel / Symfony / WordPress | 需付费 |
| CLion | C / C++ / Rust（插件） | 需付费 |
| GoLand | Go | 需付费 |
| Rider | .NET / C# / Unity / Unreal | 需付费 |
| DataGrip | SQL / 数据库管理 | 需付费 |
| RubyMine | Ruby / Rails | 需付费 |
| RustRover | Rust | 个人免费 |

## 2 核心功能

### 2.1 IDE 安装与版本管理

- **一键安装**：在 Toolbox 界面中点击 IDE 旁的 "Install" 按钮，自动下载最新稳定版
- **多版本共存**：可以同时保留 IntelliJ IDEA 2023.3 和 2024.1 两个版本，避免升级后插件不兼容
- **版本回退**：已安装的 IDE 右侧下拉菜单 → Other versions → 选择历史版本安装

### 2.2 项目发现与快速打开

Toolbox 会自动扫描本地磁盘上的项目（通过识别 `.idea`、`.git`、`package.json` 等标志文件），并在主界面展示最近使用的项目。点击即可用对应的 IDE 打开。

### 2.3 集中授权管理

- 登录 JetBrains Account 账号后，所有已购买授权的产品自动激活
- 支持浮动许可证（Floating License Server，企业团队使用）
- 教育授权（学生/教师邮箱）和开源项目授权统一在此管理

### 2.4 Shell 脚本集成

安装 Toolbox 后你可以在任意终端中用简短命令启动特定的 IDE：

```bash
idea .            # 用 IntelliJ IDEA 打开当前目录
pycharm .         # 用 PyCharm 打开当前目录
webstorm app.js   # 用 WebStorm 打开指定文件
phpstorm .        # 用 PhpStorm 打开当前目录
```

如果命令不可用，打开 Toolbox → Settings → Tools → 勾选 "Generate shell scripts"，并确认 Shell scripts location 的路径在你的 `PATH` 中。

## 3 安装与配置

### 3.1 系统需求

- **操作系统**：Windows 10/11、macOS 11+、Linux（支持 .deb 和 .rpm 打包格式）
- **内存**：Toolbox App 本身仅占约 100 MB（安装的 IDE 每个通常 1-3 GB）
- **网络**：需要稳定的网络连接用于下载 IDE

### 3.2 安装步骤

1. 访问 [https://www.jetbrains.com/toolbox-app/](https://www.jetbrains.com/toolbox-app/)
2. 下载对应系统的安装包：

   - Windows：`.exe` 安装程序
   - macOS：`.dmg` 磁盘映像
   - Linux：`.tar.gz` 压缩包

3. Windows 用户运行安装程序，建议勾选 "Start at login"（开机自启）

4. 安装完成后 Toolbox 会在系统托盘显示图标，点击打开主界面

5. 在主界面中，左侧是项目列表，右侧是可用 IDE 列表。点击 IDE 右侧的 "Install" 开始安装你需要的 IDE

!!! warning "默认安装路径"
    Toolbox 默认在 `C:\Users\<用户名>\AppData\Local\JetBrains\Toolbox\apps\` 下安装 IDE。如果 C 盘空间有限，可以在 Toolbox Settings 中更改安装路径。

### 3.3 首次配置

打开 Toolbox → 右上角齿轮图标 → Settings：

| 设置项 | 推荐值 | 说明 |
|--------|-------|------|
| Start at login | 勾选 | 随系统启动 |
| Generate shell scripts | 勾选 | 允许命令行启动 IDE |
| Shell scripts location | `C:\Users\<用户名>\jetbrains` | 建议加入 PATH |
| Update IDE silently | 勾选 | 后台静默更新，不弹窗 |
| Keep only latest versions | 不勾选 | 允许保留旧版本 |

## 4 常用操作

### 4.1 日常使用流程

```
1. 打开 Toolbox（点击系统托盘图标）
2. 左侧项目列表中找到要开发的项目
3. 点击项目卡 → 对应的 IDE 自动启动并打开该项目
4. （如果 IDE 尚未安装）右侧列表 → 找到对应 IDE → Install
```

### 4.2 管理 IDE 版本

```
1. 右侧已安装 IDE 的下拉箭头
2. 查看：当前版本、可更新版本
3. 操作：
   - Update：更新到最新版本
   - Install alongside：安装新版本但保留旧版本
   - Other versions：查看和安装历史版本
   - Uninstall：卸载该 IDE（包括所有配置和缓存）
```

### 4.3 释放磁盘空间

JetBrains IDE 的缓存和索引通常占据 500 MB - 2 GB。你可以通过以下方式释放：

1. Toolbox 中不再需要的旧 IDE 版本 → Uninstall
2. IDE 内：File → Invalidate Caches... → 重建索引
3. 手动删除 `C:\Users\<用户名>\AppData\Local\JetBrains\<IDE名称>\` 下的旧版本缓存目录

## 5 同类对比

| 对比维度 | JetBrains Toolbox | 手动下载安装 | 命令行包管理（brew/scoop/choco） |
|---------|-------------------|------------|-------------------------------|
| IDE 发现 | 全产品线一览 | 需自行搜索官网 | 需知道包名 |
| 多版本管理 | 原生支持 | 手动管理 | 通常只保留最新版 |
| 更新提醒 | 自动推送 | 依赖 IDE 自身检查 | 终端更新 |
| 授权管理 | 集中面板 | 每 IDE 独立 | 每 IDE 独立 |
| 项目导航 | 内置项目列表 | 无 | 无 |
| 适用场景 | JetBrains 全家桶用户 | 只用 1-2 个 IDE | 习惯终端操作 |

## 6 注意事项

!!! info "Toolbox 与 IDE 的更新同步"
    Toolbox 检测到新版本后默认为后台静默更新。如果你的项目依赖特定版本（如公司统一使用 IntelliJ IDEA 2024.1.2），请关闭 "Update IDE silently" 选项，改为手动更新。

!!! warning "Settings Sync 冲突"
    JetBrains IDEs 内置了 Settings Sync（通过 JetBrains Account 同步设置）。如果多台设备都登录了同一个 JetBrains Account，注意不要在同一时间修改不同设备上的快捷键配置，可能导致覆盖。

!!! danger "教育授权到期"
    JetBrains 的学生免费授权有效期为 1 年，到期后需要重新验证学生身份。授权过期后 IDE 将进入 30 天的评估模式，超期未续将无法使用。毕业季尤其需要注意。

---

## 参考资源

- [JetBrains Toolbox 官网](https://www.jetbrains.com/toolbox-app)
- [JetBrains 全产品列表](https://www.jetbrains.com/products)
- [JetBrains 学生授权申请](https://www.jetbrains.com/community/education/)
- [JetBrains 开源项目授权](https://www.jetbrains.com/community/opensource/)
