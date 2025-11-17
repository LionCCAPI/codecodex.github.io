---
layout: page
title: Deployment Guide
permalink: /en/deployment-guide.html
lang: en-US
comments: false
description: Lion CC Claude Code Complete Deployment Tutorial, 5-step quick deployment, server hosting + gateway IP system, bypass CC restrictions, direct access in China, no VPN needed
keywords: Claude Code Deployment,Claude Code Tutorial,Claude Deployment Guide,Server Hosting,Gateway IP System,China Claude Deployment,Claude API Configuration
---

<div style="text-align: center; margin: 40px 0;">
  <img src="/images/config/logo.svg" alt="Lion CC" style="height: 120px; width: auto;">
</div>

## 🚀 Lion CC Claude Code Deployment Tutorial

### 📋 Deployment Solution Overview

Lion CC's Claude Code solution, based on server hosting and gateway IP system, achieves the following core advantages:

- **✅ Bypass CC Restrictions** - No worries about official limitations
- **✅ No IP Environment Restrictions** - Direct access in China, no proxy needed
- **✅ Server Hosting** - Professional team management and maintenance
- **✅ Gateway IP System** - Intelligent routing, stable and reliable
- **✅ Customer Management System** - Real-time usage monitoring

---

## 🎯 Deployment Process

### Step 1: Contact Customer Service

Add group admin WeChat **LionCC.ai@Carpool Assistant**, inform customer service:
- How many seats you want (1-6 people)
- Choose plan (6-person ¥398/mo, 3-person ¥768/mo, 1-person ¥2200/mo)

### Step 2: Subscribe to Official Account

Customer service will assist with:
- Subscribe to Claude Max $200/month official account
- (Or) Subscribe to ChatGPT Pro official account
- Accounts managed uniformly by Lion CC

### Step 3: Install Claude Code Locally

According to your operating system, follow the [Installation Guide](/en/installation-guide.html) to complete local installation:

**macOS/Linux:**
```bash
# Install using Homebrew (Recommended)
brew install anthropics/claude/claude
```

**Windows:**
```powershell
# Install using PowerShell
irm https://raw.githubusercontent.com/Anthropics/claude-cli/main/install.ps1 | iex
```

### Step 4: Configure Authorization

Customer service will provide you with:
- **API Base URL** - Gateway address
- **API Key** - Your exclusive key

Configure environment variables in local terminal:

**macOS/Linux:**
```bash
export CLAUDE_API_BASE="https://use.codecodex.ai/api"
export CLAUDE_API_KEY="your-key"
```

**Windows:**
```powershell
$env:CLAUDE_API_BASE="https://use.codecodex.ai/api"
$env:CLAUDE_API_KEY="your-key"
```

**Permanent Configuration (Recommended):**

macOS/Linux users edit `~/.bashrc` or `~/.zshrc`:
```bash
echo 'export CLAUDE_API_BASE="https://use.codecodex.ai/api"' >> ~/.zshrc
echo 'export CLAUDE_API_KEY="your-key"' >> ~/.zshrc
source ~/.zshrc
```

### Step 5: Verify Deployment

Run test command:
```bash
claude --version
claude "Hello, Claude!"
```

If you get a normal response, deployment is successful!

---

## 📊 Customer Management System

After deployment, you can check usage through the customer management dashboard:

**Admin Portal:** [https://use.codecodex.ai/admin-next/api-stats](https://use.codecodex.ai/admin-next/api-stats)

**Features:**
- ✅ Real-time query call count
- ✅ Token input/output consumption statistics
- ✅ Computing power allocation view
- ✅ Usage history records

---

## 🔧 Technical Architecture

### Server Hosting Solution

```
Local Claude Code
    ↓
Lion CC Gateway System
    ↓
Official API Server
```

**Technical Advantages:**
1. **Intelligent Routing** - Automatically select optimal path
2. **Load Balancing** - Multi-server distributed deployment
3. **Computing Management** - Evenly distributed among carpool members
4. **Real-time Monitoring** - 24/7 system health check

### Gateway IP System

- Use dedicated IP pool to avoid official restrictions
- Dynamic IP switching ensures service stability
- Direct access in China, no VPN/proxy needed
- Prevent IP throttling, ensure full performance

---

## 💡 Usage Scenarios

### Scenario 1: Daily Development

```bash
# Run in project directory
cd /your/project
claude "Help me optimize this function's performance"
```

### Scenario 2: Code Review

```bash
claude "Review code quality of src/main.js"
```

### Scenario 3: Bug Fixing

```bash
claude "Analyze and fix this error: TypeError at line 42"
```

---

## ❓ FAQ

### Q: Do I need VPN?
**A:** No! Lion CC gateway system supports direct access in China, no VPN needed.

### Q: Can multiple devices use simultaneously?
**A:** Yes! Configure the same API Key. Computing power is evenly distributed among carpool members.

### Q: How to check my usage?
**A:** Visit admin portal [https://use.codecodex.ai/admin-next/api-stats](https://use.codecodex.ai/admin-next/api-stats) for real-time monitoring.

### Q: What if I forgot my API Key?
**A:** Contact group admin WeChat **LionCC.ai@Carpool Assistant**, customer service will resend.

### Q: Which operating systems are supported?
**A:** Supports Windows, macOS, Linux all platforms.

### Q: What's the difference between exclusive and shared?
**A:** Exclusive plan gets full computing power, shared plan distributes evenly by member count. See [Carpool Guide](/en/carpool.html) for details.

---

## 📞 Technical Support

**Encountering deployment issues?**

<div style="text-align: center; margin: 30px 0;">
  <img src="/images/qrcode.jpg" alt="Lion CC Carpool Group QR Code" style="max-width: 260px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
  <p style="margin-top: 15px;"><strong>Scan to join carpool group for consultation</strong></p>
</div>

- **Group Admin**: LionCC.ai@Carpool Assistant (WeChat)
- **Official Blog**: [LionCC.ai](https://LionCC.ai) - Solomon's Blog
- **Carpool Website**: [codecodex.ai](https://codecodex.ai)
- **Computing Platform**: [VibeCodingAPI.ai](https://VibeCodingAPI.ai)
- **Admin Portal**: [use.codecodex.ai/admin-next/api-stats](https://use.codecodex.ai/admin-next/api-stats)
- **Telegram**: [@codecodex_ai](https://t.me/codecodex_ai)

---

## 🎁 Special Offers

**Book Claude Code carpool and get free ChatGPT Codex trial!**

Lion CC also provides:
- 🚗 Claude Code Carpool Service (6-person ¥398/mo, 3-person ¥768/mo, 1-person ¥2200/mo)
- ⚡ VibeCodingAPI.ai Global AI Model API Computing Service
- 🤖 ChatGPT Codex Programming Service

For details, contact group admin WeChat: **LionCC.ai@Carpool Assistant**

---

> 💼 **Friendly Reminder**: This solution has been stably serving the market for nearly 3 months, supports flexible 1-6 person carpooling, agency cooperation welcome!
