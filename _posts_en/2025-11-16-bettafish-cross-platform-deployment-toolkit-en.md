---
layout: post
title: "🆕 BettaFish One-Click Deployment Toolkit v2.0 - User Guide"
date: 2025-11-16 08:00:00 +0800
summary: "BettaFish one-click deployment toolkit. Double-click to complete deployment. Supports Windows, macOS, and Linux. 5-10 minutes setup, no technical background required."
categories: Tech
tags: [BettaFish, One-Click Deployment, Cross-Platform Tools, Automated Deployment]
author: LION CC
lang: en
lang_ref: bettafish-deployment-v2
---

> **Tool Author**: LION CC ([codecodex.ai](https://codecodex.ai))
>
> **Tool Version**: v2.1.0
> **Supported Platforms**: Windows / macOS / Linux
> **Deployment Time**: 5-10 minutes

---

## 📑 Table of Contents

- [✨ v2.0 New Features](#-v20-new-features)
- [📦 Get the Toolkit](#-get-the-toolkit)
- [🔑 Prepare API Keys](#-prepare-api-keys)
- [🪟 Windows Usage](#-windows-usage)
- [🍎 macOS Usage](#-macos-usage)
- [🐧 Linux Usage](#-linux-usage)
- [📋 Toolkit Contents](#-toolkit-contents)
- [🎯 After Successful Deployment](#-after-successful-deployment)
- [❓ FAQ](#-faq)
- [🔗 Related Resources](#-related-resources)

---

## ✨ v2.0 New Features

- ✅ **One-Click Deployment** - Double-click to run, automatic configuration
- ✅ **Smart Repair** - Windows fix-all tool auto-diagnoses 9 categories of issues
- ✅ **Cross-Platform Menu** - Unified interactive menu experience
- ✅ **Zero Technical Barrier** - No manual configuration file editing required

---

## 📦 Get the Toolkit

### GitHub Download

```bash
git clone https://github.com/Jascenn/deployment-scripts-hub.git
cd deployment-scripts-hub/bettafish
```

### Get via Community

> **🎁 Benefits**: Scan the QR code below to join codecodex.ai community and get toolkit + technical support + VibeCoding API discount

<div style="text-align: center; margin: 20px 0;">
  <img src="/images/wechat-assistant-qrcode.jpg" alt="CodeCodex Technical Assistant WeChat QR Code" style="width: 100%; max-width: 300px; border-radius: 10px; box-shadow: 0 4px 6px rgba(0,0,0,0.1);">
  <p style="color: #666; font-size: 14px; margin-top: 10px;">Scan to add technical assistant, note: <strong>BettaFish Toolkit</strong></p>
</div>

---

## 🔑 Prepare API Keys

You need to prepare AI API keys before deployment:

**Recommended: VibeCoding API**
- Website: [https://vibecodingapi.ai](https://vibecodingapi.ai)
- Format: `sk-xxxxxxxxxxxxx`
- 🎁 Get discount by registering through community

**Other Options**: OpenAI, Claude, Gemini and other compatible APIs

**Optional APIs** (Enhanced search features):
- Tavily API: [https://tavily.com](https://tavily.com)
- Bocha API: [https://bocha.ai](https://bocha.ai)

---

## 🪟 Windows Usage

### Quick Start

```
1. Navigate to deployment-scripts-hub/bettafish/Windows folder
2. Double-click menu.bat
3. Enter 1 to select deployment
4. Enter API key as prompted
5. Wait for completion (about 5-10 minutes)
```

### Menu Options

```
1) Deploy/Update BettaFish   - Choose this for first use
2) System Diagnosis          - Check system status
3) Smart Repair (fix-all)    - Use when issues occur
4) Start Services
5) Stop Services
6) View Logs
```

### Shortcuts

- **Quick Deploy**: Double-click `deploy.bat`
- **Smart Repair**: Double-click `fix-all.bat` (auto-fix 9 common issues)

---

## 🍎 macOS Usage

### Quick Start

```bash
# 1. Navigate to directory
cd deployment-scripts-hub/bettafish/Linux_macOS

# 2. Start menu
./menu.sh

# 3. Select 1 to deploy
# 4. Enter API key as prompted
```

### Direct Deployment

```bash
./docker-deploy.sh
```

---

## 🐧 Linux Usage

### Quick Start

```bash
# 1. Navigate to directory
cd deployment-scripts-hub/bettafish/Linux_macOS

# 2. Start menu
./menu.sh

# Or deploy directly
./docker-deploy.sh
```

---

## 📋 Toolkit Contents

### Windows Tools
- `menu.bat` - Interactive menu
- `deploy.bat` - Quick deployment
- `fix-all.bat` - Smart repair (9 diagnostic categories)
- `docker-deploy.bat` - Complete deployment workflow

### macOS/Linux Tools
- `menu.sh` - Interactive menu
- `docker-deploy.sh` - One-click deployment
- `diagnose.sh` - System diagnostics
- `docker-cleanup.sh` - Docker cleanup

---

## 🎯 After Successful Deployment

1. Open browser and visit: `http://localhost:5001`
2. First-time use requires AI model configuration (API auto-filled)
3. Start chatting and experience AI assistant features

**Tip**: Supports switching between multiple AI models in the interface

---

## ❓ FAQ

### Q1: What are the prerequisites?

**A**:
- Docker Desktop (Windows/macOS) or Docker Engine (Linux)
- API key (VibeCoding or others)

### Q2: Windows scripts showing garbled text?

**A**: Double-click `fix-all.bat` to auto-fix

### Q3: Docker not started?

**A**:
- Windows/macOS: Start Docker Desktop or run `fix-all.bat`
- Linux: `sudo systemctl start docker`

### Q4: How to access after deployment?

**A**: Open `http://localhost:5001` in browser

### Q5: How to update?

**A**: Re-run deployment script (configuration will be preserved)

### Q6: What's the difference from [LionCC API Configuration Guide](/2025-11-07/bettafish-lioncc-api-deployment-guide.html)?

**A**:
- **Configuration Guide (11-07)**: Manual configuration, for technical users
- **Toolkit (this article)**: Automated deployment, for all users

---

## 🔗 Related Resources

- **BettaFish Project**: [https://github.com/666ghj/BettaFish](https://github.com/666ghj/BettaFish)
- **Deployment Toolkit**: [https://github.com/Jascenn/deployment-scripts-hub](https://github.com/Jascenn/deployment-scripts-hub)
- **VibeCoding API**: [https://vibecodingapi.ai](https://vibecodingapi.ai)
- **Detailed Configuration**: [Deployment Toolkit Documentation](https://github.com/Jascenn/deployment-scripts-hub/tree/main/bettafish)

---

## 🎉 Get Started

**Windows**: Double-click `menu.bat`
**macOS/Linux**: Run `./menu.sh`

Having issues? Scan the QR code above to join technical community for support

---

**Update Log**:
- 2025-11-16: v2.1.0 Release
  - Support Windows/macOS/Linux
  - Added fix-all smart repair tool
  - Added interactive menu system
  - Fully automated deployment process
