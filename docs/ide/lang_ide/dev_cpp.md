# Dev-C++
*轻量级 C/C++ IDE，国内高校 C 语言入门教学中的经典选择*


---

## 前言

Dev-C++ 是一款起源较早的 C/C++ IDE，最初由 Bloodshed 开发，后被 Orwell 接管并维护至 2015 年。2020 年起由 Embarcadero 继续更新（称为 Embarcadero Dev-C++）。

尽管在专业开发者中它的使用率已经很低，但它在中国高校 C 语言教学中仍有不小的惯性：启动快、安装包小、操作直观，对大一新生来说学习成本比 VS Code 和 CLion 低得多。

**本机版本：** 6.30（Embarcadero）  
**平台：** Windows（仅）  
**许可证：** 免费开源

---

## 1 概述

### 1.1 Bloodshed 版 vs Embarcadero 版

| 版本 | 维护方 | 最后更新 | 特点 |
|------|-------|---------|------|
| Bloodshed Dev-C++ | Bloodshed Software | 2005（4.9.9.2） | 原始版本，早已停更 |
| Orwell Dev-C++ | Johan Mes | 2015（5.11） | 长期接替版，广泛流传 |
| Embarcadero Dev-C++ | Embarcadero | 2024（7.5+） | 当前唯一活跃维护版，含 TDM-GCC 11.3 |

!!! note "选择建议"
    如果是新手入门，直接下载最新的 Embarcadero 版（自带 TDM-GCC 编译器，安装即用）。不要在百度上搜索旧版本的 Bloodshed 版或使用学校机房的老版本（不支持 C++11 以上标准，对现代语法报错很模糊）。

### 1.2 使用现状

Dev-C++ 在 2025 年的定位：

- **C 语言入门教学**：对指针、数组、结构体等基本概念的基础检查足够
- **ACM 竞赛备赛**：起步阶段的单文件快速编译与调试
- **嵌入式项目**：某些国产单片机厂商（如 STC、新唐）的示例代码库仍以 Dev-C++ 项目格式分发

对于任何涉及大型工程结构（CMake、多文件模块、单元测试）的项目，Dev-C++ 不再适合。

## 2 核心功能

### 2.1 单文件编译极简工作流

Dev-C++ 的操作路径比大多数 IDE 短：

```
1. 文件 → 新建 → 源代码
2. 编写代码
3. F9 编译运行

不需要创建项目，不需要 CMakeLists.txt，不需要配置文件。
```

### 2.2 项目模板

- Console Application（控制台应用）
- Windows Application（Windows GUI 应用）
- Static Library / DLL
- 空项目

教学场景通常选择 Console Application，自动生成包含 `main()` 的 `.cpp` 文件。

### 2.3 调试器

集成 GDB 调试，支持基本的逐行调试、变量查看、断点设置。功能与 Code::Blocks 的调试器类似，但 UI 更老旧。

## 3 安装与配置

### 3.1 下载与安装

1. 访问 [https://github.com/Embarcadero/Dev-Cpp](https://github.com/Embarcadero/Dev-Cpp)
2. 在 Releases 中下载最新版（如 `Embarcadero_Dev-Cpp_6.30_TDM-GCC_9.2_Setup.exe`）
3. 运行安装程序，一路默认即可
4. 安装完成后，第一次启动会弹出语言选择框 → 选择 Chinese（简体中文）
5. 进行系统自检 → 确认 TDM-GCC 被自动检测到

### 3.2 中文乱码解决

在旧版 Dev-C++（5.x）中，默认编码不是 UTF-8，导致中文注释和中文输出显示乱码：

```
工具 → 编译器选项 → 设置 → 在编译时加入以下命令
添加：
-finput-charset=UTF-8 -fexec-charset=GBK

（说明：源代码编码为 UTF-8，生成的程序输出编码为 GBK，
  与 Windows 系统的 CMD 默认编码一致，中文输出不再空白方块）
```

Embarcadero 6.x 版已默认 UTF-8，可以直接关掉此项配置。

### 3.3 推荐设置

- **字体**：工具 → 编辑器选项 → 显示 → 选择等宽字体（推荐 Consolas 或 Source Code Pro）
- **行号**：工具 → 编辑器选项 → 基本 → 显示行号
- **自动缩进**：工具 → 编辑器选项 → 基本 → 制表符 → 缩进大小 4

## 4 常用操作

| 操作 | 快捷键 |
|------|-------|
| 编译 | Ctrl+F9 |
| 运行 | Ctrl+F10 |
| 编译并运行 | F9 |
| 全部重新编译 | Ctrl+Shift+F11 |
| 调试 | F8 |
| 设置/取消断点 | Ctrl+F5 |
| 逐语句 | Shift+F7 |
| 逐过程 | F7 |
| 搜索 | Ctrl+F |
| 替换 | Ctrl+R |
| 转到行 | Ctrl+G |

## 5 同类对比

| 对比项 | Dev-C++ | Code::Blocks | CLion | Visual Studio C++ |
|-------|---------|-------------|-------|-----------------|
| 安装体积 | 50-100 MB | 100-500 MB | 1-2 GB | 4-20 GB |
| 启动速度 | 1 秒内 | 1-2 秒 | 5-10 秒 | 10-30 秒 |
| 编译器包含 | TDM-GCC（自带） | 需自带或配置 MinGW | 需系统安装 | MSVC（随安装包） |
| 项目模板 | 基础 | 较多 | 多（通过 CMake） | 极丰富 |
| C++ 标准支持 | 至 C++17 | 至 C++17（依赖编译器） | C++20/23 | C++20/23 |
| 代码补全 | 基础 | 基础 | 语义级（Clangd） | IntelliSense |
| 适用场景 | C 语言教学入门 | 教学/竞赛 | 专业开发 | 企业级大型项目 |

## 6 注意事项

!!! warning "不要用它写现代 C++"
    Dev-C++ 的核心问题是 IDE 本身对 C++11/14/17 的理解很浅，报错信息直接透传 GCC 的原始输出，对模板错误没有做任何过滤或美化。当教学阶段从"写一个函数"过渡到"使用 STL 容器和智能指针"时，应该尽快迁移到 VS Code 或者 Code::Blocks。

!!! danger "源代码编码"
    与团队成员共享 `.cpp` 文件时，确保所有参与者使用相同的编译器（如果是 Embarcadero 版 + GCC 9.2，建议统一编译器版本）。有一个常见的错误：团队成员 A 使用 VS 的 MSVC 编译，B 使用 Dev-C++，两人提交到同一个仓库，导致 `.sln` 和 `.dev` 项目文件互相冲突。

---

## 参考资源

- [Embarcadero Dev-C++ GitHub 仓库](https://github.com/Embarcadero/Dev-Cpp)
- [Orwell Dev-C++（已存档）](https://sourceforge.net/projects/orwelldevcpp/)
- [TDM-GCC 编译器](https://jmeubank.github.io/tdm-gcc/)
