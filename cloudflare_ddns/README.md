# 🌐 MikroTik(ROS) Cloudflare DDNS Script (RouterOS v7.x)

![](https://api.visitorbadge.io/api/visitors?path=https://github.com/tty228/mikrotik-cloudflare-dns&label=View%20Count)

[English](README.md) | [中文文档](README_CN.md)

This script is designed for **MikroTik RouterOS v7.x**, allowing automatic updates of A and AAAA DNS records on Cloudflare using the Cloudflare API. It supports multiple domains, IPv6, and efficient caching.

---

## ✨ Features

- ✅ **Supports multiple domains and record types** (A / AAAA) for simultaneous updates  
- 🔐 **Uses Cloudflare API Token for simpler and safer setup**  
- ➕ **Auto-creates DNS records – no manual intervention**  
- 🧠 **Caching mechanism to avoid frequent API requests, with optional forced update interval**  
- 📤 **Supports submitting IPv6 addresses from the local device or internal network** (e.g. `::1`, manual suffix appending、MAC Address)  
- 📡 **Uses Cloudflare DNS API to read domain records directly, instead of relying on DNS resolution**  

---

## 🔑 Get Your Cloudflare API Token

1. Go to the [Cloudflare API Tokens page](https://dash.cloudflare.com/profile/api-tokens)  
2. **Do not use the Global API Token**  
3. Click **"Create Token"**, and choose the **"Edit Zone DNS (Template)"** option  
4. After creation, copy your Token and paste it into the `CFtoken` variable in the script  

---

## 🔧 Configuration

Edit the following global variables at the top of the script:

```routeros
:local CFiface "pppoe-out1"           # Interface to get public IPv4
:local CFiface6 "pppoe-out1"          # Interface to get IPv6 prefix
:local CFzoneid "your-zone-id"        # Cloudflare Zone ID
:local CFtoken "your-api-token"       # Use token from 'Edit Zone DNS' template (do NOT use global API key)
# List of records to update (supports multiple):
:local DomainsToUpdate {
    "v4.domain.com|A";
    "v6.domain.com|AAAA";
    "ds.domain.com|A";
    "ds.domain.com|AAAA";
}
```