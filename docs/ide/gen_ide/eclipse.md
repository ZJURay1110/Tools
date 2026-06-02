# Eclipse
*老牌开源 Java IDE，基于 OSGi 插件架构，通过扩展支持 C/C++ / Python / PHP 等多语言开发*


---

## 前言

Eclipse 是 Java 世界中最具历史地位的 IDE 之一。由 IBM 于 2001 年向 Eclipse Foundation 捐赠，至今已运行超过 20 年。它不仅是 Java 开发者的首选之一，还是整个 IDE 插件架构的奠基者 —— IntelliJ IDEA、NetBeans 等后来的 IDE 都在不同程度上借鉴了 Eclipse 的插件体系设计。

Eclipse 的核心运行环境是 OSGi（Equinox），所有功能（包括 Java 编译器 JDT）均以插件形式加载，这赋予了它极高的可扩展性。即使到了 2025 年，仍有大量企业级项目（尤其是银行、保险、电信等传统行业）在 Eclipse 上运行着庞大的 Java 代码库。

**最新稳定版：** 2024-12 (Eclipse 4.35)  
**平台：** Windows / macOS / Linux  
**许可证：** EPL（Eclipse Public License，完全免费开源）

---

## 1 概述

### 1.1 版本命名

Eclipse 从 2018 年开始采用 **年份-月份** 的命名方式，每年 3 月、6 月、9 月和 12 月各发布一个主版本：

- 2024-03（2024 年 3 月）
- 2024-06（2024 年 6 月）
- 2024-09（2024 年 9 月）
- 2024-12（2024 年 12 月）

这种节奏让企业团队可以提前规划升级窗口。

### 1.2 发行包类型

Eclipse 官网提供多种预打包的发行版（Packages），每种针对不同的开发类型：

| 发行包 | 包含功能 |
|--------|---------|
| Eclipse IDE for Java Developers | JDT、Maven、Git、JUnit |
| Eclipse IDE for Enterprise Java | 以上 + Jakarta EE、Server 工具 |
| Eclipse IDE for C/C++ Developers | CDT、GDB 调试、CMake 支持 |
| Eclipse IDE for PHP Developers | PDT、Composer、Xdebug |
| Eclipse IDE for RCP and RAP Developers | 桌面应用框架开发 |

!!! tip "不要下载错了"
    新手最常见的错误是下载了"Eclipse for Enterprise Java"却发现启动后多出一堆用不到的 Server 视图。如果你只是写 Spring Boot 这样的非 Jakarta EE 项目，选择标准版 "Java Developers" 即可。

## 2 核心功能

### 2.1 JDT（Java Development Tools）

JDT 是 Eclipse 的"心脏"。它不是外部插件，但在架构上依然通过 OSGi Bundle 加载。JDT 提供的 Java 开发能力包括：

- **增量编译**：保存文件时自动增量编译，不需要显式点击"编译"按钮。即使项目有 10000 个 `.java` 文件，也只重编译修改过的和受影响的文件。
- **重构（Refactoring）**：重命名（F2 / Alt+Shift+R）、提取方法（Alt+Shift+M）、上移/下移（Alt+Shift+V / Alt+Shift+T）
- **快速修正（Ctrl+1）**：Eclipse 最标志性的功能。光标放在错误或警告处按 Ctrl+1，IDE 会列出可能的修复方案（如"导入缺失的类"、"生成未实现的方法"、"包围在 try/catch 中"）
- **调用层次结构（Ctrl+Alt+H）**：查看一个方法被谁调用、调用了谁

### 2.2 工作空间（Workspace）

Eclipse 的工作空间不同于 VS Code 的"文件夹"。一个工作空间包含：

- 项目的集合（可添加/移除）
- 全局编辑器设置（字体、主题、快捷键）
- 编译器设置（JDK 版本、警告级别）
- `.metadata` 隐藏文件夹（存储以上所有状态）

一个开发团队的一般做法是：每个 Git 仓库使用一个独立的工作空间，避免不同项目间的 JDK 版本或编译器设置互相干扰。

### 2.3 透视图（Perspective）

透视图是 Eclipse 独有的概念。它是一组视图（View）和编辑器（Editor）的布局方案。不同的开发任务使用不同的透视图：

| 透视图 | 用途 |
|--------|------|
| Java | Java 代码编写（默认） |
| Debug | 调试时自动切换 |
| Git | 版本控制操作 |
| Database Development | 连接和查询数据库 |

在 Eclipse 右上角可以快速切换透视图。

### 2.4 调试器

Eclipse 的 Java 调试器支持：

- 条件断点：右键断点 → Breakpoint Properties → 输入条件（如 `index > 100`）
- 异常断点：在 Run → Add Java Exception Breakpoint 中指定异常类型，一旦该异常抛出就自动中断
- 远程调试：Run → Debug Configurations → Remote Java Application → 附加到远程 JVM（适用于服务器端调试）
- 热代码替换：调试时修改代码并保存，Eclipse 尝试将新字节码注入正在运行的 JVM（不保证每次都成功）

## 3 安装与配置

### 3.1 系统需求

| 组件 | 最低要求 | 推荐 |
|------|---------|------|
| Java 版本 | JDK 17 | JDK 21（LTS） |
| 操作系统 | Windows 10+ / macOS 11+ / Linux | Windows 11 / macOS 14+ |
| 内存 | 2 GB | 8 GB+ |
| 磁盘 | 500 MB（IDE 本体） | SSD，额外 5 GB 用于项目缓存 |

!!! warning "JDK 版本匹配"
    Eclipse 2024-12 需要 JDK 17 及以上才能启动。如果你的系统默认是 JDK 8 或 11，需要在 `eclipse.ini` 中显式指定 `-vm` 参数指向 JDK 17 的路径（见下文）。

### 3.2 安装步骤

1. 访问 [https://www.eclipse.org/downloads/packages/](https://www.eclipse.org/downloads/packages/)
2. 选择你需要的发行包，点击对应的 Windows/macOS/Linux 下载链接
3. Eclipse 不提供传统"安装向导"，下载的是一个 zip/tar.gz 压缩包

4. **解压到目标目录**（例如 `D:\eclipse\`），不需要管理员权限
5. 进入解压目录，双击 `eclipse.exe`（Windows）启动

!!! note "Eclipse 无需安装"
    Eclipse 是"绿色软件"——解压即用。你可以把整个 `eclipse/` 文件夹复制到 U 盘，插到任何电脑上直接运行（前提是目标电脑有匹配的 JDK）。

### 3.3 首次配置

1. 启动时会提示选择工作空间位置。推荐在代码根目录外单独建一个 `workspace/` 文件夹，不要放在 Git 仓库内。

2. 进入后首先配置 JDK：
   - Window → Preferences → Java → Installed JREs
   - 点击 Add → Standard VM → 浏览到 JDK 安装目录（如 `C:\Program Files\Eclipse Adoptium\jdk-21.0.1.12-hotspot\`）
   - 勾选新添加的 JDK 作为默认

3. 设置 UTF-8 编码：
   - Window → Preferences → General → Workspace
   - Text file encoding → Other → UTF-8

4. 设置代码字体：
   - Window → Preferences → General → Appearance → Colors and Fonts
   - Java → Java Editor Text Font → Edit → 推荐 Consolas 或 JetBrains Mono

### 3.4 如果 Eclipse 无法启动（JDK 问题）

打开 `eclipse.ini`，在 `-vmargs` 行**之前**添加：

```ini
-vm
C:\Program Files\Eclipse Adoptium\jdk-21.0.1.12-hotspot\bin\javaw.exe
```

!!! danger "顺序很重要"
    `-vm` 必须在 `-vmargs` 之前，否则 Eclipse 会忽略这个配置，继续尝试使用系统默认 JDK。

### 3.5 推荐插件

| 插件 | 用途 | 安装方式 |
|------|------|---------|
| SonarLint | 实时代码异味检测 | Marketplace |
| P3C（Alibaba） | Java 编码规范检查 | Marketplace |
| Darkest Dark Theme | 深色主题优化 | Marketplace |
| AnyEdit Tools | 文本编辑增强（行排序、空格处理） | Marketplace |
| EGit | Git 集成（通常已内置） | 更新站点 |

## 4 常用操作

### 4.1 核心快捷键

| 操作 | 快捷键 |
|------|-------|
| 快速修正（显示建议） | Ctrl+1 |
| 代码补全 | Ctrl+Space |
| 打开资源（文件搜索） | Ctrl+Shift+R |
| 打开类型（类搜索） | Ctrl+Shift+T |
| 转到定义 | F3 |
| 转到父类方法 | 光标在 @Override 上按 F3 |
| 查找引用 | Ctrl+Shift+G |
| 调用层次结构 | Ctrl+Alt+H |
| 重命名重构 | Alt+Shift+R |
| 提取方法重构 | Alt+Shift+M |
| 生成 Getter/Setter/Constructor | Alt+Shift+S, 然后选择 |
| 多行注释切换 | Ctrl+Shift+/（块注释）/ Ctrl+Shift+\（取消） |
| 单行注释切换 | Ctrl+/ |
| 运行 | Ctrl+F11 |
| 调试 | F11 |
| 逐过程 | F6 |
| 逐语句 | F5 |
| 格式化 | Ctrl+Shift+F |

### 4.2 代码模板

Eclipse 内置了大量代码模板以提高编码效率。在编辑器中输入模板名然后按 Ctrl+Space：

| 模板名 | 展开结果 |
|--------|---------|
| `main` | public static void main(String[] args) |
| `sysout` | System.out.println(); |
| `systrace` | System.out.println("当前方法: " + Thread.currentThread().getStackTrace()[1].getMethodName()); |
| `foreach` | for (Type item : collection) {} |
| `try` | try { ... } catch (Exception e) { ... } |

可以在 Window → Preferences → Java → Editor → Templates 中自定义。

### 4.3 实战场景

**场景 A：启动一个 Java 桌面应用项目**

```
1. File → New → Java Project
2. Project Name: hello_app
3. JRE: 选择 JavaSE-21
4. Project Layout: 选择 "Create separate folders for sources and class files"
5. Finish
6. 在 src 下 New → Class → Name: MainApp, 勾选 public static void main
7. 编写代码 → Ctrl+F11 运行
```

**场景 B：附加到远程 Tomcat 调试**

```
1. 在远程 Tomcat 的 catalina.bat 中添加：
   set CATALINA_OPTS=-agentlib:jdwp=transport=dt_socket,address=8000,server=y,suspend=n
2. Eclipse → Run → Debug Configurations → Remote Java Application
3. Host: 远程服务器 IP, Port: 8000
4. Debug → 在本地 Eclipse 中设置断点 → 触发远程代码 → 调试
```

## 5 同类对比

| 对比维度 | Eclipse | IntelliJ IDEA Community | VS Code（+ Java 插件） | NetBeans |
|---------|---------|------------------------|----------------------|---------|
| 启动速度 | 10-20 秒 | 5-10 秒 | 2-4 秒 | 8-15 秒 |
| Java 增量编译 | 原生（优秀） | 原生（优秀） | 依赖 Maven/Gradle | 原生 |
| 内置重构 | 20+ 种 | 30+ 种 | 基础（F2 重命名） | 15+ 种 |
| Git 集成 | EGit（内置） | 内置 | 内置 | 内置 |
| 内存占用（空项目） | 500-800 MB | 800-1200 MB | 300-500 MB | 400-700 MB |
| 插件生态 | 丰富（老牌） | 极其丰富 | 极其丰富 | 较丰富 |
| Jakarta EE 支持 | 优秀（原生） | 仅 Ultimate 付费版 | 无 | 有限 |
| 学习曲线 | 陡 | 中 | 低 | 中 |
| 免费 | 完全免费 | Community 免费 | 完全免费 | 完全免费 |

## 6 注意事项

!!! warning "工作空间损坏"
    `.metadata` 文件夹对于 Eclipse 至关重要。如果这个文件夹损坏（现象为启动后看不到任何项目），可以让 Eclipse 在启动时加上 `-clean` 参数：在快捷方式目标后添加 `-clean`。如果仍不行，可以新建一个工作空间重新 Import 项目。

!!! info "告别 `eclipse.exe -clean` 的手动操作"
    可以编辑 `eclipse.ini`，在 `-vmargs` 行前加一行 `-clean`，这样每次启动都会清理缓存。但频繁 `-clean` 会延长启动时间，建议只在出现问题时使用。

!!! danger "JDK 升级导致项目报错"
    如果系统 JDK 从 17 升级到 21 后所有项目都出现编译错误，需要在 Window → Preferences → Java → Installed JREs 中移除旧的 JDK 路径，并添加新的 JDK 21 路径。然后右键项目 → Properties → Java Build Path → Libraries → 检查 JRE System Library 指向的版本。

---

## 参考资源

- [Eclipse 官网](https://www.eclipseide.org)
- [Eclipse 发行包下载](https://www.eclipse.org/downloads/packages)
- [Eclipse Marketplace](https://marketplace.eclipse.org)
- [Eclipse Wiki](https://wiki.eclipse.org)
