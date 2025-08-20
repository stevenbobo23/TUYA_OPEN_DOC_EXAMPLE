---
title: T5AI-Board 概述
---

# **T5AI-Board** 开发套件

![T5-AI Board DevKit](https://images.tuyacn.com/fe-static/docs/img/83859360-38f6-42c2-9614-99b47f487775.jpg)


## 软件编译配置

板级配置文件定义了外设驱动、引脚映射、BSP 包以及第三方库等核心功能组件的配置参数。通过使用开发板预配置的板级配置文件，可以显著降低硬件适配和驱动开发的工作量，提高开发效率。


:::tip 想要开发新的外设？
**Config 配置特点：**
- **用户如需新增外设，可直接在应用层编写驱动。** BSP 驱动主要用于板卡内部固化的外围器件。
- 不同应用的外设需求可能存在配置差异，需要根据具体需求调整 `config` 文件。
- 不同应用需求可能需要配置不同的第三方库参数。
- **建议** 以初始配置文件作为 **板级基础模板**，在此基础上进行二次开发和功能扩展。
:::

#### 怎么使能 config? 请参阅：[TOS 工具指南 - 配置选择](/docs/tos-tools/tos-guide#config-choice)

<table class="hw-config-flag-table">
  <tbody>
    <tr>
      <th>编译标志</th>
      <td><code>TUYA_T5AI_BOARD_LCD_3.5.config</code></td>
      <td>T5AI-Board + 3.5 寸屏幕 BSP 板卡配置 - <a href="https://github.com/tuya/TuyaOpen/blob/master/apps/tuya.ai/your_chat_bot/config/TUYA_T5AI_BOARD_LCD_3.5.config">配置文件</a></td>
    </tr>
    <tr>
      <th>BSP 驱动源码</th>
      <td colspan="2"><a href="https://github.com/tuya/TuyaOpen/tree/master/boards/T5AI/TUYA_T5AI_BOARD">T5AI-Board BSP 驱动源码</a></td>
    </tr>
  </tbody>
</table>

---

## 硬件概述

涂鸦 T5AI-Board 是一款基于 T5-E1-IPEX 的语音和屏幕多交互开发板，T5-E1-IPEX 是涂鸦智能开发的嵌入式 Wi-Fi 和蓝牙组合模块。该开发板配备 2 个麦克风和 1 个扬声器，支持语音识别和播放，提供语音交互功能。

通过开发板上的 I/O 连接器，您可以使用 LCD 显示堆叠模块来实现触摸屏和摄像头捕获功能。您还可以设计自己的 LCD 屏幕，支持多种接口，包括 I2C、SPI、8080 和 RGB 接口。

---
## 开发套件亮点
- 涂鸦 T5 MCU 模块（Wi-Fi 2.4G + BLE 5.4）
- 8 MB Flash
- 16 MB RAM
- 串行固件下载和调试日志
- 2 通道麦克风
- 1 通道扬声器
- TF 卡槽
- 模块完整引脚引出
- 板载 2.4 GHz Wi-Fi 天线
- USB 主机接口
- USB 供电
- （可选堆叠模块）RGB565 显示 + DVP 摄像头支持

## 详细规格

| 特性 | 规格 |
|---------|---------------|
| 板载模块 | T5-E1-IPEX |
| CPU | ARMv8-M Star (M33F) @480MHz |
| 缓存 | 16KB ITCM 和 16KB DTCM |
| 闪存 | 8 MB SiP 闪存 |
| RAM | 16 MB SiP PSRAM |
| SRAM | 640 KB 共享 SRAM |
| 音频 ADC | 2 通道 16 位 48KHz |
| 音频 DAC | 1 通道 16 位 48KHz |
| 均衡器 | 4 段数字均衡器 |
| 摄像头 | DVP 接口 |
| 显示 | RGB 和 8080 接口 |
| 扩展 | TF 卡支持 |
| GPIO | 56 个 GPIO |
| 接口 | 2x SPI, 2x QSPI, 3x UART, 2x I2C, 1x SDIO, 1x CAN, 12x PWM, 3x I2S |
| 标准 | 符合 IEEE 802.11b/g/n/ax |
| 蓝牙 | 蓝牙 LE 5.4 |
| USB type-C | 输入：5V@1A，固件下载和调试 |

---

## 引脚定义
T5AI-Board 通过其扩展接头提供全面的引脚选项。以下是可用引脚及其功能的详细说明：

![T5-AI Board Pinout](https://images.tuyacn.com/fe-static/docs/img/6b7ab959-0635-4293-991b-b8dda293614b.jpg)

### 下载高清引脚图：
[![](https://img.shields.io/badge/V102-下载%20PDF%20引脚图-orange?style=for-the-badge)](/docs/hardware/T5-AI-Board-Pinout-v102.pdf)

---
## LCD 屏幕 + 摄像头模块
T5AI-Board 支持可选的 LCD 屏幕和摄像头模块，可以堆叠在主板上。

#### 显示规格：
- 3.5" TFT 显示屏，320×480 RGB 分辨率
- TFT 显示驱动：`ILI9488`
- 触摸面板驱动：`GT1151QM`

#### 摄像头规格：
- 图像传感器：`GC2145`
- 分辨率：2MP（1616 x 1232 像素）
- I2C 通信地址：`0x78` 和 `0x79`
- [查看摄像头数据手册](https://e2e.ti.com/cfs-file/__key/communityserver-discussions-components-files/968/GC2145-CSP-DataSheet-release-V1.0_5F00_20131201.pdf)

### 引脚配置
下图显示了 LCD 屏幕和摄像头模块使用的引脚分配：
![Stacking Module Pin Usage](https://images.tuyacn.com/content-platform/hestia/173693668247bb1930ac5.png)

:::info 重要引脚注意事项
- 摄像头和触摸面板共享一个公共 I2C 接口。
- TF 卡引脚 `DATA3` 和 `DATA2` 与模块的 UART 端口共享，用于固件更新。
:::


## 下载资源
#### T5AI-Board 开发板
- [T5AI-Board 原理图](https://images.tuyacn.com/content-platform/hestia/174243908480e34e64d08.pdf) ：T5AI-Board 完整电路图。
- [T5AI-Board 引脚图](/docs/hardware/T5-AI-Board-Pinout-v102.pdf) ：详细的引脚映射和接口布局。
- [LCD 和摄像头模块原理图](https://images.tuyacn.com/content-platform/hestia/17387200670bcae1561bf.pdf) ：显示和摄像头模块板的电路图。
#### T5 MCU 数据手册
- [T5-E1-IPEX 模块数据手册](https://developer.tuya.com/en/docs/iot/T5-E1-IPEX-Module-Datasheet?id=Kdskxvxe835tq#title-12-Pin%20definition)：T5-E1-IPEX 模块的技术规格和引脚定义。
- [T5 MCU 芯片技术数据手册](https://images.tuyaeu.com/content-platform/hestia/1731549161e5fd8879de6.pdf)：T5 系列的综合技术规格和参考文档。


### USB 转串口驱动安装
T5AI-Board 使用板载 CH343 USB 转串口芯片进行固件烧录和调试。请下载适合您操作系统的驱动程序：

- [Windows 驱动](https://www.wch-ic.com/downloads/CH343SER_ZIP.html)
- [Linux 驱动](https://github.com/WCHSoftGroup/ch343ser_linux)
- [macOS 驱动](https://github.com/WCHSoftGroup/ch34xser_macos)


## 相关技术文档/Demo
- [T5AI-Board 入门指南 - (环境搭建 + 烧录 Demo）](/docs/quick-start/enviroment-setup)
- [T5AI-Board Demo 聊天机器人](/docs/applications/tuya.ai/demo-your-chat-bot)
- [T5AI-Board Demo IoT 智能插座/灯](/docs/applications/tuya_cloud/demo-tuya-iot-light)
- [T5AI-Board Demo WIFI/BT 和其他外设](/docs/examples/demo-generic-examples)
