# Cursor
*基于 VS Code 深度集成的 AI 原生代码编辑器，将大语言模型嵌入编码工作流*


---

## 前言

Cursor 是 2023 年由 Anysphere 团队推出的 AI 代码编辑器，在 VS Code 的代码基础上进行了大量修改和增强，将大语言模型（LLM）从"外部聊天窗口"变成了编辑器的原生能力。开发者不需要复制代码到 ChatGPT，不需要在浏览器和编辑器之间切换 —— 在 Cursor 里，你选中代码，按一个快捷键，AI 直接在你的光标位置修改或生成代码。

截至 2025 年初，Cursor 已成为增长最快的 AI 开发工具之一，用户包括大量前端工程师、全栈开发者和独立开发者。它的实质是"你熟悉的 VS Code + 一个深度嵌入的 AI 同事"。

**本机版本：** 0.45.x  
**平台：** Windows / macOS / Linux  
**许可证：** 免费（有限额度）/ Pro $20/月（无限调用 + 优先模型访问）

---

## 1 概述

### 1.1 与 VS Code 的关系

Cursor 基于 VS Code 开源代码库的分支（Fork），保留了 VS Code 的全部编辑体验、插件生态和快捷键。在此基础上，Cursor 在编辑器内部添加了以下 AI 能力：

- **AI 聊天侧边栏**（Ctrl+L）：与 AI 对话，可引用文件/文件夹作为上下文
- **AI 内联编辑**（Ctrl+K）：选中代码直接用自然语言指令重写
- **Tab 补全增强**：不仅补全当前行，还预测并修改项目中的其他文件引用
- **Composer**：在聊天面板中以迭代方式生成/修改整个文件或多文件

### 1.2 为什么不用 ChatGPT 网页版替代

在 ChatGPT 网页版中，编码流程是"复制代码 → 粘贴到对话 → 等待回复 → 复制回来 → 调整格式"，5 步操作。Cursor 将这个流程压缩为 1 步：选中代码，输入提示，回车。AI 的结果直接应用在文件中，接受（Tab）或拒绝（Esc）即可。对于日常编码场景，这个微小的体验差异会产生量变的效率提升。

!!! info "模型选择"
    免费用户可使用 GPT-4o-mini 和 Cursor-small（自研模型）。Pro 用户额外解锁 GPT-4o、Claude 3.5 Sonnet、Claude 4 等最强模型。对于复杂重构任务，强烈建议切换到 Claude 系列，其在代码理解和修改方面的表现普遍优于 GPT 系列。

## 2 核心功能

### 2.1 AI 聊天（Ctrl+L / Cmd+L）

按下 Ctrl+L 打开聊天侧边栏。与 ChatGPT 类似，你可以自由提问，但不同的是：

- **选择上下文**：点击聊天框下的 `@` 符号，可以选择文件、文件夹、当前打开的标签页作为 AI 的参考范围
- **代码提及**：在对话中使用 `@filename` 直接引用特定文件内容
- **文档引用**：使用 `@Web` 指令让 AI 先查阅官方文档再回答（需联网）

```text
# 示例对话
用户: @file:src/router.ts 
      帮我分析这个路由文件，找出所有无效的重定向规则

AI 会读取 router.ts 的完整内容，然后逐行标注出无效的重定向规则
```

### 2.2 AI 内联编辑（Ctrl+K / Cmd+K）

这是 Cursor 最高频使用的功能。选中一段代码，按 Ctrl+K 打开一个输入框，用自然语言描述你要做的修改：

```python
# 原始代码（选中后按 Ctrl+K）:
def CalculateTotal(items):
    total = 0
    for item in items:
        total += item.price
    return total

# 在输入框输入: 
# "添加类型注解、缺少 items 时的防错处理、并简化循环为 sum 生成器"

# AI 修改后:
def CalculateTotal(items: list[Product] | None) -> float:
    # 如果传入 None 或空列表，直接返回 0
    if not items:
        return 0.0
    return sum(item.price for item in items)
```

!!! tip "Ctrl+K 的使用姿势"
    不要一次只让 AI 修改一行。给它一个完整的函数或代码块，清晰地说明你想要的变化。指令中可以结合几种要求："添加错误处理"、"改用 async/await"、"添加中文注释"、"提取常量到顶部"等。多试几次就会找到适合自己的描述风格。

### 2.3 Tab 智能补全

Cursor 的 Tab 补全比传统代码补全更进一步：

- **多行预测**：不只是补全当前行的剩余部分，而是预测接下来 3-5 行的完整逻辑
- **跨文件感知**：如果你在 `settings.ts` 中新增了一个配置项，回到 `app.ts` 后，Tab 会自动建议对应的引用修改
- **光标跳转**：接受一个多行补全后，Tab 可以跳到下一个需要你手动修改的位置

### 2.4 Composer（多文件编辑）

Composer 是 Cursor 最强的功能，位于聊天面板中。它可以：

- 生成整个文件（"帮我创建一个 Express 服务器，包含 /health 和 /api/users 两个端点"）
- 同时修改多个文件（"把所有 `var` 声明改成 `const`，并且把回调函数改成 async/await"）
- 在对话中迭代："这个版本可以工作，但是把 JWT 过期时间改成 15 分钟，并添加刷新令牌逻辑"

### 2.5 图像理解（前端开发利器）

将 UI 设计图、手绘图、截图直接拖入聊天窗口，Cursor 的视觉模型可以理解图像内容，生成对应的 HTML/CSS/React 组件代码。

## 3 安装与配置

### 3.1 系统需求

- **操作系统**：Windows 10/11、macOS 12+、Linux
- **内存**：推荐 8 GB+（AI 功能需要额外内存）
- **磁盘**：约 500 MB
- **网络**：AI 功能需要稳定网络连接

### 3.2 安装步骤

1. 访问 [https://cursor.sh](https://cursor.sh)，下载对应系统版本
2. Windows 用户运行 `Cursor Setup x64.exe` 安装
3. 首次启动提示登录：支持 Google / GitHub 账号
4. 登录后进入订阅选择界面：

   - **Hobby（免费）**：每月 2000 次代码补全 + 50 次慢速高级请求
   - **Pro（$20/月）**：无限补全 + 500 次快速高级请求/月 + 每日 10 次 OpenAI o1 请求
   - **Business（$40/用户/月）**：额外管理面板 + 团队集中计费

### 3.3 从 VS Code 一键迁移

Cursor 完全兼容 VS Code 的配置格式。首次启动时可以一键导入：

1. 启动时选择 "Import from VS Code"
2. 勾选要导入的内容：扩展（Extensions）、设置（Settings）、快捷键（Keybindings）
3. 确认 → 等待 10-30 秒导入完成
4. 之后打开 VS Code 的项目文件夹直接在 Cursor 中使用，无需任何额外配置

### 3.4 推荐设置

打开 Cursor Settings（Ctrl+K, Ctrl+S 或左下角齿轮图标）：

| 设置项 | 推荐值 | 说明 |
|--------|-------|------|
| Models → Chat Model | claude-4-sonnet | 代码理解和修改能力最强 |
| Models → Tab Model | cursor-small | 速度最快，日常补全够用 |
| Rules for AI | 自定义编码规范 | 告诉 AI 你的命名偏好和架构习惯 |
| Privacy → Privacy Mode | 启用 | 代码不上传至 Cursor 服务器存储 |
| Beta → Long Context | 启用 | 允许 AI 一次读取大文件完整内容 |

### 3.5 Rules for AI 配置示例

在 Cursor Settings → General → Rules for AI 中添加：

```text
- 函数使用 PascalCase 命名
- 变量使用 camelCase 命名
- 所有函数必须包含 JSDoc 注释
- 使用 TypeScript strict 模式
- 不要使用 any 类型
- 异步操作统一使用 async/await 而非 Promise.then
- 组件文件放在 src/components/ 下，工具函数放在 src/utils/ 下
```

这些规则会被自动附加到每一次 AI 请求的系统提示词中，确保生成的代码风格一致。

## 4 常用操作

### 4.1 核心快捷键

| 操作 | Windows / Linux | macOS |
|------|----------------|-------|
| AI 聊天 | Ctrl+L | Cmd+L |
| AI 内联编辑 | Ctrl+K | Cmd+K |
| 接受 AI 建议 | Tab | Tab |
| 拒绝 AI 建议 | Esc | Esc |
| Composer 面板 | Ctrl+I | Cmd+I |
| 选择下一个补全位置 | Ctrl+Shift+Enter | Cmd+Shift+Enter |
| 在聊天中引用文件 | 输入 `@` 后选择 | 输入 `@` 后选择 |
| 查看快捷键列表 | Ctrl+K, Ctrl+S | Cmd+K, Cmd+S |

### 4.2 实战场景

**场景 A：给遗留代码添加错误处理**

```
1. 打开一个已有 200 行的 Python 脚本
2. 选中所有函数（Ctrl+A 全选文件内容）
3. 按 Ctrl+K
4. 输入：给所有函数添加 try/except，异常统一记录到 logger，
   关键操作添加中文日志，并在函数顶部添加 docstring
5. 等待 AI 生成 → 审查修改 → Tab 接受
```

**场景 B：解释和重构**

```
1. 选中一段复杂的正则表达式或 SQL 语句
2. 按 Ctrl+K
3. 输入：首先用中文注释解释这段代码的意图，
   然后将其改写为更可读的函数形式，将魔法数字提取为常量
4. AI 先逐行解释，然后给出重构版本
```

## 5 同类对比

| 对比维度 | Cursor | GitHub Copilot | Windsurf | VS Code + Continue 插件 |
|---------|--------|---------------|----------|-----------------------|
| AI 集成方式 | 编辑器原生 | 各种 IDE 的插件 | 编辑器原生 | VS Code/JetBrains 插件 |
| 代码补全 | 多行 + 跨文件 | 多行 | 多行 | 需配置 |
| AI 聊天 | 内置侧边栏 | 内置侧边栏 | 内置侧边栏 | 内置侧边栏 |
| 内联编辑（Ctrl+K） | 支持（最强） | 不支持 | 支持 | 不支持 |
| Composer 多文件 | 支持 | 不支持 | 支持（Cascade） | 不支持 |
| 自由选择模型 | GPT-4o/Claude/自有 | 仅 OpenAI | 自研模型为主 | 支持多种（Ollama 本地） |
| 免费额度 | 2000 次/月 | 无免费 | 有限免费 | 取决于 API Key |
| 订阅价格 | $20/月 (Pro) | $10/月 | $15/月 | 免费（自备 API Key） |

## 6 注意事项

!!! warning "数据隐私"
    Cursor 设置中有一条关键的 "Privacy Mode" 选项。**如果开启**，你的代码在传输过程中仅用于生成即时建议，不会在 Cursor 服务器上存储。**如果关闭**（为提升模型表现），部分代码片段可能被保留用于服务改进。处理公司内部代码或商业机密项目时，请务必开启 Privacy Mode。

!!! danger "AI 生成代码的安全审查"
    Cursor 生成的代码可能存在以下风险：（1）直接复制了训练数据中的受版权保护代码片段；（2）使用了已废弃的 API 或有已知漏洞的库版本；（3）在处理用户输入时缺少必要的校验和转义。**所有 AI 生成的代码在合并到主分支前必须经过人工 Code Review。**

!!! info "离线场景"
    Cursor 的 AI 功能依赖网络连接。在没有网络的飞机/火车上，它可以正常作为 VS Code 使用（编辑、调试、终端），但所有 AI 功能不可用。如果你需要离线也能使用 AI 辅助，考虑本地部署的方案（如 Continue + Ollama + CodeLlama）。

---

## 参考资源

- [Cursor 官网](https://cursor.sh)
- [Cursor 文档](https://docs.cursor.sh)
- [Cursor 变更日志](https://changelog.cursor.sh)
- [Anysphere 公司](https://anysphere.com)
