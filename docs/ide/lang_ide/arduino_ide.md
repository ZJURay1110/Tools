# Arduino IDE
*Arduino 微控制器的官方编程与上传环境，适合嵌入式入门和快速原型开发*


---

## 前言

Arduino 是一个开源电子原型平台。Arduino IDE 是 Arduino 项目官方提供的编程环境，它所做的核心事情只有两件：写代码，然后通过 USB 把代码烧录到微控制器开发板上。

Arduino IDE 不是一个通用 IDE。它的语言是 C++ 的一个子集封装（Arduino 框架），它的编译和链接针对 AVR/ARM/RISC-V 等嵌入式架构设计。开发者不需要关心交叉编译链的配置、链接脚本的编写或烧录工具的调用 —— Arduino IDE 将这一切隐藏在"上传"按钮背后。这也是它能够在非嵌入式专业人群（如设计师、艺术家、创客）中广泛流行的原因。

**本机版本：** 2.3.4  
**平台：** Windows / macOS / Linux  
**许可证：** AGPLv3（免费开源）

---

## 1 概述

### 1.1 Arduino IDE 2.x vs 1.x

2022 年起 Arduino 官方推出了 2.x 版本，与 1.x 的差异很大：

| 特性 | 1.x（传统版） | 2.x（新版） |
|------|-------------|------------|
| 编辑器引擎 | Java Swing | VS Code 代码技术（Monaco Editor） |
| 代码补全 | 无 | 有（基础） |
| 自动完成 | 无 | 基础符号补全 |
| 调试 | 不支持 | 可通过 Debugger 插件 |
| 串口监视器 | 单独窗口 | 集成在编辑器底部 |
| 主题 | 默认亮色 | 深色 + 亮色切换 |
| 插件支持 | 无 | 有（实验性） |

!!! warning "决定使用哪个"
    如果你正在复现 2020 年以前的教程（如大部分中文 Arduino 图书），教程中的截图对应的是 1.x 版。2.x 版仍保持与 1.x 兼容，界面布局也保留大部分相似性，但 2.x 的稳定性在发布初期低于 1.x。如果上传过程中频繁出错，换回 1.x 往往是可用的办法。

## 2 核心功能

### 2.1 编译与上传

这是 Arduino IDE 的核心工作流：

```cpp
// void setup() —— 只运行一次，用于引脚初始化和硬件配置
void setup() {
    pinMode(13, OUTPUT);        // 将数字引脚 13 设置为输出模式
    Serial.begin(9600);         // 初始化串口通信，波特率 9600
}

// void loop() —— 不断重复执行，Arduino 的标准主循环
void loop() {
    digitalWrite(13, HIGH);     // 给引脚 13 输出高电平（LED 亮）
    delay(1000);                // 延迟 1000 毫秒（1 秒）
    digitalWrite(13, LOW);      // 低电平（LED 灭）
    delay(1000);
}
```

操作流程：

```
1. 将 Arduino 板通过 USB 连接到电脑
2. 工具（Tools）→ 开发板（Board）→ 选择 Arduino Uno（或对应的型号）
3. 工具（Tools）→ 端口（Port）→ 选择 Arduino 对应的 COM 端口
4. 点击 "上传" 按钮（→ 图标）
5. 等待底部状态显示 "上传完成"
```

### 2.2 串口监视器

串口监视器（Serial Monitor）是嵌入式开发的重要调试通道。开发板无法像电脑一样在屏幕上 print 输出（因为没有屏幕），但可以通过 USB 串口把调试信息发送到电脑：

```cpp
void setup() {
    Serial.begin(9600);          // 初始化串口速率 9600bps
}

void loop() {
    int sensorValue = analogRead(A0);   // 读取模拟引脚 A0 的原始值（0-1023）
    Serial.print("Sensor: ");
    Serial.println(sensorValue);        // 在串口监视器中打印
    delay(500);
}
```

在 Arduino IDE 中点击工具栏右侧的"串口监视器"图标（放大镜），即可看到传感器数据在窗口中持续输出。波特率必须设置一致（Serail.begin(9600) 与监视器窗口右下角的 9600 匹配）。

### 2.3 库管理

Arduino 生态的一大优势是其庞大的第三方库。Tools → Manage Libraries（或左侧库图标）：

- 搜索库：`DHT`（温湿度传感器）、`LiquidCrystal`（LCD 显示屏）、`Servo`（舵机）
- 一键安装：点击 Install
- 安装完成后，在代码中用 `#include <dht.h>` 导入

```cpp
#include <dht.h>

DHT sensor(2);          // DHT11 传感器连接在引脚 2

void setup() {
    Serial.begin(9600);
}

void loop() {
    float temperature = sensor.readTemperature();  // 读取温度（摄氏度）
    float humidity = sensor.readHumidity();         // 读取湿度（百分比）
    Serial.print("Temp: ");
    Serial.print(temperature);
    Serial.print(" C, Humidity: ");
    Serial.print(humidity);
    Serial.println(" %");
    delay(2000);
}
```

## 3 安装与配置

### 3.1 系统需求

- **操作系统**：Windows 10+ / macOS 11+ / Linux
- **磁盘**：约 300 MB（2.x 版）/ 约 150 MB（1.x 版）
- **USB 驱动**：Windows 通常自动识别，部分国产克隆板（CH340 芯片）可能需要手动安装驱动

### 3.2 安装

1. 访问 [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)
2. 选择 "Arduino IDE 2.x.x" 下载

3. **Windows 用户**：
   - 下载 `.exe` 安装程序
   - 运行安装，全部默认即可
   - 安装过程中会提示安装 USB 驱动，选择"安装"

4. **首次启动**：
   - 打开 IDE → 文件 → 示例 → 01.Basics → Blink
   - 连接 Arduino 板 → 核对开发板型号和端口 → 点击上传

### 3.3 添加第三方开发板支持

Arduino IDE 原生支持 Arduino 官方的板（Uno、Mega、Nano、Due 等）。对 ESP8266、ESP32 等第三方板，需要通过开发板管理器添加：

```
1. 文件 → 首选项 → "附加开发板管理器网址"
2. 添加以下 URL（ESP32 为例）：
   https://dl.espressif.com/dl/package_esp32_index.json
3. 工具 → 开发板 → 开发板管理器
4. 搜索 ESP32 → 安装（约 500 MB，需要下载 ESP-IDF 工具链）
5. 安装完成后在工具 → 开发板中会多出 ESP32 相关的板型列表
```

```bash
# 常用的开发板管理器 JSON URL
Arduino AVR（官方，已预装）：不需要额外添加
ESP8266：https://arduino.esp8266.com/stable/package_esp8266com_index.json
ESP32：https://dl.espressif.com/dl/package_esp32_index.json
STM32：https://github.com/stm32duino/BoardManagerFiles/raw/main/package_stmicroelectronics_index.json
```

### 3.4 常用设置

- **字体**：文件 → 首选项 → 编辑器字体大小：建议 14-16（IDE 界面字体较小）
- **自动格式化**：工具 → 自动格式化（Ctrl+T），规范化大括号和缩进
- **行号**：首选项 → 显示行号

## 4 常用操作

| 操作 | 快捷键 |
|------|-------|
| 验证/编译（仅检查语法不烧录） | Ctrl+R |
| 上传到开发板 | Ctrl+U |
| 打开串口监视器 | Ctrl+Shift+M |
| 新建项目 | Ctrl+N |
| 打开示例 | Ctrl+O |
| 增大字体 | Ctrl+= |
| 减小字体 | Ctrl+- |
| 自动格式化 | Ctrl+T |

### 4.1 上传失败排查步骤

```
1. 检查 USB 线：数据线（非充电线）。红色充电线无法传输数据
2. 开发板选择：工具 → 开发板 → Arduino Uno（与硬件一致）
3. COM 端口选择：工具 → 端口 → 选择已连接的端口（Windows 显示为 COMx）
4. 如果端口为空：检查 USB 驱动（CH340 芯片需手动安装驱动）
5. 重启 Arduino IDE 或重新插拔 USB
6. 按住开发板上的 Reset 按钮，点击上传，在编译日志出现时松开
```

## 5 同类对比

| 对比项 | Arduino IDE | PlatformIO (VS Code) | ESP-IDF (ESP32 官方) |
|-------|------------|---------------------|---------------------|
| 目标用户 | 入门创客/爱好者 | 中级嵌入式开发者 | 专业嵌入式工程师 |
| 配置复杂度 | 极低（即插即用） | 中等（需理解 platform.ini） | 高（需管理工具链） |
| 编译速度 | 中等 | 较快 | 慢（完整 IDF） |
| 代码补全 | 2.x 基本支持 | 极好（Clangd） | 弱（终端操作） |
| 调试器支持 | 弱（需插件） | 支持 J-Link/OpenOCD | 支持 JTAG |
| 库生态 | Arduino 库 | PlatformIO 注册表 + Arduino | 由官方维护的 IDF 组件 |
| 多框架支持 | Arduino 框架 | Arduino/IDF/STM32Cube 等 | 仅 ESP-IDF |
| 适用阶段 | 入门原型 | 项目开发 | 量产产品 |

## 6 注意事项

!!! warning "USB 线类型"
    Arduino 板通过 USB 供电且传送数据。如果你使用一根只支持充电的 USB 线（手机充电线），电脑能识别到开发板但不能上传代码。如果你换了波特率、库、开发板类型后仍然上传失败，首先检查的应该是线。

!!! info "CH340 驱动"
    国内很多兼容 Arduino 的克隆板使用的是 CH340G USB 转串口芯片。这些板插上电脑后可能不显示端口，因为 Windows 未预装 CH340 驱动。从 [http://www.wch.cn/download/CH341SER_EXE.html](http://www.wch.cn/download/CH341SER_EXE.html) 下载并安装即可。

!!! danger "上传前断开其他串口程序"
    如果串口监视器或第三方串口工具（如串口助手、PuTTY）正在占用 Arduino 的 COM 口，上传会失败（"port is already in use"）。关闭所有占用该端口的程序后再试。

---

## 参考资源

- [Arduino 官网](https://www.arduino.cc)
- [Arduino IDE 下载](https://www.arduino.cc/en/software)
- [Arduino 语言参考](https://www.arduino.cc/reference/en/)
- [PlatformIO IDE](https://platformio.org)
- [ESP32 Arduino 核心](https://github.com/espressif/arduino-esp32)
