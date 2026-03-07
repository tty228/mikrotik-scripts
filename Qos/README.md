# Overview 概述

本项目提供一套适用于 **MikroTik RouterOS (ROS)** 的 **QoS 流量分类与限速策略**。

This project provides a **traffic classification and bandwidth control strategy for MikroTik RouterOS QoS**.

# QoS Priority Levels

本规则共 **7 个优先级队列**。

This QoS configuration uses **7 priority levels**.

| Priority | Name | Description |
|--------|------|-------------|
| 1 | L1 | TCP handshake / ICMP / very small packets |
| 2 | L2 | Web interaction packets |
| 3 | L3 | VoIP / Web content elements |
| 4 | L4 | File transfer / video / images |
| 5 | Misc | Multi-connection traffic |
| 6 | Max | Large packet transfers |
| 7 | P2P | P2P or manually limited traffic |

使用前：
![image](https://github.com/tty228/mikrotik-scripts/blob/main/other/2026-03-07-115435.png)

使用后：
![image](https://github.com/tty228/mikrotik-scripts/blob/main/other/2026-03-07-124628.png)
