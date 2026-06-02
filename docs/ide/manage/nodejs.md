# Node.js
*开源的跨平台 JavaScript 运行时环境，基于 Chrome V8 引擎，前端生态的核心基础*


---

## 前言

Node.js（通常简称为 Node）将 Chrome V8 引擎从浏览器中剥离，赋予 JavaScript 在服务端处理文件、网络、数据库的能力。自 2009 年由 Ryan Dahl 发布以来，Node.js 不仅成为 Web 前端开发者转向服务端的桥梁，更催生了 npm（Node Package Manager）——全球最大的开源包注册表。

大多数现代开发环境的第一步就是安装 Node.js。无论搭建 React 前端、Express 后端、Electron 桌面应用还是 Vite 构建工具，nvm 切换和在终端中执行 `node -v` 是开发者最熟悉的起步仪式。

**推荐版本：** LTS（长期支持，偶数主版本，如 20.x / 22.x）  
**当前最新 LTS：** 22.12（截至 2025-01）  
**平台：** Windows / macOS / Linux  
**许可证：** MIT（开源免费）

---

## 1 概述

### 1.1 Node.js 能做什么

- 运行 JavaScript/TypeScript 服务端（Express / Koa / Fastify）
- 构建前端工具（Vite / Webpack / Rollup / esbuild）
- 桌面应用开发（Electron / Tauri）
- 命令行工具（CLI，如 ESLint / Prettier / TypeScript 编译器）
- 跨平台脚本编写（替代 Bash / Python）

### 1.2 重要概念：LTS 与 Current

Node.js 每隔 6 个月发布一个大版本（4 月、10 月），LTS 版本在发布后获得 3 年的长期维护，Current 版本只有 6 个月的快速支持窗口：

| 版本类型 | 发布月份 | 维护周期 | 适用场景 |
|---------|---------|---------|---------|
| LTS（如 20.x / 22.x） | 偶数年 4 月 | 30 个月 | 生产环境、团队协作 |
| Current（如 21.x / 23.x） | 奇数年 10 月 | 6 个月 | 尝鲜、学习新特性 |

!!! warning "生产环境坚持 LTS"
    在团队项目或生产部署中，始终使用 LTS 版本。Current 版本可能有未预期的 API 变更或第三方库兼容问题。在 2024 年，建议选择 20.x 或 22.x LTS。

## 2 安装

### 2.1 方案 A：从官网直接安装（推荐新手）

1. 访问 [https://nodejs.org](https://nodejs.org)
2. 在首页点击 LTS 版本（左侧大按钮，如 22.12.0 LTS）
3. 下载对应系统的安装包：

   - Windows：`.msi`（推荐）或 `.exe`
   - macOS：`.pkg`
   - Linux：下载 `.tar.xz` 或通过包管理器

4. 运行安装程序：

   **Windows（msi）：**
   - 全部默认选项即可
   - Node.js runtime 和 npm 会被自动添加到系统 PATH

   **macOS（pkg）：**
   - 点击继续 → 安装
   - 安装后打开终端验证

5. 打开终端验证：

```bash
node --version
# 期望输出：v22.12.0

npm --version
# 期望输出：10.9.0
```

### 2.2 方案 B：通过 nvm 管理多版本（推荐开发者）

nvm（Node Version Manager）允许在一台机器上安装多个 Node.js 版本，并在项目间快速切换。当同时维护使用不同 Node 版本的多个项目时，nvm 几乎是必需品。

**Windows 用户：** 使用 nvm-windows（注意：与 macOS/Linux 的 nvm 是两个独立项目）

```bash
# Windows 安装 nvm-windows
1. 访问 https://github.com/coreybutler/nvm-windows/releases
2. 下载 nvm-setup.exe
3. 安装 → 自动配置 PATH
4. 重启终端后：

nvm --version
# 期望输出：1.1.12

# 安装 Node.js 22.x LTS
nvm install 22.12.0

# 切换使用
nvm use 22.12.0

# 查看已安装列表
nvm list

# 设置默认版本
nvm alias default 22.12.0
```

**macOS/Linux 用户：**

```bash
# 安装 nvm（使用 install 脚本）
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

# 重新加载 shell 配置
source ~/.zshrc

# 安装并使用 Node.js LTS
nvm install --lts
nvm use --lts
```

!!! tip "项目级 .nvmrc 文件"
    在项目根目录创建 `.nvmrc` 文件，写入 `20.18.0`。之后团队成员进入项目执行 `nvm use`，nvm 会自动读取 `.nvmrc` 并切换到对应版本。这个操作可以集成在 shell 的 cd 钩子中自动触发。

### 2.3 方案 C：包管理器安装

```bash
# macOS (Homebrew)
brew install node@22

# Windows (Scoop)
scoop install nodejs@22.12.0

# Windows (Chocolatey)
choco install nodejs --version 22.12.0

# Linux (Ubuntu/Debian, NodeSource 源)
curl -fsSL https://deb.nodesource.com/setup_22.x | sudo -E bash -
sudo apt-get install -y nodejs
```

## 3 生态工具

### 3.1 npm 与版本管理命令

```bash
# 查看当前项目依赖
npm list --depth=0

# 安装依赖
npm install <package>           # 生产依赖
npm install <package> --save-dev  # 开发依赖
npm install <package> -g         # 全局安装

# 更新包
npm update <package>

# 运行脚本（package.json scripts 中的命令）
npm run dev
npm run build
```

### 3.2 包管理器的选择

| 包管理器 | 命令 | 特点 |
|---------|------|------|
| npm | npm install | Node 官方，功能完整，速度较慢 |
| pnpm | pnpm add | 磁盘效率高（硬链接复用），速度快 |
| Yarn | yarn add | 确定性 lock 文件，团队友好 |

```bash
# 三个管理器用同一个项目根目录
# 不要混用！选择一个后统一使用

# npm
npm init
npm install react

# pnpm（安装）
npm install -g pnpm
pnpm init
pnpm add react

# Yarn（安装）
npm install -g yarn
yarn init
yarn add react
```

!!! danger "不要混用包管理器"
    项目中出现了 `package-lock.json`（npm）、`yarn.lock`（Yarn）、`pnpm-lock.yaml`（pnpm）中的两个或更多，会导致 CI/CD 流水线生成不同的依赖树版本，增加"在我电脑上可以跑"问题的几率。在一个项目中只选择一个包管理器并 lock 文件。

## 4 常用操作

```bash
# 核心命令速查
node -v                     # 查看 Node.js 版本
npm -v                      # 查看 npm 版本
npx <package>               # 临时运行某包（无需全局安装）

# 项目初始化
mkdir my-project && cd my-project
npm init -y                 # 快速生成 package.json
npm init                    # 交互式生成

# 运行脚本
npm run dev                 # 开发服务器
npm run build               # 生产构建
npm test                    # 运行测试
npm run lint                # 代码检查

# 全局工具
npm list -g --depth=0       # 查看全局安装的包
npm cache clean --force     # 清理缓存
npx clear-npx-cache         # 清理 npx 缓存
```

## 5 常见问题

!!! warning "Windows 上 node 命令找不到"
    安装时没有勾选"添加到 PATH"选项。解决方法：重新运行 msi 安装包 → Modify → 确认勾选"Add to PATH"。或手动编辑系统环境变量，在 Path 中添加 `C:\Program Files\nodejs\`。

!!! info "npm 权限错误（EACCES）"
    macOS/Linux 上使用全局安装时可能遇到。推荐使用 nvm 管理版本（避免 sudo npm install -g）。如果已使用 nvm 仍有问题：检查 `npm config get prefix` 指向是否正确。

---

## 参考资源

- [Node.js 官网](https://nodejs.org)
- [Node.js 官方文档（中文）](https://nodejs.org/zh-cn/docs)
- [npm 官方文档](https://docs.npmjs.com)
- [nvm-windows 仓库](https://github.com/coreybutler/nvm-windows)
- [nvm（macOS/Linux）仓库](https://github.com/nvm-sh/nvm)
- [Node.js 发布计划](https://github.com/nodejs/release)
