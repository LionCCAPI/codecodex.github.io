---
layout: post
title: "BettaFish Micro-Sentiment System - LionCC API Complete Deployment Guide"
date: 2025-11-07 08:00:00 +0800
summary: "Complete deployment tutorial for BettaFish Micro-Sentiment System, including LionCC API configuration, Docker deployment, model selection recommendations, and troubleshooting solutions. Supports Claude, GPT-4, Gemini, and other LLM models."
categories: Tech
tags: [BettaFish, LionCC, API Deployment, Docker, LLM, Claude, GPT-4, Gemini]
author: Lion CC
description: Complete BettaFish deployment guide with LionCC API configuration, Docker setup, model recommendations, and troubleshooting
keywords: BettaFish deployment,LionCC API,Claude API,Docker deployment,LLM configuration,Gemini 2.5 Pro
lang: en
lang_ref: bettafish-lioncc-deployment
---

> **Author**: Lion CC ([lioncc.ai](https://lioncc.ai)) WeChat: HSQBJ088888888
>
> **Last Updated**: 2025-11-07
> **System Version**: v1.0.1
> **Deployment Method**: Docker
> **Update Notes**: Added Gemini 2.5 Pro model configuration, updated recommended model list

---

## 💡 About LionCC API Service

This guide is tested and verified based on **LionCC API** (VibeCodingAPI.ai) platform, fully compatible with all LLM models in BettaFish Micro-Sentiment System (Claude, GPT-4, Gemini, etc.).

> **🎁 Special Offer**: Register LionCC API through <a href="#" onclick="showQRCode(); return false;" style="color: #0066cc; text-decoration: underline; cursor: pointer;">codecodex.ai community</a> and get $20 testing credits (limited to first 1000 users)

<div id="qrcode-modal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 9999; justify-content: center; align-items: center;" onclick="hideQRCode()">
  <div style="background: white; padding: 30px; border-radius: 15px; text-align: center; max-width: 400px;" onclick="event.stopPropagation()">
    <h3 style="margin-top: 0; color: #333;">Add Business Assistant on WeChat</h3>
    <img src="/images/wechat-assistant-qrcode.jpg" alt="Lion CC Business Assistant WeChat QR Code" style="width: 100%; max-width: 300px; border-radius: 10px; margin: 20px 0;">
    <p style="color: #666; font-size: 14px;">Scan to add business assistant, note: <strong>BettaFish</strong></p>
    <p style="color: #999; font-size: 12px; margin-top: 5px;">Get $20 API testing credits + technical support</p>
    <button onclick="hideQRCode()" style="background: #0066cc; color: white; border: none; padding: 10px 30px; border-radius: 5px; cursor: pointer; font-size: 16px; margin-top: 10px;">Close</button>
  </div>
</div>

<script>
function showQRCode() {
  document.getElementById('qrcode-modal').style.display = 'flex';
  document.body.style.overflow = 'hidden';
}

function hideQRCode() {
  document.getElementById('qrcode-modal').style.display = 'none';
  document.body.style.overflow = 'auto';
}

// Close with ESC key
document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape') {
    hideQRCode();
  }
});
</script>

---

## 📋 Table of Contents

1. [System Architecture Overview](#️-system-architecture-overview)
2. [Third-Party API Configuration](#-third-party-api-configuration)
3. [Docker Deployment Notes](#-docker-deployment-notes)
4. [Common Issues & Solutions](#-common-issues--solutions)
5. [🚀 Quick Start Guide ⭐️](#-quick-start-guide-️-core-content) **← Recommended Starting Point**

---

## 🏗️ System Architecture Overview

### Core Components

```
BettaFish Micro-Sentiment System
├── InsightEngine     - Private database mining (Claude 3.5 Sonnet)
├── MediaEngine       - Multimodal content analysis (Gemini Pro)
├── QueryEngine       - Web search reasoning (DeepSeek Chat)
├── ForumEngine       - Agent collaboration forum
└── ReportEngine      - Intelligent report generation (Gemini 2.5 Pro)
```

### Tech Stack

- **Backend**: Python 3.11 + Flask + LangGraph
- **Database**: MySQL 8.0
- **Containers**: Docker + Docker Network
- **Frontend**: Streamlit (single engine) + HTML/JavaScript (main app)

---

## 🔑 Third-Party API Configuration

### 1. LLM API Configuration (LionCC API)

#### 📍 API Provider
- **Service Name**: LionCC API
- **Platform**: VibeCodingAPI.ai
- **Website**: [https://vibecodingapi.ai](https://vibecodingapi.ai)
- **Features**: OpenAI-compatible interface, optimized for BettaFish Micro-Sentiment System, supports all mainstream LLM models

#### 🔐 API Key Configuration

```bash
# All engines use the same API Key
INSIGHT_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
MEDIA_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
QUERY_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
REPORT_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
FORUM_HOST_API_KEY=sk-YOUR_API_KEY_HERE
MINDSPIDER_API_KEY=sk-YOUR_API_KEY_HERE
KEYWORD_OPTIMIZER_API_KEY=sk-YOUR_API_KEY_HERE
```

#### 🎯 Recommended Model Configuration

| Engine | Recommended Model | Reason | Alternative |
|--------|------------------|--------|-------------|
| **InsightEngine** | `claude-3-5-sonnet-20241022` | Strong data analysis | `claude-3-opus-20240229` |
| **MediaEngine** | `gemini-pro` | Excellent multimodal understanding | `gpt-4o` |
| **QueryEngine** | `deepseek-chat` | Strong reasoning, cost-effective | `gpt-4-turbo` |
| **ReportEngine** | `gemini-2.5-pro` | Latest Gemini, outstanding performance | `gpt-4o`, `gpt-4` |
| **ForumEngine** | `claude-3-5-sonnet-20241022` | Strong collaboration | `gpt-4` |
| **MindSpider** | `deepseek-chat` | Crawler analysis, low cost | `gpt-3.5-turbo` |
| **KeywordOptimizer** | `gpt-3.5-turbo` | Lightweight tasks, fast | `deepseek-chat` |

#### ⚠️ Tested Model List

**✅ Available Models** (tested and verified through LionCC API):
```
- gpt-4o              ✅ (Latest GPT-4 Optimized)
- gpt-4               ✅
- gpt-4-turbo         ✅
- gpt-3.5-turbo       ✅
- claude-3-5-sonnet-20241022  ✅ (Recommended)
- claude-3-opus-20240229      ✅
- gemini-pro          ✅
- gemini-2.5-pro      ✅ (Latest version, outstanding performance, recommended for reports)
- deepseek-chat       ✅ (Recommended, cost-effective)
- deepseek-reasoner   ⚠️ (Unstable, fails under high load, not recommended)
```

**❌ Unavailable Models**:
```
- kimi-k2-0711-preview    ❌ (HTTP 500)
- qwen-plus               ❌ (HTTP 503)
- qwen-turbo              ❌ (HTTP 503)
- gemini-2.0-flash-exp    ❌ (HTTP 500)
```

#### 🆕 Gemini 2.5 Pro New Features

**Recommended Scenario**: ReportEngine (report generation)

**Advantages**:
- ✅ Latest generation Gemini model with significant performance improvements
- ✅ Long context support (1M+ tokens), ideal for large-scale report generation
- ✅ Optimized for multiple languages, excellent Chinese and English generation quality
- ✅ Strong structured output capabilities, suitable for HTML/Markdown format reports
- ✅ Better cost-performance ratio than GPT-4o

**Notes**:
- ⚠️ Slightly higher token consumption compared to Gemini Pro
- ⚠️ Some API providers may not yet support this model
- ⚠️ Test availability before large-scale use

**Test Command**:
```bash
# Test Gemini 2.5 Pro availability
curl -X POST "https://vibecodingapi.ai/v1/chat/completions" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemini-2.5-pro",
    "messages": [{"role": "user", "content": "test"}],
    "max_tokens": 100
  }'
```

---

#### 💡 Model Switching Recommendations

If a specific model is unavailable, switch according to these priorities:

**Text Analysis Tasks**:
```
claude-3-5-sonnet > gpt-4o > gpt-4-turbo > deepseek-chat
```

**Reasoning Tasks**:
```
deepseek-chat > gpt-4-turbo > claude-3-opus
```

**Report Generation**:
```
gemini-2.5-pro > gpt-4o > gpt-4 > claude-3-5-sonnet
```

**Cost Optimization**:
```
deepseek-chat > gpt-3.5-turbo > gemini-pro
```

---

### 2. Bocha API Configuration (Multimodal Search)

#### 📍 API Information
- **Name**: Bocha AI
- **Website**: [https://api.bochaai.com](https://api.bochaai.com) or [https://open.bochaai.com](https://open.bochaai.com)
- **Function**: Multimodal web search (images, videos, web pages)
- **Used by**: MediaEngine

#### 🔐 Configuration Points

```bash
# Bocha API Configuration
BOCHA_BASE_URL=https://api.bochaai.com
BOCHA_WEB_SEARCH_API_KEY=sk-YOUR_BOCHA_KEY_HERE
```

#### ⚠️ Key Notes

**1. API Endpoint Selection**

Bocha offers two API packages:

| Package Type | API Endpoint | Purpose |
|-------------|--------------|---------|
| **Web Search** | `/v1/web-search` | Web search (recommended) |
| **AI Search** | `/v1/ai-search` | AI-enhanced search (requires premium package) |

**2. Code Configuration**

By default, BettaFish uses `/v1/ai-search`. If your package is Web Search, modify:

```bash
# Edit file: MediaEngine/tools/search.py
# Line 94
BASE_URL = "https://api.bochaai.com/v1/web-search"  # Change to web-search
```

**3. Quota Check**

Login to Bocha dashboard to check:
- Account balance
- Package type (Web Search / AI Search)
- Remaining calls

**4. Common Errors**

```json
{"message": "You do not have enough money or package quota", "code": "403"}
```
**Solutions**:
- Recharge account
- Confirm using correct API endpoint
- Check if API Key is correct

---

### 3. Tavily API Configuration (Web Search)

#### 📍 API Information
- **Name**: Tavily
- **Website**: [https://www.tavily.com](https://www.tavily.com)
- **Function**: Text web search
- **Used by**: InsightEngine, QueryEngine

#### 🔐 Configuration

```bash
TAVILY_API_KEY=tvly-YOUR_KEY_HERE
```

#### ✅ Features

- **Free Quota**: Usually includes trial credits
- **Stability**: High
- **Speed**: Fast
- **Languages**: Supports Chinese and English

#### 💡 Test Command

```bash
curl -X POST 'https://api.tavily.com/search' \
  -H 'Content-Type: application/json' \
  -d '{
    "api_key": "YOUR_KEY",
    "query": "test",
    "max_results": 1
  }'
```

---

## 🐳 Docker Deployment Notes

### 1. Docker Image Building

#### 📋 Basic Configuration

```dockerfile
FROM python:3.11-slim

# Key dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    ffmpeg \
    libgl1 \
    chromium \
    && apt-get clean

# Python package manager (use uv for acceleration)
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
```

#### ⚠️ Notes

**1. Python Version Lock**
- ✅ **Use Python 3.11** (recommended)
- ❌ **Do not use Python 3.14** (compatibility issues)
- ⚠️ Python 3.12 untested

**2. Dependency Installation Issues**

Some packages need to be installed after container startup:

```bash
# cryptography (MySQL authentication)
docker exec bettafish pip install cryptography --quiet

# If encountering permission issues
docker exec -u root bettafish pip install cryptography
```

**Permanent solution**: Add `cryptography` to `requirements.txt` and rebuild image.

---

### 2. Container Configuration

#### 📍 Port Mapping

```bash
docker run -d \
  --name bettafish \
  -p 15888:5000   # Flask main app
  -p 8501:8501    # InsightEngine (Streamlit)
  -p 8502:8502    # MediaEngine (Streamlit)
  -p 8503:8503    # QueryEngine (Streamlit)
  bettafish:latest
```

#### ⚠️ Port Conflict Issues

**Issue**: Default port 5000 may be occupied by proxy (e.g., Clash)

**Symptoms**:
```
HTTP 403 Forbidden
localhost:5000 cannot be accessed
```

**Solutions**:
```bash
# Method 1: Use non-standard port
-p 15888:5000

# Method 2: Set no_proxy
export no_proxy="localhost,127.0.0.1"
open -a "Google Chrome" "http://localhost:15888"
```

---

### 3. Network Configuration

#### 📍 Docker Network

BettaFish uses a separate Docker network to connect containers:

```bash
# Create network
docker network create bettafish-network

# MySQL container
docker run -d \
  --name bettafish-mysql \
  --network bettafish-network \
  -p 3307:3306 \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=bettafish_db \
  mysql:8.0

# Application container
docker run -d \
  --name bettafish \
  --network bettafish-network \
  -p 15888:5000 \
  bettafish:latest
```

#### ⚠️ Database Connection Configuration

**.env file configuration**:
```bash
# ❌ Wrong (localhost doesn't work inside container)
DB_HOST=localhost

# ✅ Correct (use container name)
DB_HOST=bettafish-mysql
DB_PORT=3306
```

---

### 4. Environment Variable Management

#### 📋 .env File Sync

**Issue**: Docker image contains old .env file

**Symptoms**:
- After updating host .env file, container configuration doesn't take effect
- `docker restart` doesn't reload .env

**Solutions**:

```bash
# Method 1: Manual copy (recommended)
docker cp .env bettafish:/app/.env
docker restart bettafish

# Method 2: Use --env-file (when creating container)
docker run -d --env-file .env bettafish:latest

# Method 3: Rebuild image
docker build -t bettafish:latest .
```

#### ⚠️ Configuration Update Workflow

After modifying .env or code:

```bash
# 1. Stop and remove old container
docker stop bettafish && docker rm bettafish

# 2. Rebuild image (if code changed)
docker build -t bettafish:latest .

# 3. Start new container
docker run -d \
  --name bettafish \
  --network bettafish-network \
  -p 15888:5000 \
  -p 8501-8503:8501-8503 \
  --env-file .env \
  bettafish:latest

# 4. Install additional dependencies
docker exec bettafish pip install cryptography --quiet

# 5. Restart to apply
docker restart bettafish
```

---

### 5. Data Persistence

#### 📍 Important Directories

```bash
/app/logs/              # Runtime logs
/app/final_reports/     # Generated reports
/app/forum.log          # Forum discussion logs
/app/templates/         # Custom templates
```

#### 💡 Mount Volumes (Optional)

```bash
docker run -d \
  -v /host/path/logs:/app/logs \
  -v /host/path/reports:/app/final_reports \
  bettafish:latest
```

---

## 🔧 Common Issues & Solutions

### 1. ModuleNotFoundError: No module named 'config'

**Cause**: Missing config.py file in container

**Solution**:

```bash
# Create config.py
docker exec bettafish bash -c 'cat > /app/config.py << EOF
import os
from dotenv import load_dotenv

load_dotenv()

# Database configuration
DB_HOST = os.getenv("DB_HOST", "localhost")
DB_PORT = int(os.getenv("DB_PORT", "3306"))
DB_USER = os.getenv("DB_USER", "root")
DB_PASSWORD = os.getenv("DB_PASSWORD", "")
DB_NAME = os.getenv("DB_NAME", "bettafish_db")

# LLM configuration (add all required config items)
# ...
EOF'

# Restart container
docker restart bettafish
```

**Permanent solution**: Create config.py in project root directory, rebuild image.

---

### 2. MySQL Authentication Failure

**Error Message**:
```
Authentication plugin 'caching_sha2_password' cannot be loaded
```

**Cause**: PyMySQL requires cryptography package for MySQL 8.0

**Solution**:

```bash
docker exec bettafish pip install cryptography --quiet
docker restart bettafish
```

---

### 3. Bocha API 403 Error

**Error Message**:
```json
{"message": "You do not have enough money or package quota", "code": "403"}
```

**Troubleshooting Steps**:

1. **Check API Key**:
   ```bash
   docker exec bettafish grep "BOCHA" /app/.env
   ```

2. **Confirm Account Balance**: Login to Bocha dashboard

3. **Confirm API Endpoint**: Check if using correct endpoint (web-search vs ai-search)

4. **Test API**:
   ```bash
   curl -X POST "https://api.bochaai.com/v1/web-search" \
     -H "Authorization: Bearer YOUR_KEY" \
     -H "Content-Type: application/json" \
     -d '{"query":"test"}'
   ```

---

### 4. LLM API High Load (500 Error)

**Error Message**:
```json
{"error": {"message": "Current model load is high, please retry later or switch to another model"}}
```

**Solutions**:

**Method 1: Wait and Retry** (system will auto-retry)

**Method 2: Switch to Backup Model**

```bash
# Edit .env file
# Replace unstable model with backup
QUERY_ENGINE_MODEL_NAME=deepseek-chat  # Change from deepseek-reasoner to deepseek-chat

# Sync to container
docker cp .env bettafish:/app/.env
docker restart bettafish
```

---

### 5. Report Format Issues

**Issue**: Generated reports are plain text, no visualization

**Cause**:
1. System visualization is built-in, not template-dependent
2. Templates only define report outline structure

**Explanation**:
- ✅ System has 6 built-in templates
- ✅ ReportEngine auto-selects appropriate template
- ✅ Visualization effects (charts, data cards) are code-generated
- ⚠️ "Upload template" feature is for customizing report structure, not adding visualization

**Confirm System Normal**:
- Check logs for `[HTMLGenerationNode] Starting HTML report generation...`
- Check `/app/final_reports/` directory for report files

---

## 🚀 Quick Start Guide ⭐️ Core Content

> **💡 Important**: This is the fastest way to deploy BettaFish, bookmark this script!
>
> **Use Case**: Initial deployment completed, need to quickly start system

### Complete Startup Script

> **📦 One-Click Startup Script - Copy and Use**
>
> Save the following as `start-bettafish.sh`, give execute permission and run directly to start the entire system.

```bash
#!/bin/bash

echo "======================================"
echo "BettaFish Micro-Sentiment System - Quick Start"
echo "======================================"

# 1. Start MySQL
echo "1️⃣  Starting MySQL container..."
docker start bettafish-mysql
sleep 3

# 2. Start application
echo "2️⃣  Starting BettaFish container..."
docker start bettafish
sleep 10

# 3. Sync config file
echo "3️⃣  Syncing config file..."
docker cp .env bettafish:/app/.env 2>/dev/null || echo "   .env synced"

# 4. Install dependencies
echo "4️⃣  Installing required dependencies..."
docker exec bettafish pip install cryptography --quiet 2>/dev/null

# 5. Restart application
echo "5️⃣  Restarting application to load config..."
docker restart bettafish >/dev/null 2>&1
sleep 30

# 6. Check status
echo "6️⃣  Checking service status..."
docker ps --filter "name=bettafish" --format "   ✓ {% raw %}{{.Names}}: {{.Status}}{% endraw %}"

echo ""
echo "======================================"
echo "✅ Startup Complete!"
echo "======================================"
echo ""
echo "🌐 Access URLs:"
echo "   Main App: http://localhost:15888"
echo "   InsightEngine: http://localhost:8501"
echo "   MediaEngine: http://localhost:8502"
echo "   QueryEngine: http://localhost:8503"
echo ""
echo "💡 Opening browser:"
export no_proxy="localhost,127.0.0.1"
export NO_PROXY="localhost,127.0.0.1"
open -a "Google Chrome" "http://localhost:15888"
```

**Usage**:

```bash
chmod +x start-bettafish.sh
./start-bettafish.sh
```

---

## 📚 Complete Configuration File Example

### .env File Template

```bash
# ====================== Database Configuration ======================
DB_HOST=bettafish-mysql
DB_PORT=3306
DB_USER=bettafish_user
DB_PASSWORD=BettaFish2024!
DB_NAME=bettafish_db
DB_CHARSET=utf8mb4
DB_DIALECT=mysql

# ======================= LLM Configuration =======================
# Insight Agent - Database Mining
INSIGHT_ENGINE_API_KEY=sk-YOUR_API_KEY
INSIGHT_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
INSIGHT_ENGINE_MODEL_NAME=claude-3-5-sonnet-20241022

# Media Agent - Multimodal Analysis
MEDIA_ENGINE_API_KEY=sk-YOUR_API_KEY
MEDIA_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
MEDIA_ENGINE_MODEL_NAME=gemini-pro

# Query Agent - Web Search
QUERY_ENGINE_API_KEY=sk-YOUR_API_KEY
QUERY_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
QUERY_ENGINE_MODEL_NAME=deepseek-chat

# Report Agent - Report Generation
REPORT_ENGINE_API_KEY=sk-YOUR_API_KEY
REPORT_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
REPORT_ENGINE_MODEL_NAME=gemini-2.5-pro

# Forum Host - Forum Hosting
FORUM_HOST_API_KEY=sk-YOUR_API_KEY
FORUM_HOST_BASE_URL=https://vibecodingapi.ai/v1
FORUM_HOST_MODEL_NAME=claude-3-5-sonnet-20241022

# MindSpider - Crawler Analysis
MINDSPIDER_API_KEY=sk-YOUR_API_KEY
MINDSPIDER_BASE_URL=https://vibecodingapi.ai/v1
MINDSPIDER_MODEL_NAME=deepseek-chat

# Keyword Optimizer - Keyword Optimization
KEYWORD_OPTIMIZER_API_KEY=sk-YOUR_API_KEY
KEYWORD_OPTIMIZER_BASE_URL=https://vibecodingapi.ai/v1
KEYWORD_OPTIMIZER_MODEL_NAME=gpt-3.5-turbo

# ================== Web Tools Configuration ====================
# Tavily API (Web Search)
TAVILY_API_KEY=tvly-YOUR_KEY

# Bocha API (Multimodal Search)
BOCHA_BASE_URL=https://api.bochaai.com
BOCHA_WEB_SEARCH_API_KEY=sk-YOUR_BOCHA_KEY
```

---

## 🎯 Deployment Checklist

### Pre-Deployment Checks

- [ ] Python 3.11 environment
- [ ] Docker and Docker Compose installed
- [ ] At least 4GB available memory
- [ ] Ports 15888, 8501-8503 not occupied

### API Configuration Checks

- [ ] VibeCodingAPI API Key obtained
- [ ] Tavily API Key obtained
- [ ] Bocha API Key obtained (optional)
- [ ] All models tested and available

### Container Configuration Checks

- [ ] Docker network created
- [ ] MySQL container running normally
- [ ] BettaFish container running normally
- [ ] Container network connectivity

### Function Testing Checks

- [ ] Main app (15888) accessible
- [ ] 3 Streamlit Engines (8501-8503) accessible
- [ ] Database connection successful
- [ ] Test query generates report
- [ ] 5 Engine status indicators show green

---

## 📞 Get Help

### Official Resources

- **GitHub**: [https://github.com/666ghj/BettaFish](https://github.com/666ghj/BettaFish)
- **Documentation**: README.md
- **Discussion**: [https://linux.do/t/topic/1009280](https://linux.do/t/topic/1009280)
- **Sample Report**: `final_reports/final_report__20250827_131630.html`

### View Logs

```bash
# Real-time logs
docker logs -f bettafish

# Last 100 lines
docker logs bettafish --tail 100

# Error logs
docker logs bettafish 2>&1 | grep -i error
```

---

## ✅ Summary

**Signs of Successful BettaFish Deployment**:

1. ✅ All containers running
2. ✅ Main app accessible (http://localhost:15888)
3. ✅ All 5 Engine indicators green
4. ✅ Test query successfully generates report
5. ✅ Report includes visualization content

**Key Configuration Points**:

- 🔑 **API Keys Configured Correctly** (VibeCodingAPI, Tavily, Bocha)
- 🎯 **Models Selected Appropriately** (choose best models based on tasks)
- 🐳 **Docker Configuration Complete** (network, ports, environment variables)
- 📁 **Files Synced Timely** (.env, config.py)

---

## 📝 Changelog

### v1.0.1 (2025-11-07)

**New Content**:
- ✨ Added Gemini 2.5 Pro model configuration guide
- ✨ Added Gemini 2.5 Pro feature introduction and testing methods
- 📝 Updated ReportEngine recommended model to `gemini-2.5-pro`
- 📝 Updated model priority recommendation list
- 📝 Updated tested model list
- 📝 Updated .env configuration file template

**Optimized Content**:
- 🔧 Marked DeepSeek Reasoner as unstable, not recommended
- 🔧 Optimized report generation model selection recommendations

### v1.0.0 (2025-11-06)

**Initial Version**:
- 📚 Complete BettaFish system deployment guide
- 🔑 Third-party API configuration detailed explanation (VibeCodingAPI, Tavily, Bocha)
- 🐳 Docker deployment notes
- 🔧 Common issues and solutions
- 🚀 Quick start script

---

**Enjoy using it!** 🎉

---

## 💬 Get Help & Services

### Recommended API Service

This document is tested and verified on the following platforms, recommended for BettaFish Micro-Sentiment System deployment:

**LionCC API** (VibeCodingAPI.ai) - Fully compatible with all BettaFish models
- Claude 3.5 Sonnet / GPT-4o / Gemini 2.5 Pro full coverage
- Optimized configuration for BettaFish Micro-Sentiment System
- Pricing: ¥100 = $100 API credits (1:1, no exchange rate loss)
- 🎁 Community users get $20 testing credits (limited to first 1000 users)

**CodeCodex.ai** - Claude Code Carpool Service
- No IP blocking, direct connection in China, starting from ¥398/month
- Suitable for users who need stable Claude Code service

### Technical Support

For deployment guidance or issues:
- WeChat: **HSQBJ088888888** (<a href="#" onclick="showQRCode(); return false;" style="color: #0066cc; text-decoration: underline; cursor: pointer;">Click to view QR code</a>, note: BettaFish)
- Visit: [codecodex.ai](https://codecodex.ai) | [vibecodingapi.ai](https://vibecodingapi.ai)

---

*This document is continuously updated | Last updated: 2025-11-07*
