# 🌐 MikroTik(ROS) Cloudflare DDNS 脚本（RouterOS v7.x）

![](https://api.visitorbadge.io/api/visitors?path=https://github.com/tty228/mikrotik-cloudflare-dns&label=View%20Count)

[English](README.md) | [中文文档](README_CN.md)

这个脚本适用于 **MikroTik RouterOS v7.x**，通过 Cloudflare API 自动更新 DDNS 记录（支持 A 和 AAAA）。支持多域名、IPv6。

---

## ✨ 功能特性

- ✅ **支持多个域名和记录类型**（A / AAAA）同时更新  
- 🔐 **使用 Cloudflare API Token，设置更简单**  
- ➕ **自动新建域名记录，无需手动创建**  
- 🧠 **使用缓存机制，避免高频 API 请求，支持强制更新时间间隔**  
- 📤 **支持提交本机或内网设备的 IPv6 地址**（如 `::1`、手动后缀拼接、MAC 地址获取）  
- 📡 **使用 Cloudflare DNS API 读取域名记录，而非 DNS 解析**

---

## 🔑 获取 Cloudflare API Token

1. 前往 [Cloudflare API Tokens 页面](https://dash.cloudflare.com/profile/api-tokens)
2. 请勿使用全局 token
3. 点击 **"创建令牌"**，选择 **"编辑区域 DNS（使用模板）"**
4. 创建后复制你的 Token 并填写到脚本中的 `CFtoken` 变量

## 🔧 配置说明

在脚本顶部设置以下变量：

```
:local CFiface "pppoe-out1"      # 获取IPv4地址的接口
:local CFiface6 "pppoe-out1"     # 获取IPv6前缀的接口
:local CFzoneid "你的Zone ID"    # 区域 ID
:local CFtoken "你的API令牌"      # 创建令牌->编辑区域 DNS (请勿使用全局 API)
# 设置要更新的记录（支持多个）：
:local DomainsToUpdate {
    "v4.domain.com|A";
    "v6.domain.com|AAAA";
    "ds.domain.com|A";
    "ds.domain.com|AAAA";
}
```