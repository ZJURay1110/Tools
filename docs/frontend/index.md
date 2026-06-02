# 前端开发

---

## 1 分类简介

前端开发工具链是现代 Web 开发的基础设施。从打包构建到样式库，这些工具帮你把开发效率提上去、把重复劳动降下来。

!!! tip ""
    根据场景快速选择：
    - 调试页面布局和性能 → [Chrome DevTools](browser_dt/chrome_devtools.md)
    - 管理项目依赖 → [pnpm](pkg_mgr/pnpm.md) 或 [npm](pkg_mgr/npm.md)
    - 新一代构建工具 → [Vite](build/vite.md)
    - 大型项目打包 → [Webpack](build/webpack.md)
    - 构建 UI 界面 → [React](framework/react.md) 或 [Vue](framework/vue.md)
    - 快速原型 CSS → [Tailwind CSS](ui_lib/tailwind_css.md)
    - 代码规范 → [ESLint](lint/eslint.md) + [Prettier](lint/prettier.md)

---

## 2 为什么需要这些工具

| 场景 | 痛点 | 解决工具 |
|------|------|---------|
| 调试页面和网络请求 | 控制台 log 不够用、性能瓶颈难定位 | 浏览器 DevTools 检查元素 + 网络 + 性能面板 |
| 项目越来越大，依赖难以管理 | 手动下载复制 JS 库不现实 | 包管理器声明式安装、版本锁定、lock 文件 |
| 模块文件太多需要打包 | 浏览器不支持 ESM 模块加载大型应用 | 构建工具合并、压缩、Tree Shaking |
| 需要一套组件框架快速开发 | 从零搭建 UI 太慢 | 框架提供组件化、路由、状态管理方案 |
| 团队代码风格不统一 | 缩进换行引号各有习惯，CR 吵架 | 代码检查工具自动格式化 + 规则约束 |

---

## 3 子分类速览

### 3.1 浏览器 DevTools

浏览器内置的开发调试面板，前端开发的每日必备工具。

| 工具 | 一句话 |
|------|--------|
| Chrome DevTools | 功能最全的浏览器调试工具，DOM / 网络 / 性能 / 内存全包括 |
| Firefox DevTools | CSS 网格调试和 Accessibility 检查比 Chrome 更清晰 |

> [进入浏览器 DevTools 分类](browser_dt/index.md)

### 3.2 包管理器

管理 JavaScript 项目的第三方依赖，锁定版本，提升构建可复现性。

| 工具 | 一句话 |
|------|--------|
| npm | Node.js 官方包管理器，生态最大 |
| Yarn | Facebook 出品的 npm 替代，确定性 lock 文件 |
| pnpm | 磁盘效率最高的包管理器，硬链接复用节省空间 |

> [进入包管理器分类](pkg_mgr/index.md)

### 3.3 构建工具

将前端源码（JSX、TS、SCSS）转换为浏览器可执行的静态文件。

| 工具 | 一句话 |
|------|--------|
| Vite | 基于 ESM 的极速开发服务器，秒级 HMR |
| Webpack | 模块打包的老牌工具，插件生态最丰富 |
| esbuild | 用 Go 写的超快速打包器，常用于 vite/webpack 底层 |
| Rollup | 面向库打包的构建工具，Tree Shaking 优秀 |

> [进入构建工具分类](build/index.md)

### 3.4 前端框架

提供组件化、路由和状态管理的 Web 应用架构方案。

| 工具 | 一句话 |
|------|--------|
| React | Facebook 出品的 UI 库，组件 + 单向数据流 |
| Vue | 渐进式框架，上手平缓、模板语法直觉化 |
| Angular | Google 出品的全栈框架，TypeScript 优先 |
| Svelte | 编译时框架，无虚拟 DOM 体积最小 |

> [进入前端框架分类](framework/index.md)

### 3.5 UI 组件库

开箱即用的 UI 组件集合，快速搭建一致的产品界面。

| 工具 | 一句话 |
|------|--------|
| Tailwind CSS | 原子化 CSS 方案，灵活到可以设计任何界面 |
| Bootstrap | 最流行的传统 CSS 框架，组件最全 |
| Element Plus | Vue 3 生态的组件库，中后台首选 |
| Ant Design | React 生态最完整的企业级 UI 组件库 |

> [进入 UI 组件库分类](ui_lib/index.md)

### 3.6 代码检查与格式化

统一团队的代码风格，在开发阶段捕获潜在语法错误。

| 工具 | 一句话 |
|------|--------|
| ESLint | JavaScript / TypeScript 的代码质量检查标准 |
| Prettier | 专注于格式化的工具，消除团队风格争论 |

> [进入代码检查分类](lint/index.md)

---

> [回到工具首页](../index.md)
