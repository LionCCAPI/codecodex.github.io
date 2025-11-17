---
layout: post
title: "BettaFish 微舆系统 - LionCC API 部署配置完全指南"
date: 2025-11-07 08:00:00 +0800
summary: "BettaFish 微舆系统完整部署教程，包含 LionCC API 配置、Docker 部署、模型选择建议及常见问题解决方案。支持 Claude、GPT-4、Gemini 等多种 LLM 模型。"
categories: Tech
tags: [BettaFish, LionCC, API部署, Docker, LLM, Claude, GPT-4, Gemini]
author: Lion CC
lang: zh-CN
lang_ref: bettafish-lioncc-deployment
---

> **作者**: Lion CC（[lioncc.ai](https://lioncc.ai)） 微信：HSQBJ088888888
>
> **文档更新时间**: 2025-11-07
> **系统版本**: v1.0.1
> **部署方式**: Docker
> **更新内容**: 新增 Gemini 2.5 Pro 模型配置,更新推荐模型列表

---

## 💡 关于 LionCC API 服务

本指南基于 **LionCC API**（VibeCodingAPI.ai）平台测试验证，已完整适配 BettaFish 微舆系统所有 LLM 模型（Claude、GPT-4、Gemini 等）。

> **🎁 福利**: 通过 <a href="#" onclick="showQRCode(); return false;" style="color: #0066cc; text-decoration: underline; cursor: pointer;">codecodex.ai 社群</a> 注册 LionCC API 可获 $20 测试额度（限前 1000 名）

<div id="qrcode-modal" style="display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.8); z-index: 9999; justify-content: center; align-items: center;" onclick="hideQRCode()">
  <div style="background: white; padding: 30px; border-radius: 15px; text-align: center; max-width: 400px;" onclick="event.stopPropagation()">
    <h3 style="margin-top: 0; color: #333;">添加业务助手微信</h3>
    <img src="/images/wechat-assistant-qrcode.jpg" alt="Lion CC 业务助手微信二维码" style="width: 100%; max-width: 300px; border-radius: 10px; margin: 20px 0;">
    <p style="color: #666; font-size: 14px;">微信扫码添加业务助手，备注：<strong>BettaFish</strong></p>
    <p style="color: #999; font-size: 12px; margin-top: 5px;">获取 $20 API 测试额度 + 技术支持</p>
    <button onclick="hideQRCode()" style="background: #0066cc; color: white; border: none; padding: 10px 30px; border-radius: 5px; cursor: pointer; font-size: 16px; margin-top: 10px;">关闭</button>
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

// ESC键关闭
document.addEventListener('keydown', function(e) {
  if (e.key === 'Escape') {
    hideQRCode();
  }
});
</script>

---

## 📋 目录

1. [系统架构概述](#️-系统架构概述)
2. [第三方 API 配置要点](#-第三方-api-配置要点)
3. [Docker 部署注意事项](#-docker-部署注意事项)
4. [常见问题与解决方案](#-常见问题与解决方案)
5. [🚀 快速启动指南 ⭐️](#-快速启动指南-️-核心内容) **← 推荐从这里开始**

---

## 🏗️ 系统架构概述

### 核心组件

```
BettaFish 微舆系统
├── InsightEngine     - 私有数据库挖掘 (Claude 3.5 Sonnet)
├── MediaEngine       - 多模态内容分析 (Gemini Pro)
├── QueryEngine       - 网络搜索推理 (DeepSeek Chat)
├── ForumEngine       - Agent 协作论坛
└── ReportEngine      - 智能报告生成 (Gemini 2.5 Pro)
```

### 技术栈

- **后端**: Python 3.11 + Flask + LangGraph
- **数据库**: MySQL 8.0
- **容器**: Docker + Docker Network
- **前端**: Streamlit (单引擎) + HTML/JavaScript (主应用)

---

## 🔑 第三方 API 配置要点

### 1. LLM API 配置 (LionCC API)

#### 📍 API 提供商
- **服务名称**: LionCC API
- **平台**: VibeCodingAPI.ai
- **官网**: [https://vibecodingapi.ai](https://vibecodingapi.ai)
- **特点**: OpenAI 兼容接口,专为 BettaFish 微舆系统优化,支持所有主流 LLM 模型

#### 🔐 API Key 配置

```bash
# 所有引擎使用同一个 API Key
INSIGHT_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
MEDIA_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
QUERY_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
REPORT_ENGINE_API_KEY=sk-YOUR_API_KEY_HERE
FORUM_HOST_API_KEY=sk-YOUR_API_KEY_HERE
MINDSPIDER_API_KEY=sk-YOUR_API_KEY_HERE
KEYWORD_OPTIMIZER_API_KEY=sk-YOUR_API_KEY_HERE
```

#### 🎯 推荐模型配置

| Engine | 推荐模型 | 原因 | 备选方案 |
|--------|---------|------|----------|
| **InsightEngine** | `claude-3-5-sonnet-20241022` | 数据分析能力强 | `claude-3-opus-20240229` |
| **MediaEngine** | `gemini-pro` | 多模态理解优秀 | `gpt-4o` |
| **QueryEngine** | `deepseek-chat` | 推理能力强,性价比高 | `gpt-4-turbo` |
| **ReportEngine** | `gemini-2.5-pro` | 最新Gemini模型,性能卓越 | `gpt-4o`, `gpt-4` |
| **ForumEngine** | `claude-3-5-sonnet-20241022` | 协作能力强 | `gpt-4` |
| **MindSpider** | `deepseek-chat` | 爬虫分析,成本低 | `gpt-3.5-turbo` |
| **KeywordOptimizer** | `gpt-3.5-turbo` | 轻量任务,快速 | `deepseek-chat` |

#### ⚠️ 已测试模型列表

**✅ 可用模型** (通过 LionCC API 测试验证):
```
- gpt-4o              ✅ (最新 GPT-4 Optimized)
- gpt-4               ✅
- gpt-4-turbo         ✅
- gpt-3.5-turbo       ✅
- claude-3-5-sonnet-20241022  ✅ (推荐)
- claude-3-opus-20240229      ✅
- gemini-pro          ✅
- gemini-2.5-pro      ✅ (最新版本,性能卓越,推荐用于报告生成)
- deepseek-chat       ✅ (推荐,性价比高)
- deepseek-reasoner   ⚠️ (不稳定,负载高时失败,已不推荐使用)
```

**❌ 不可用模型**:
```
- kimi-k2-0711-preview    ❌ (HTTP 500)
- qwen-plus               ❌ (HTTP 503)
- qwen-turbo              ❌ (HTTP 503)
- gemini-2.0-flash-exp    ❌ (HTTP 500)
```

#### 🆕 Gemini 2.5 Pro 新特性

**推荐场景**: ReportEngine (报告生成)

**优势**:
- ✅ 最新一代 Gemini 模型,性能大幅提升
- ✅ 长上下文支持 (1M+ tokens),适合大规模报告生成
- ✅ 多语言优化,中英文生成质量优秀
- ✅ 结构化输出能力强,适合 HTML/Markdown 格式报告
- ✅ 性价比高于 GPT-4o

**注意事项**:
- ⚠️ 相比 Gemini Pro,Token 消耗略高
- ⚠️ 某些 API 提供商可能尚未支持此模型
- ⚠️ 建议先测试可用性再大规模使用

**测试命令**:
```bash
# 测试 Gemini 2.5 Pro 可用性
curl -X POST "https://vibecodingapi.ai/v1/chat/completions" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gemini-2.5-pro",
    "messages": [{"role": "user", "content": "测试"}],
    "max_tokens": 100
  }'
```

---

#### 💡 模型切换建议

如果遇到特定模型不可用,按以下优先级切换:

**文本分析任务**:
```
claude-3-5-sonnet > gpt-4o > gpt-4-turbo > deepseek-chat
```

**推理任务**:
```
deepseek-chat > gpt-4-turbo > claude-3-opus
```

**报告生成**:
```
gemini-2.5-pro > gpt-4o > gpt-4 > claude-3-5-sonnet
```

**成本优化**:
```
deepseek-chat > gpt-3.5-turbo > gemini-pro
```

---

### 2. Bocha API 配置 (多模态搜索)

#### 📍 API 信息
- **名称**: Bocha AI
- **官网**: [https://api.bochaai.com](https://api.bochaai.com) 或 [https://open.bochaai.com](https://open.bochaai.com)
- **功能**: 多模态网络搜索 (图片、视频、网页)
- **使用引擎**: MediaEngine

#### 🔐 配置要点

```bash
# Bocha API 配置
BOCHA_BASE_URL=https://api.bochaai.com
BOCHA_WEB_SEARCH_API_KEY=sk-YOUR_BOCHA_KEY_HERE
```

#### ⚠️ 关键注意事项

**1. API 端点选择**

Bocha 有两种 API 套餐:

| 套餐类型 | API 端点 | 用途 |
|---------|----------|------|
| **Web Search** | `/v1/web-search` | 网页搜索 (推荐) |
| **AI Search** | `/v1/ai-search` | AI 增强搜索 (需要高级套餐) |

**2. 代码配置**

默认情况下,BettaFish 使用 `/v1/ai-search`,如果你的套餐是 Web Search,需要修改:

```bash
# 修改文件: MediaEngine/tools/search.py
# 第 94 行
BASE_URL = "https://api.bochaai.com/v1/web-search"  # 改为 web-search
```

**3. 配额检查**

登录 Bocha 后台检查:
- 账户余额
- 套餐类型 (Web Search / AI Search)
- 剩余次数

**4. 常见错误**

```json
{"message": "You do not have enough money or package quota", "code": "403"}
```
**解决方案**:
- 充值账户
- 确认使用正确的 API 端点
- 检查 API Key 是否正确

---

### 3. Tavily API 配置 (网络搜索)

#### 📍 API 信息
- **名称**: Tavily
- **官网**: [https://www.tavily.com](https://www.tavily.com)
- **功能**: 文本网络搜索
- **使用引擎**: InsightEngine, QueryEngine

#### 🔐 配置

```bash
TAVILY_API_KEY=tvly-YOUR_KEY_HERE
```

#### ✅ 特点

- **免费额度**: 通常有试用额度
- **稳定性**: 较高
- **速度**: 快速
- **语言**: 支持中英文

#### 💡 测试命令

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

## 🐳 Docker 部署注意事项

### 1. Docker 镜像构建

#### 📋 基础配置

```dockerfile
FROM python:3.11-slim

# 关键依赖
RUN apt-get update && apt-get install -y \
    build-essential \
    ffmpeg \
    libgl1 \
    chromium \
    && apt-get clean

# Python 包管理器 (使用 uv 加速)
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
```

#### ⚠️ 注意事项

**1. Python 版本锁定**
- ✅ **使用 Python 3.11** (推荐)
- ❌ **不要使用 Python 3.14** (兼容性问题)
- ⚠️ Python 3.12 未测试

**2. 依赖安装问题**

某些包需要在容器启动后安装:

```bash
# cryptography (MySQL 认证)
docker exec bettafish pip install cryptography --quiet

# 如果遇到权限问题
docker exec -u root bettafish pip install cryptography
```

**永久解决方案**: 将 `cryptography` 添加到 `requirements.txt` 并重新构建镜像。

---

### 2. 容器配置

#### 📍 端口映射

```bash
docker run -d \
  --name bettafish \
  -p 15888:5000   # Flask 主应用
  -p 8501:8501    # InsightEngine (Streamlit)
  -p 8502:8502    # MediaEngine (Streamlit)
  -p 8503:8503    # QueryEngine (Streamlit)
  bettafish:latest
```

#### ⚠️ 端口冲突问题

**问题**: 默认端口 5000 可能被代理占用 (如 Clash)

**现象**:
```
HTTP 403 Forbidden
localhost:5000 无法访问
```

**解决方案**:
```bash
# 方法 1: 改用非标准端口
-p 15888:5000

# 方法 2: 设置 no_proxy
export no_proxy="localhost,127.0.0.1"
open -a "Google Chrome" "http://localhost:15888"
```

---

### 3. 网络配置

#### 📍 Docker Network

BettaFish 使用独立的 Docker 网络连接容器:

```bash
# 创建网络
docker network create bettafish-network

# MySQL 容器
docker run -d \
  --name bettafish-mysql \
  --network bettafish-network \
  -p 3307:3306 \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=bettafish_db \
  mysql:8.0

# 应用容器
docker run -d \
  --name bettafish \
  --network bettafish-network \
  -p 15888:5000 \
  bettafish:latest
```

#### ⚠️ 数据库连接配置

**.env 文件配置**:
```bash
# ❌ 错误 (容器内无法使用 localhost)
DB_HOST=localhost

# ✅ 正确 (使用容器名)
DB_HOST=bettafish-mysql
DB_PORT=3306
```

---

### 4. 环境变量管理

#### 📋 .env 文件同步

**问题**: Docker 镜像中包含旧的 .env 文件

**现象**:
- 更新宿主机 .env 文件后,容器内配置不生效
- `docker restart` 不会重新加载 .env

**解决方案**:

```bash
# 方法 1: 手动复制 (推荐)
docker cp .env bettafish:/app/.env
docker restart bettafish

# 方法 2: 使用 --env-file (创建容器时)
docker run -d --env-file .env bettafish:latest

# 方法 3: 重新构建镜像
docker build -t bettafish:latest .
```

#### ⚠️ 配置更新流程

每次修改 .env 或代码后:

```bash
# 1. 停止并删除旧容器
docker stop bettafish && docker rm bettafish

# 2. 重新构建镜像 (如果代码有变化)
docker build -t bettafish:latest .

# 3. 启动新容器
docker run -d \
  --name bettafish \
  --network bettafish-network \
  -p 15888:5000 \
  -p 8501-8503:8501-8503 \
  --env-file .env \
  bettafish:latest

# 4. 安装额外依赖
docker exec bettafish pip install cryptography --quiet

# 5. 重启生效
docker restart bettafish
```

---

### 5. 数据持久化

#### 📍 重要目录

```bash
/app/logs/              # 运行日志
/app/final_reports/     # 生成的报告
/app/forum.log          # 论坛讨论日志
/app/templates/         # 自定义模板
```

#### 💡 挂载卷 (可选)

```bash
docker run -d \
  -v /host/path/logs:/app/logs \
  -v /host/path/reports:/app/final_reports \
  bettafish:latest
```

---

## 🔧 常见问题与解决方案

### 1. ModuleNotFoundError: No module named 'config'

**原因**: 容器中缺少 config.py 文件

**解决方案**:

```bash
# 创建 config.py
docker exec bettafish bash -c 'cat > /app/config.py << EOF
import os
from dotenv import load_dotenv

load_dotenv()

# 数据库配置
DB_HOST = os.getenv("DB_HOST", "localhost")
DB_PORT = int(os.getenv("DB_PORT", "3306"))
DB_USER = os.getenv("DB_USER", "root")
DB_PASSWORD = os.getenv("DB_PASSWORD", "")
DB_NAME = os.getenv("DB_NAME", "bettafish_db")

# LLM 配置 (添加所有需要的配置项)
# ...
EOF'

# 重启容器
docker restart bettafish
```

**永久解决方案**: 在项目根目录创建 config.py,重新构建镜像。

---

### 2. MySQL 认证失败

**错误信息**:
```
Authentication plugin 'caching_sha2_password' cannot be loaded
```

**原因**: PyMySQL 需要 cryptography 包支持 MySQL 8.0

**解决方案**:

```bash
docker exec bettafish pip install cryptography --quiet
docker restart bettafish
```

---

### 3. Bocha API 403 错误

**错误信息**:
```json
{"message": "You do not have enough money or package quota", "code": "403"}
```

**排查步骤**:

1. **检查 API Key**:
   ```bash
   docker exec bettafish grep "BOCHA" /app/.env
   ```

2. **确认账户余额**: 登录 Bocha 后台查看

3. **确认 API 端点**: 检查是否使用了正确的端点 (web-search vs ai-search)

4. **测试 API**:
   ```bash
   curl -X POST "https://api.bochaai.com/v1/web-search" \
     -H "Authorization: Bearer YOUR_KEY" \
     -H "Content-Type: application/json" \
     -d '{"query":"test"}'
   ```

---

### 4. LLM API 负载过高 (500 错误)

**错误信息**:
```json
{"error": {"message": "当前模型负载较高,请稍候重试,或者切换其他模型"}}
```

**解决方案**:

**方法 1: 等待重试** (系统会自动重试)

**方法 2: 切换备用模型**

```bash
# 编辑 .env 文件
# 将不稳定的模型换成备用模型
QUERY_ENGINE_MODEL_NAME=deepseek-chat  # 从 deepseek-reasoner 改为 deepseek-chat

# 同步到容器
docker cp .env bettafish:/app/.env
docker restart bettafish
```

---

### 5. 报告格式问题

**问题**: 生成的报告是纯文本,没有可视化

**原因**:
1. 系统的可视化是内置的,不依赖模板
2. 模板只定义报告大纲结构

**说明**:
- ✅ 系统已有 6 个内置模板
- ✅ ReportEngine 会自动选择合适的模板
- ✅ 可视化效果 (图表、数据卡片) 是代码生成的
- ⚠️ "上传模板"功能用于自定义报告结构,不是添加可视化

**确认系统正常**:
- 查看日志中是否有 `[HTMLGenerationNode] 开始生成HTML报告...`
- 检查 `/app/final_reports/` 目录下的报告文件

---

## 🚀 快速启动指南 ⭐️ 核心内容

> **💡 重要提示**: 这是最快速部署 BettaFish 的方法，建议收藏此脚本！
>
> **适用场景**: 已完成初始化部署，需要快速启动系统

### 完整启动脚本

> **📦 一键启动脚本 - 复制即用**
>
> 将以下内容保存为 `start-bettafish.sh`，赋予执行权限后直接运行即可启动整个系统。

```bash
#!/bin/bash

echo "======================================"
echo "BettaFish 微舆系统 - 快速启动"
echo "======================================"

# 1. 启动 MySQL
echo "1️⃣  启动 MySQL 容器..."
docker start bettafish-mysql
sleep 3

# 2. 启动应用
echo "2️⃣  启动 BettaFish 容器..."
docker start bettafish
sleep 10

# 3. 同步配置文件
echo "3️⃣  同步配置文件..."
docker cp .env bettafish:/app/.env 2>/dev/null || echo "   .env 已同步"

# 4. 安装依赖
echo "4️⃣  安装必要依赖..."
docker exec bettafish pip install cryptography --quiet 2>/dev/null

# 5. 重启应用
echo "5️⃣  重启应用加载配置..."
docker restart bettafish >/dev/null 2>&1
sleep 30

# 6. 检查状态
echo "6️⃣  检查服务状态..."
docker ps --filter "name=bettafish" --format "   ✓ {% raw %}{{.Names}}: {{.Status}}{% endraw %}"

echo ""
echo "======================================"
echo "✅ 启动完成！"
echo "======================================"
echo ""
echo "🌐 访问地址:"
echo "   主应用: http://localhost:15888"
echo "   InsightEngine: http://localhost:8501"
echo "   MediaEngine: http://localhost:8502"
echo "   QueryEngine: http://localhost:8503"
echo ""
echo "💡 打开浏览器:"
export no_proxy="localhost,127.0.0.1"
export NO_PROXY="localhost,127.0.0.1"
open -a "Google Chrome" "http://localhost:15888"
```

**使用方法**:

```bash
chmod +x start-bettafish.sh
./start-bettafish.sh
```

---

## 📚 配置文件完整示例

### .env 文件模板

```bash
# ====================== 数据库配置 ======================
DB_HOST=bettafish-mysql
DB_PORT=3306
DB_USER=bettafish_user
DB_PASSWORD=BettaFish2024!
DB_NAME=bettafish_db
DB_CHARSET=utf8mb4
DB_DIALECT=mysql

# ======================= LLM 配置 =======================
# Insight Agent - 数据库挖掘
INSIGHT_ENGINE_API_KEY=sk-YOUR_API_KEY
INSIGHT_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
INSIGHT_ENGINE_MODEL_NAME=claude-3-5-sonnet-20241022

# Media Agent - 多模态分析
MEDIA_ENGINE_API_KEY=sk-YOUR_API_KEY
MEDIA_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
MEDIA_ENGINE_MODEL_NAME=gemini-pro

# Query Agent - 网络搜索
QUERY_ENGINE_API_KEY=sk-YOUR_API_KEY
QUERY_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
QUERY_ENGINE_MODEL_NAME=deepseek-chat

# Report Agent - 报告生成
REPORT_ENGINE_API_KEY=sk-YOUR_API_KEY
REPORT_ENGINE_BASE_URL=https://vibecodingapi.ai/v1
REPORT_ENGINE_MODEL_NAME=gemini-2.5-pro

# Forum Host - 论坛主持
FORUM_HOST_API_KEY=sk-YOUR_API_KEY
FORUM_HOST_BASE_URL=https://vibecodingapi.ai/v1
FORUM_HOST_MODEL_NAME=claude-3-5-sonnet-20241022

# MindSpider - 爬虫分析
MINDSPIDER_API_KEY=sk-YOUR_API_KEY
MINDSPIDER_BASE_URL=https://vibecodingapi.ai/v1
MINDSPIDER_MODEL_NAME=deepseek-chat

# Keyword Optimizer - 关键词优化
KEYWORD_OPTIMIZER_API_KEY=sk-YOUR_API_KEY
KEYWORD_OPTIMIZER_BASE_URL=https://vibecodingapi.ai/v1
KEYWORD_OPTIMIZER_MODEL_NAME=gpt-3.5-turbo

# ================== 网络工具配置 ====================
# Tavily API (网络搜索)
TAVILY_API_KEY=tvly-YOUR_KEY

# Bocha API (多模态搜索)
BOCHA_BASE_URL=https://api.bochaai.com
BOCHA_WEB_SEARCH_API_KEY=sk-YOUR_BOCHA_KEY
```

---

## 🎯 部署检查清单

### 部署前检查

- [ ] Python 3.11 环境
- [ ] Docker 和 Docker Compose 已安装
- [ ] 至少 4GB 可用内存
- [ ] 端口 15888, 8501-8503 未被占用

### API 配置检查

- [ ] VibeCodeAI API Key 已获取
- [ ] Tavily API Key 已获取
- [ ] Bocha API Key 已获取 (可选)
- [ ] 所有模型已测试可用

### 容器配置检查

- [ ] Docker 网络已创建
- [ ] MySQL 容器运行正常
- [ ] BettaFish 容器运行正常
- [ ] 容器间网络连通

### 功能测试检查

- [ ] 主应用 (15888) 可访问
- [ ] 3 个 Streamlit Engine (8501-8503) 可访问
- [ ] 数据库连接成功
- [ ] 测试查询能生成报告
- [ ] 5 个 Engine 状态显示绿色

---

## 📞 获取帮助

### 官方资源

- **GitHub**: [https://github.com/666ghj/BettaFish](https://github.com/666ghj/BettaFish)
- **文档**: README.md
- **讨论**: [https://linux.do/t/topic/1009280](https://linux.do/t/topic/1009280)
- **示例报告**: `final_reports/final_report__20250827_131630.html`

### 日志查看

```bash
# 实时日志
docker logs -f bettafish

# 最近 100 行
docker logs bettafish --tail 100

# 错误日志
docker logs bettafish 2>&1 | grep -i error
```

---

## ✅ 总结

**BettaFish 部署成功的标志**:

1. ✅ 所有容器运行中
2. ✅ 主应用可访问 (http://localhost:15888)
3. ✅ 5 个 Engine 指示灯全部绿色
4. ✅ 测试查询能成功生成报告
5. ✅ 报告包含可视化内容

**关键配置要点**:

- 🔑 **API Key 配置正确** (VibeCodeAI, Tavily, Bocha)
- 🎯 **模型选择合适** (根据任务选择最佳模型)
- 🐳 **Docker 配置完整** (网络、端口、环境变量)
- 📁 **文件同步及时** (.env, config.py)

---

## 📝 更新日志

### v1.0.1 (2025-11-07)

**新增内容**:
- ✨ 新增 Gemini 2.5 Pro 模型配置说明
- ✨ 添加 Gemini 2.5 Pro 特性介绍和测试方法
- 📝 更新 ReportEngine 推荐模型为 `gemini-2.5-pro`
- 📝 更新模型优先级推荐列表
- 📝 更新已测试模型列表
- 📝 更新 .env 配置文件模板

**优化内容**:
- 🔧 标注 DeepSeek Reasoner 不稳定,不推荐使用
- 🔧 优化报告生成模型选择建议

### v1.0.0 (2025-11-06)

**初始版本**:
- 📚 完整的 BettaFish 系统部署指南
- 🔑 第三方 API 配置详解 (VibeCodeAI, Tavily, Bocha)
- 🐳 Docker 部署注意事项
- 🔧 常见问题与解决方案
- 🚀 快速启动脚本

---

**祝你使用愉快！** 🎉

---

## 💬 获取帮助与服务

### API 服务推荐

本文档基于以下平台测试验证，推荐用于 BettaFish 微舆系统部署：

**LionCC API** (VibeCodingAPI.ai) - 已完整适配 BettaFish 所有模型
- Claude 3.5 Sonnet / GPT-4o / Gemini 2.5 Pro 全覆盖
- 专为 BettaFish 微舆系统优化配置
- 价格：¥100 = $100 API 额度（1:1，无汇率损失）
- 🎁 社群用户送 $20 测试额度（限前 1000 名）

**CodeCodex.ai** - Claude Code 拼车服务
- 无 IP 封锁，国内直连，最低 ¥398/月起
- 适合需要稳定 Claude Code 服务的用户

### 技术支持

如需部署指导或遇到问题：
- 微信：**HSQBJ088888888**（<a href="#" onclick="showQRCode(); return false;" style="color: #0066cc; text-decoration: underline; cursor: pointer;">点击查看二维码</a>，备注：BettaFish）
- 访问：[codecodex.ai](https://codecodex.ai) | [vibecodingapi.ai](https://vibecodingapi.ai)

---

*本文档持续更新中 | 最后更新：2025-11-07*
