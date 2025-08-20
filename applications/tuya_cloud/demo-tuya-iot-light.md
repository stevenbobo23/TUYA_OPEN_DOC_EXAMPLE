---
title: switch_demo
---


`switch_demo` 是涂鸦 IoT 应用是涂鸦 AI+IoT 平台提供的一种最小功能应用演示，一个简单的，跨平台、跨系统、支持多种连接的开关示例，通过涂鸦 APP、涂鸦云服务，可以对这个开关进行远程控制（外出）、局域网控制（同一局域网）和蓝牙控制（没有可用网络）。

`switch_demo` 当前演示功能如下：
1. 支持蓝牙配网
2. 支持 WiFi AP 模式配网
3. 接收来自云端的 MQTT 控制数据，并自动回复
4. 接收来自 APP 的局域网 TCP 控制数据，并自动回复
5. OTA 功能

当前 `switch_demo` 未控制真实的硬件，所以可以在当前支持的所有 [platform](../../about-tuyaopen.md#支持-platform) 上运行。

使用 `switch_demo` 之前，你需要先了解以下名词：
1. [TuyaOpen 专用授权码](../../quick-start/index.md#tuyaopen-专用授权码)
2. [PID](../../quick-start/index.md#pid)
3. [配网](../../quick-start/device-network-configuration.md)
4. [DP](../../applications/index.md#dp)

## 默认 APP 控制面板

![](https://images.tuyacn.com/fe-static/docs/img/0e155d73-1042-4d9f-8886-024d89ad16b2.png)

## 目录结构

```sh
+- switch_demo
    +- src
        -- cli_cmd.c
        -- tuya_main.c
        -- tuya_config.h
    -- CMakeLists.txt
    -- README_CN.md
    -- README.md
```

- cli_cmd.c: switch_demo 的一些命令行操作，用于查看、操作 switch_demo 的信息和状态
- tuya_main.c: switch_demo 的主要功能
- tuya_config.h: 涂鸦PID和授权信息，在涂鸦IoT平台上创建并获取，可以参考文档 [TuyaOS quickstart](https://developer.tuya.com/en/docs/iot-device-dev/application-creation?id=Kbxw7ket3aujc)

## 支持硬件

当前工程可在所有当前已支持的芯片和开发板上运行

## 编译

1. 运行 `tos config_choice` 命令， 选择当前运行的开发板或 platform。
2. 如需修改配置，请先运行 `tos menuconfig` 命令修改配置。
3. 运行 `tos build` 命令，编译工程。
