---
layout: page
title: 部署教程
permalink: /deployment-guide.html
comments: false
description: Lion CC Claude Code 完整部署教程，5步快速部署，支持服务器托管+网关IP系统，绕过CC封锁，国内网络直连，无需VPN
keywords: Claude Code部署,Claude Code教程,Claude部署指南,服务器托管,网关IP系统,国内部署Claude,Claude API配置
---

<div style="text-align: center; margin: 40px 0;">
  <img src="/images/config/logo.svg" alt="Lion CC" style="height: 120px; width: auto;">
</div>

## 🚀 Lion CC Claude Code 部署教程

### 📋 部署方案概述

Lion CC 提供的 Claude Code 解决方案，基于服务器托管和网关 IP 系统，实现以下核心优势：

- **✅ 绕过 CC 封锁** - 无需担心官方限制
- **✅ 无 IP 环境限制** - 国内网络直接使用，无需代理
- **✅ 服务器托管** - 专业团队管理维护
- **✅ 网关 IP 系统** - 智能路由，稳定可靠
- **✅ 客户管理系统** - 实时查询使用情况

---

## 🎯 部署流程

### 第一步：联系客服预约

添加群管理拼车助手微信 **LionCC.ai@拼车助手**，告知客服：
- 你要预定几人车（1-6人）
- 选择套餐（6人车 ¥398/月、3人车 ¥768/月、1人车 ¥2200/月）

### 第二步：订阅官方账号

客服会协助完成：
- 订阅 Claude Max $200/月 官方账号
- （或）订阅 ChatGPT Pro 官方账号
- 账号由 Lion CC 统一管理

### 第三步：本地安装 Claude Code

根据你的操作系统，按照 [安装指南](/installation-guide.html) 完成本地安装：

**macOS/Linux:**
```bash
# 使用 Homebrew 安装（推荐）
brew install anthropics/claude/claude
```

**Windows:**
```powershell
# 使用 PowerShell 安装
irm https://raw.githubusercontent.com/Anthropics/claude-cli/main/install.ps1 | iex
```

### 第四步：配置授权信息

客服会提供给你：
- **API Base URL** - 网关地址
- **API Key** - 你的专属密钥

在本地终端配置环境变量：

**macOS/Linux:**
```bash
export CLAUDE_API_BASE="https://use.codecodex.ai/api"
export CLAUDE_API_KEY="你的密钥"
```

**Windows:**
```powershell
$env:CLAUDE_API_BASE="https://use.codecodex.ai/api"
$env:CLAUDE_API_KEY="你的密钥"
```

**永久配置（推荐）：**

macOS/Linux 用户编辑 `~/.bashrc` 或 `~/.zshrc`：
```bash
echo 'export CLAUDE_API_BASE="https://use.codecodex.ai/api"' >> ~/.zshrc
echo 'export CLAUDE_API_KEY="你的密钥"' >> ~/.zshrc
source ~/.zshrc
```

### 第五步：验证部署

运行测试命令：
```bash
claude --version
claude "Hello, Claude!"
```

如果返回正常响应，说明部署成功！

---

## 📊 客户管理系统

部署完成后，你可以通过客户管理系统仪表盘查看使用情况：

**管理后台地址：** [https://use.codecodex.ai/admin-next/api-stats](https://use.codecodex.ai/admin-next/api-stats)

**功能特性：**
- ✅ 实时查询调用次数
- ✅ Token 输入输出消耗统计
- ✅ 算力分配情况查看
- ✅ 使用历史记录

---

## 🔧 技术架构说明

### 服务器托管方案

```
用户本地 Claude Code
    ↓
Lion CC 网关系统
    ↓
官方 API 服务器
```

**技术优势：**
1. **智能路由** - 自动选择最优路径
2. **负载均衡** - 多服务器分布式部署
3. **算力管理** - 按车队成员平均分配
4. **实时监控** - 24/7 系统健康检查

### 网关 IP 系统

- 使用专用 IP 池，避免官方封锁
- 动态 IP 切换，保证服务稳定性
- 国内直连，无需 VPN/代理
- 防 IP 降智，保证满血性能

---

## 💡 使用场景

### 场景一：日常开发

```bash
# 在项目目录中运行
cd /your/project
claude "帮我优化这个函数的性能"
```

### 场景二：代码审查

```bash
claude "审查 src/main.js 的代码质量"
```

### 场景三：Bug 修复

```bash
claude "分析并修复这个错误: TypeError at line 42"
```

---

## ❓ 常见问题

### Q: 需要科学上网吗？
**A:** 不需要！Lion CC 网关系统支持国内网络直连，无需 VPN。

### Q: 多个设备可以同时使用吗？
**A:** 可以！配置相同的 API Key 即可。算力会在车队成员间平均分配。

### Q: 如何查看我的使用量？
**A:** 访问管理后台 [https://use.codecodex.ai/admin-next/api-stats](https://use.codecodex.ai/admin-next/api-stats) 实时查看。

### Q: API Key 忘记了怎么办？
**A:** 联系群管理拼车助手微信 **LionCC.ai@拼车助手**，客服会重新发送。

### Q: 支持哪些操作系统？
**A:** 支持 Windows、macOS、Linux 全平台。

### Q: 包车和拼车有什么区别？
**A:** 包车独享全部算力，拼车按人数平均分配。详见 [拼车指南](/carpool.html)。

---

## 📞 技术支持

**遇到部署问题？**

<div style="text-align: center; margin: 30px 0;">
  <img src="/images/qrcode.jpg" alt="Lion CC 拼车群二维码" style="max-width: 260px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
  <p style="margin-top: 15px;"><strong>扫码加入拼车群咨询</strong></p>
</div>

- **群管理拼车助手**: LionCC.ai@拼车助手（微信）
- **官方博客**: [LionCC.ai](https://LionCC.ai) - 所罗门博客
- **拼车官网**: [codecodex.ai](https://codecodex.ai)
- **算力平台**: [VibeCodingAPI.ai](https://VibeCodingAPI.ai)
- **管理后台**: [use.codecodex.ai/admin-next/api-stats](https://use.codecodex.ai/admin-next/api-stats)
- **Telegram**: [@codecodex_ai](https://t.me/codecodex_ai)

---

## 🎁 特别优惠

**预约上车 Claude Code 送 ChatGPT Codex 免费体验！**

Lion CC 同时提供：
- 🚗 Claude Code 拼车服务（6人车 ¥398/月、3人车 ¥768/月、1人车 ¥2200/月）
- ⚡ VibeCodingAPI.ai 全球 AI 大模型 API 算力服务
- 🤖 ChatGPT Codex 编程服务

详情咨询群管理拼车助手微信：**LionCC.ai@拼车助手**

---

> 💼 **温馨提示**：此方案已稳定服务市场近 3 个月，支持 1-6 人灵活拼车使用，欢迎代理合作！