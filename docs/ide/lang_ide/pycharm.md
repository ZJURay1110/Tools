# PyCharm
*JetBrains 出品的 Python 专用 IDE，覆盖 Web 开发、数据科学与脚本编写全场景*


---

## 前言

PyCharm 是 JetBrains 公司专门为 Python 开发打造的 IDE，也是 Python 社区中使用最广泛的专业级 IDE。它分为两个版本：Community（免费开源）和 Professional（付费，$249/年或 $24.90/月）。两个版本的区别不在于性能，而在于集成的工具链深度。

PyCharm 区别于 VS Code + Python 插件的核心优势在于：**开箱即用的深度集成**。Django 的路由跳转和模板补全、Jupyter Notebook 的变量监视和数据帧查看、数据库工具面板的 SQL 自动补全 —— 这些功能在 VS Code 中需要 5-6 个插件组合才能部分实现，而在 PyCharm 中全部内置。

**本机版本：** 2024.2  
**平台：** Windows / macOS / Linux  
**许可证：** Community 免费（Apache 2.0）/ Professional 付费

---

## 1 概述

### 1.1 Community vs Professional

| 功能 | Community | Professional |
|------|-----------|-------------|
| Python 编辑器与调试器 | 有 | 有 |
| Git / Mercurial 集成 | 有 | 有 |
| 代码补全与重构 | 有 | 有 |
| 单元测试（pytest/unittest） | 有 | 有 |
| 虚拟环境管理 | 有 | 有 |
| Django / Flask 支持 | 无 | 有 |
| SQL / 数据库工具 | 无 | 有 |
| Jupyter Notebook 集成 | 无 | 有 |
| 科学工具（Matplotlib / NumPy） | 无 | 有 |
| 远程开发（SSH/Docker） | 无 | 有 |

!!! note "Community 版对大多数人够用"
    如果你写的是纯粹的 Python 脚本、CLI 工具、Tkinter/PyQt 桌面应用，Community 版的功能已经完全够用。Professional 版的价值体现在 Django Web 开发和 Jupyter 数据科学场景。

## 2 核心功能

### 2.1 智能代码补全

PyCharm 的 Python IntelliSense 提供以下能力：

- **基于类型注解的补全**：如果函数签名包含类型注解（`-> list[int]`），补全会精确到返回值的属性和方法
- **Django 模型字段补全**：在 `.filter()` 中自动补全模型字段名
- **循环变量推断**：当遍历 `stringList: list[str]` 时，循环变量自动推断为 `str` 类型
- **文档字符串检查**：`"""` 后自动生成参数类型和返回类型模板

### 2.2 调试器

除了标准的断点调试，PyCharm 的调试器有几个独特功能：

- **行内变量显示**：调试模式下，变量值直接显示在代码行尾，无需悬停
- **数据帧查看器**：调试过程中，查看 Pandas DataFrame 的列统计和行采样
- **远程调试**：在服务器上调试运行中的 Django 应用
- **并发调试**：跟踪多线程和多进程的调用路径

!!! tip "调试器中的 Evaluate Expression"
    在断点暂停时按 Alt+F8，可以执行任意 Python 表达式（如 `list(range(10))`），结果直接在弹窗中显示。这比在代码中临时加 print 再重跑高效得多。

### 2.3 数据库工具

Professional 版内置了 DataGrip 的核心功能，可以在 PyCharm 中直接连接和操作数据库：

- 支持 MySQL / PostgreSQL / SQLite / Oracle / SQL Server 等
- SQL 编辑器自动补全表名、列名、关键字
- 查看表数据、编辑行、执行查询
- 从 SQL 结果直接生成 Pandas 导入代码

### 2.4 Django 支持

这是 PyCharm Professional 的核心卖点：

- Django 管理命令面板（`python manage.py ...`）
- 模型类中 `class Meta:` 的字段名补全
- 在模板 `.html` 文件中补全模板标签和过滤器
- 从 `urls.py` 路由名跳转到视图函数
- ORM 查询的 SQL 预览

### 2.5 Jupyter Notebook 集成

Professional 版可直接在 PyCharm 中创建和编辑 `.ipynb` 文件：

- 单元格编辑 + 补全
- 变量渲染（DataFrame 的富表格显示）
- Matplotlib 图表内联显示
- `Shift+Enter` 执行当前单元格
- 在 Notebook 中设置断点并调试

## 3 安装与配置

### 3.1 安装

1. 访问 [https://www.jetbrains.com/pycharm/download](https://www.jetbrains.com/pycharm/download)
2. 选择 Community（下）或 Professional（上）版本下载
3. Windows 用户运行 `.exe` 安装程序

### 3.2 首次配置

**Python 解释器配置（项目新建时的关键步骤）：**

```
1. File → New Project
2. Location：项目路径
3. Environment Type：
   - New environment（使用 Virtualenv）→ 推荐
   - 选择 Base interpreter（指向系统 Python 或 Anaconda 的 python.exe）
4. 勾选 "Create a main.py welcome script"
5. Create

如果已有项目代码：
1. File → Open → 选择包含 Python 源码的目录
2. 如果右下角弹出 "No Python interpreter configured"，点击 → Add Interpreter
```

**推荐设置：**

- Settings → Editor → Font → Size: 14，勾选 Font Ligatures
- Settings → Editor → General → Code Completion → Case sensitive completion: None（大小写不敏感匹配）
- Settings → Tools → Python Integrated Tools → Default test runner: pytest

### 3.3 必备插件

| 插件 | 用途 |
|------|------|
| .env files support | `.env` 环境变量补全 |
| Rainbow Brackets | 彩色括号提高可读性 |
| Key Promoter X | 提示操作的对应快捷键 |

### 3.4 推荐开发环境搭配

```bash
# 创建一个 Conda 环境给 PyCharm 项目使用
conda create --name my_project python=3.11
conda activate my_project
conda install black pylint mypy pytest

# 在 PyCharm 的 Python Interpreter 设置中选择此 Conda 环境
# Settings → Project → Python Interpreter → Add → Conda Environment
```

## 4 常用操作

| 操作 | Windows / Linux | macOS |
|------|----------------|-------|
| 搜索所有位置 | Ctrl+Shift+F | Cmd+Shift+F |
| 搜索类/文件 | Ctrl+N | Cmd+O |
| 转到定义 | Ctrl+B 或 Ctrl+Click | Cmd+B 或 Cmd+Click |
| 查找引用 | Alt+F7 | Alt+F7 |
| 快速修复 | Alt+Enter | Alt+Enter |
| 格式化代码 | Ctrl+Alt+L | Cmd+Option+L |
| 优化导入 | Ctrl+Alt+O | Ctrl+Option+O |
| 运行 | Shift+F10 | Ctrl+Shift+R |
| 调试 | Shift+F9 | Ctrl+Shift+D |
| 单步调试 | F8 | F8 |
| 进入函数 | F7 | F7 |

## 5 同类对比

| 对比项 | PyCharm Professional | VS Code + Python 插件 | Spyder（Anaconda） |
|-------|-------------------|----------------------|-------------------|
| 启动速度 | 慢 8-15 秒 | 快 2-3 秒 | 中 4-6 秒 |
| 内存占用（空项目） | ~1.2 GB | ~400 MB | ~600 MB |
| Django 支持 | 顶级（原生） | 良好（插件） | 无 |
| Jupyter 集成 | 优秀（原生） | 良好（插件） | 优秀（原生） |
| 变量浏览器 | 专业 | 基础 | 内置 |
| 数据库工具 | 内含 | 需插件 | 无 |
| 远程开发 | 内置 | 内置（Remote-SSH） | 无 |
| 价格 | $249/年 | 免费 | 免费 |

---

## 参考资源

- [PyCharm 官网](https://www.jetbrains.com/pycharm/)
- [PyCharm 文档](https://www.jetbrains.com/help/pycharm/)
- [PyCharm Community 源码](https://github.com/JetBrains/intellij-community/tree/master/python)
