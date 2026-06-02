# MATLAB
*MathWorks 出品的数值计算、算法开发与数据可视化环境，和 Simulink 构成学术与工程领域的标准工具链*


---

## 前言

MATLAB（MATrix LABoratory，矩阵实验室）是由 MathWorks 公司开发的商业数值计算环境。与通用编程语言不同，MATLAB 的核心抽象是矩阵（Matrix）：所有标量是 1x1 矩阵，向量是矩阵，图像是矩阵。这个设计使它在线性代数、信号处理、图像分析、控制系统和计算物理等领域成为事实标准。

在学术界，MATLAB 的许可证费用一直是争议点。教育版定价 $99/年（含 Simulink），商业版则高达 $2150/年（单用户）。围绕这个价格催生了 GNU Octave 和 Julia 等开源替代方案，但它们与 Simulink 均不兼容，因此自动驾驶、航空航天和嵌入式控制领域的相关从业者基本绕不开 MATLAB。

**本机版本：** R2024b  
**平台：** Windows / macOS / Linux  
**许可证：** 商业付费（学生版 $99 / 标准版 $2150 / 年）

---

## 1 概述

### 1.1 MATLAB 的特点

- **矩阵即一切**：变量默认是 `double` 类型矩阵，所有运算符（`+` `-` `*` `/`）按矩阵规则计算
- **交互式命令行**：在 Command Window 中键入表达式即刻执行并显示结果，适合快速探索数据
- **工具箱体系**：各项专业功能按工具箱（Toolbox）购买，互不捆绑

### 1.2 工具箱（Toolbox）分类

MATLAB 有 85+ 个可选工具箱，涵盖从深度学习到 CFD 的全部工程场景：

| 工具箱类别 | 常用工具箱 | 典型用户 |
|-----------|-----------|---------|
| 信号与图像 | Signal Processing Toolbox, Image Processing Toolbox | 通信/电子工程师 |
| 控制系统 | Control System Toolbox, Robotic System Toolbox | 自动化/控制工程师 |
| 计算物理 | Partial Differential Equation Toolbox | 力学/航空/能源领域 |
| 深度学习 | Deep Learning Toolbox, Computer Vision Toolbox | CV 研究员 |
| GIS 开发 | Mapping Toolbox | GIS 开发者 |

!!! note "工具箱定价"
    每个工具箱的年度订阅费用通常为 $500-2000。MATLAB 的高价格主要来自商业工具箱的嵌套需求：一个计算机视觉项目可能需要基础 MATLAB + Image Processing Toolbox + Computer Vision Toolbox + Deep Learning Toolbox，总计超过 $5000/年。

## 2 核心功能

### 2.1 交互式命令行

Command Window 是 MATLAB 最常用的交互方式：

```matlab
% 矩阵即变量
A = [1, 2, 3; 4, 5, 6; 7, 8, 9];   % 3x3 矩阵
B = inv(A) * A;                      % 逆矩阵运算

% 一例所有绘图指令
x = linspace(0, 2*pi, 100);
y = sin(x);
plot(x, y);                          % 一键打开 Figure 窗口显示正弦曲线

% 导入 Excel 数据
data = readtable('measurement.xlsx');
mean_val = mean(data.column_1);      % 读取并统计
```

### 2.2 编辑器与调试

MATLAB 编辑器具备专业的 IDE 能力：

- **断点**：行断点、条件断点、错误断点
- **代码分节**：`%% SectionTitle` 将脚本划分为独立运行的小节（Ctrl+Enter 运行当前节）
- **变量浏览器**：GUI 面板直接查看工作区中每个变量的类型、大小和最小值/最大值
- **性能分析（Profile）**：`profile on；run_your_script；profile viewer` 可视化每行代码的耗时分布

### 2.3 Simulink

Simulink 是 MATLAB 最知名的附加产品，也是 MATLAB 商业价值的核心。它是一种基于模型的设计（MBD）环境，通过拖拽模块连接来构建动态系统模型。在自动驾驶、电机控制、飞行器仿真等领域，Simulink 是法定的工具之一。

**典型 Simulink 项目流程：**

```
1. 在 Simulink 中搭建控制系统的功能框图
2. 通过 Embedded Coder 将框图自动转换成 C/C++ 代码
3. 将生成的代码部署到目标硬件（如 STM32、TI C2000）
4. 在 Simulink 中运行硬件在环测试验证
```

### 2.4 与 Python 的互操作

MATLAB R2024b 起显著加强了与 Python 的集成：

```matlab
% 在 MATLAB 中调用 Python
py.importlib.import_module('numpy');
np = py.importlib.import_module('numpy');
arr = py.numpy.array([1, 2, 3, 4, 5]);
result = py.numpy.sum(arr)           % 结果返回到 MATLAB 变量

% 在 MATLAB 中使用 pandas
pd = py.importlib.import_module('pandas');
df = pd.read_csv('data.csv');
```

## 3 安装与配置

### 3.1 系统需求

- **操作系统**：Windows 10/11、macOS 11+、Linux（Ubuntu/RHEL）
- **内存**：推荐 8 GB+（大型 Simulink 模型或深度学习任务 32 GB+）
- **磁盘**：基础安装 ~4 GB，全套工具箱安装 ~25 GB
- **显卡**：深度学习工具箱需要 NVIDIA GPU + CUDA

### 3.2 安装步骤

1. 注册 MathWorks 账号（需使用学校邮箱申请教育版或联系单位授权部门）
2. 访问 [https://www.mathworks.com/downloads](https://www.mathworks.com/downloads)
3. 下载对应系统的安装引导程序
4. 运行安装程序 → 登录 MathWorks 账号
5. 选择许可证（学生/商业/试用）
6. 选择要安装的产品列表（如果磁盘允许，建议勾选所有常用工具箱）
7. 安装路径不要包含中文字符或空格

### 3.3 首次配置

- **设置工作目录**：Home → Set Path → 添加常用代码库目录
- **编辑器字体**：Home → Preferences → Editor/Debugger → Display → Font 推荐 Cascadia Code 或 Consolas
- **快捷键**：Preferences → Keyboard → Shortcuts → 可选择 VS Code 或 Eclipse 风格

## 4 常用操作

```matlab
% ---- 基础命令速查 ----

clear;           % 清空工作区变量
clc;             % 清空 Command Window
close all;       % 关闭所有 Figure 窗口
help <function>  % 查看函数文档
doc <function>   % 打开函数帮助文档（更详细的 HTML 页面）

% ---- 绘图 ----

x = 0:0.1:10;
y1 = sin(x);
y2 = cos(x);

figure;                          % 创建新图像窗口
hold on;                         % 在一张图上叠加
plot(x, y1, 'r-', 'LineWidth', 2);
plot(x, y2, 'b--');
legend('sin(x)', 'cos(x)');
xlabel('x');
ylabel('y');
title('Sin and Cos Curves');
grid on;
```

## 5 同类对比

| 对比项 | MATLAB | GNU Octave | Python (NumPy/SciPy) | Julia |
|-------|-------|-----------|-------------------|-------|
| 许可证 | 商业付费（$99+） | 免费开源 | 免费开源 | 免费开源 |
| 语法 | 适合矩阵操作 | 接近 MATLAB | 通用编程语法 | 类似 MATLAB |
| 工具箱生态 | 极丰富（85+ 工具箱） | 有限 | Python 包生态（pip） | 包生态成长中 |
| Simulink | 原生支持 | 不支持 | 不支持 | 不支持 |
| 性能 | 商业优化（优秀） | 中等 | 好（需 NumPy 向量化） | 极好 |
| 应用领域 | 学术/工业标准 | 教学 | 工业/Web | 科学研究 |
| 学习曲线 | 低（交互式环境） | 低 | 中 | 中 |

---

## 参考资源

- [MATLAB 官网](https://www.mathworks.com/products/matlab.html)
- [MATLAB 文档](https://www.mathworks.com/help/matlab/)
- [MATLAB 常用函数速查（PDF）](https://www.mathworks.com/help/releases/R2024b/pdf_doc/matlab/matlab_quickref.pdf)
- [MathWorks 学习中心](https://matlabacademy.mathworks.com)
