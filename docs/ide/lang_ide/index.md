# 单语言专用 IDE
*为特定编程语言或领域深度定制的集成开发环境*


---

## 前言

单语言专用 IDE 与通用 IDE 的区别在于：它们为某一门语言或某一类开发场景做了深度定制，用户体验在设计之初就围绕目标语言的核心工作流展开。例如 PyCharm 的 Django 模板补全和 Jupyter Notebook 支持，CLion 的 CMake 深度集成和内置 Sanitizer 可视化，MATLAB 的交互式命令行与图形化调试器 —— 这些功能在通用 IDE 中需要安装大量插件后才能部分模拟，但效果往往不够理想。

如果你的大多数时间都在使用同一门语言，切换到专用 IDE 会带来更流畅的体验。如果语言经常切换，通用 IDE 的灵活性更合适。

!!!

## 1 本类目收录工具

| 工具名称 | 一句话描述 | 核心语言 | 平台 | 许可证 |
|---------|-----------|---------|------|--------|
| [PyCharm](pycharm.md) | JetBrains 出品的 Python IDE，Django/Jupyter/科学计算深度支持 | Python | Windows / macOS / Linux | Community 免费 |
| [CLion](clion.md) | JetBrains 出品的 C/C++ IDE，CMake 原生集成，Sanitizer 可视化 | C / C++ | Windows / macOS / Linux | 付费（$99/年起） |
| [MATLAB](matlab.md) | MathWorks 出品的数值计算和环境，学术和工程领域标配 | MATLAB / Simulink | Windows / macOS / Linux | 商业付费（学生版 $99） |
| [Dev-C++](dev_cpp.md) | 轻量级 C/C++ IDE，国内高校 C 语言教学常用 | C / C++ | Windows | 免费开源 |
| [Thonny](thonny.md) | 面向 Python 初学者的 IDE，内置变量查看器和步进调试 | Python | Windows / macOS / Linux | 免费开源 |
| [Arduino IDE](arduino_ide.md) | Arduino 微控制器编程工具，一键编译上传到开发板 | C++（Arduino 框架） | Windows / macOS / Linux | 免费开源 |

## 2 按语言快速选择

| 开发场景 | 推荐工具 | 理由 |
|---------|---------|------|
| Python Web（Django/Flask） | PyCharm Professional | Django 模型可视化 + 路由跳转 |
| Python 数据科学 | PyCharm Professional 或 VS Code | Jupyter 集成（PyCharm 更友好） |
| C/C++ 跨平台开发 | CLion | CMake 原生，Linux/macOS/Windows 一致 |
| C/C++ 竞赛/教学 | Dev-C++ 或 Code::Blocks | 启动快，占内存小 |
| Python 入门教学 | Thonny | 内置步进调试和变量可视化 |
| 嵌入式 / Arduino | Arduino IDE | 极简，一键编译+上传 |
| 学术数值计算 | MATLAB | Simulink 建模 + 官方工具箱生态 |

---

## 相关资源

- [JetBrains 官网](https://www.jetbrains.com)
- [Python 官方](https://www.python.org)
- [Arduino 官网](https://www.arduino.cc)
