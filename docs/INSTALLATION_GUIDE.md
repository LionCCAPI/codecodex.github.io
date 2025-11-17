# 📦 Claude Code 安装指南

> 完整详细的 Claude Code 三平台安装教程，从环境准备到成功运行一步到位！

## 🎯 选择你的操作系统

<div align="center">

| [🪟 Windows](#-windows-安装) | [🍎 macOS](#-macos-安装) | [🐧 Linux/WSL2](#-linux-安装) |
|---|---|---|
| PowerShell + 图形界面 | Terminal + Homebrew | 命令行 + 包管理器 |

</div>

---

## 🪟 Windows 安装

### 第一步：安装 Node.js 环境

Claude Code 需要 Node.js 环境才能运行。

#### 方法一：官网下载（推荐）

1. 打开浏览器访问 [https://nodejs.org/](https://nodejs.org/)
2. 点击 **"LTS"** 版本进行下载（推荐长期支持版本）
3. 下载完成后双击 `.msi` 文件
4. 按照安装向导完成安装，保持默认设置即可

#### 方法二：使用包管理器

如果你安装了 Chocolatey 或 Scoop，可以使用命令行安装：

```powershell
# 使用 Chocolatey
choco install nodejs

# 或使用 Scoop
scoop install nodejs
```

#### Windows 注意事项

- 建议使用 **PowerShell** 而不是 CMD
- 如果遇到权限问题，尝试以管理员身份运行
- 某些杀毒软件可能会误报，需要添加白名单

#### 验证安装是否成功

安装完成后，打开 PowerShell 或 CMD，输入以下命令：

```bash
node --version
npm --version
```

如果显示版本号，说明安装成功了！

### 第二步：安装 Claude Code

打开 PowerShell 或 CMD，运行以下命令：

```bash
# 全局安装 Claude Code
npm install -g @anthropic-ai/claude-code
```

> 💡 **提示**
> - 建议使用 PowerShell 而不是 CMD，功能更强大
> - 如果遇到权限问题，以管理员身份运行 PowerShell

#### 验证 Claude Code 安装

安装完成后，输入以下命令检查是否安装成功：

```bash
claude --version
```

如果显示版本号，恭喜你！Claude Code 已经成功安装了。

### 第三步：设置环境变量

为了让 Claude Code 连接到你的中转服务，需要设置两个环境变量。

#### 方法一：PowerShell 临时设置（当前会话）

在 PowerShell 中运行以下命令：

```powershell
$env:ANTHROPIC_BASE_URL = "https://use.codecodex.ai/api"
$env:ANTHROPIC_AUTH_TOKEN = "你的API密钥"
```

> 💡 记得将 **"你的API密钥"** 替换为在管理后台 "API Keys" 标签页中创建的实际密钥。

#### 方法二：PowerShell 永久设置（用户级）

在 PowerShell 中运行以下命令设置用户级环境变量：

```powershell
# 设置用户级环境变量（永久生效）
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_BASE_URL", "https://use.codecodx.ai/api", [System.EnvironmentVariableTarget]::User)
[System.Environment]::SetEnvironmentVariable("ANTHROPIC_AUTH_TOKEN", "你的API密钥", [System.EnvironmentVariableTarget]::User)
```

查看已设置的环境变量：

```powershell
# 查看用户级环境变量
[System.Environment]::GetEnvironmentVariable("ANTHROPIC_BASE_URL", [System.EnvironmentVariableTarget]::User)
[System.Environment]::GetEnvironmentVariable("ANTHROPIC_AUTH_TOKEN", [System.EnvironmentVariableTarget]::User)
```

> 💡 设置后需要重新打开 PowerShell 窗口才能生效。

#### 验证环境变量设置

设置完环境变量后，可以通过以下命令验证是否设置成功：

**在 PowerShell 中验证：**
```powershell
echo $env:ANTHROPIC_BASE_URL
echo $env:ANTHROPIC_AUTH_TOKEN
```

**在 CMD 中验证：**
```cmd
echo %ANTHROPIC_BASE_URL%
echo %ANTHROPIC_AUTH_TOKEN%
```

**预期输出示例：**
```
https://use.codecodx.ai/api
cr_xxxxxxxxxxxxxxxxxx
```

> 💡 如果输出为空或显示变量名本身，说明环境变量设置失败，请重新设置。

### 第四步：高级配置（可选）

#### 配置 Gemini CLI 环境变量

如果你使用 Gemini CLI，需要设置以下环境变量：

**PowerShell 设置方法：**
```powershell
$env:CODE_ASSIST_ENDPOINT = "https://use.codecodx.ai/gemini"
$env:GOOGLE_CLOUD_ACCESS_TOKEN = "你的API密钥"
$env:GOOGLE_GENAI_USE_GCA = "true"
```

**PowerShell 永久设置（用户级）：**
```powershell
# 设置用户级环境变量（永久生效）
[System.Environment]::SetEnvironmentVariable("CODE_ASSIST_ENDPOINT", "https://use.codecodx.ai/gemini", [System.EnvironmentVariableTarget]::User)
[System.Environment]::SetEnvironmentVariable("GOOGLE_CLOUD_ACCESS_TOKEN", "你的API密钥", [System.EnvironmentVariableTarget]::User)
[System.Environment]::SetEnvironmentVariable("GOOGLE_GENAI_USE_GCA", "true", [System.EnvironmentVariableTarget]::User)
```

**验证 Gemini CLI 环境变量：**
```powershell
echo $env:CODE_ASSIST_ENDPOINT
echo $env:GOOGLE_CLOUD_ACCESS_TOKEN
echo $env:GOOGLE_GENAI_USE_GCA
```

#### 配置 Codex 环境变量

如果你使用支持 OpenAI API 的工具（如 Codex），需要设置以下环境变量：

**在 `~/.codex/config.toml` 文件中添加以下配置：**
```toml
model_provider = "crs"
model = "gpt-5-codex"
model_reasoning_effort = "high"
disable_response_storage = true
preferred_auth_method = "apikey"

[model_providers.crs]
name = "crs"
base_url = "https://use.codecodx.ai/openai"
wire_api = "responses"
```

**在 `~/.codex/auth.json` 文件中配置API密钥：**
```json
{
  "OPENAI_API_KEY": "你的API密钥"
}
```

### 第五步：开始使用 Claude Code

现在你可以开始使用 Claude Code 了！

#### 启动 Claude Code

```bash
claude
```

#### 在特定项目中使用

```bash
# 进入你的项目目录
cd C:\path\to\your\project

# 启动 Claude Code
claude
```

### 🔧 Windows 常见问题解决

<details>
<summary><strong> 安装时提示 "permission denied" 错误</strong></summary>

**解决方案：**
1. 以管理员身份运行 PowerShell
2. 右键点击 PowerShell 图标 → "以管理员身份运行"
3. 重新执行安装命令

</details>

<details>
<summary><strong> PowerShell 执行策略错误</strong></summary>

**解决方案：**
```powershell
# 临时允许执行脚本
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# 或者临时绕过执行策略
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
```

</details>

<details>
<summary><strong> 环境变量设置后不生效</strong></summary>

**解决方案：**
1. 重新打开 PowerShell 窗口
2. 重启计算机
3. 检查环境变量是否正确设置：
   ```powershell
   Get-ChildItem Env: | Where-Object Name -like "*ANTHROPIC*"
   ```

</details>

---

## 🍎 macOS 安装

### 第一步：安装 Node.js 环境

Claude Code 需要 Node.js 环境才能运行。

#### 方法一：使用 Homebrew（推荐）

如果你已经安装了 Homebrew，使用它安装 Node.js 会更方便：

```bash
# 更新 Homebrew
brew update

# 安装 Node.js
brew install node
```

#### 方法二：官网下载

1. 访问 [https://nodejs.org/](https://nodejs.org/)
2. 下载适合 macOS 的 LTS 版本
3. 打开下载的 `.pkg` 文件
4. 按照安装程序指引完成安装

#### macOS 注意事项

- 如果遇到权限问题，可能需要使用 `sudo`
- 首次运行可能需要在系统偏好设置中允许
- 建议使用 Terminal 或 iTerm2

#### 验证安装是否成功

安装完成后，打开 Terminal，输入以下命令：

```bash
node --version
npm --version
```

如果显示版本号，说明安装成功了！

### 第二步：安装 Claude Code

打开 Terminal，运行以下命令：

```bash
# 全局安装 Claude Code
npm install -g @anthropic-ai/claude-code
```

如果遇到权限问题，可以使用 sudo：

```bash
sudo npm install -g @anthropic-ai/claude-code
```

#### 验证 Claude Code 安装

安装完成后，输入以下命令检查是否安装成功：

```bash
claude --version
```

如果显示版本号，恭喜你！Claude Code 已经成功安装了。

### 第三步：设置环境变量

为了让 Claude Code 连接到你的中转服务，需要设置两个环境变量。

#### 方法一：临时设置（当前会话）

在 Terminal 中运行以下命令：

```bash
export ANTHROPIC_BASE_URL="https://use.codecodx.ai/api"
export ANTHROPIC_AUTH_TOKEN="你的API密钥"
```

> 💡 记得将 **"你的API密钥"** 替换为在管理后台 "API Keys" 标签页中创建的实际密钥。

#### 方法二：永久设置

编辑你的 shell 配置文件（根据你使用的 shell）：

**对于 zsh（默认）：**
```bash
echo 'export ANTHROPIC_BASE_URL="https://use.codecodx.ai/api"' >> ~/.zshrc
echo 'export ANTHROPIC_AUTH_TOKEN="你的API密钥"' >> ~/.zshrc
source ~/.zshrc
```

**对于 bash：**
```bash
echo 'export ANTHROPIC_BASE_URL="https://use.codecodx.ai/api"' >> ~/.bash_profile
echo 'export ANTHROPIC_AUTH_TOKEN="你的API密钥"' >> ~/.bash_profile
source ~/.bash_profile
```

### 第四步：高级配置（可选）

#### 配置 Gemini CLI 环境变量

如果你使用 Gemini CLI，需要设置以下环境变量：

**Terminal 设置方法：**
```bash
export CODE_ASSIST_ENDPOINT="https://use.codecodx.ai/gemini"
export GOOGLE_CLOUD_ACCESS_TOKEN="你的API密钥"
export GOOGLE_GENAI_USE_GCA="true"
```

**永久设置方法：**
```bash
# 对于 zsh（默认）
echo 'export CODE_ASSIST_ENDPOINT="https://use.codecodx.ai/gemini"' >> ~/.zshrc
echo 'export GOOGLE_CLOUD_ACCESS_TOKEN="你的API密钥"' >> ~/.zshrc
echo 'export GOOGLE_GENAI_USE_GCA="true"' >> ~/.zshrc
source ~/.zshrc

# 对于 bash
echo 'export CODE_ASSIST_ENDPOINT="https://use.codecodx.ai/gemini"' >> ~/.bash_profile
echo 'export GOOGLE_CLOUD_ACCESS_TOKEN="你的API密钥"' >> ~/.bash_profile
echo 'export GOOGLE_GENAI_USE_GCA="true"' >> ~/.bash_profile
source ~/.bash_profile
```

**验证 Gemini CLI 环境变量：**
```bash
echo $CODE_ASSIST_ENDPOINT
echo $GOOGLE_CLOUD_ACCESS_TOKEN
echo $GOOGLE_GENAI_USE_GCA
```

#### 配置 Codex 环境变量

如果你使用支持 OpenAI API 的工具（如 Codex），需要设置以下环境变量：

**在 `~/.codex/config.toml` 文件中添加以下配置：**
```toml
model_provider = "crs"
model = "gpt-5-codex"
model_reasoning_effort = "high"
disable_response_storage = true
preferred_auth_method = "apikey"

[model_providers.crs]
name = "crs"
base_url = "https://use.codecodx.ai/openai"
wire_api = "responses"
```

**在 `~/.codex/auth.json` 文件中配置API密钥：**
```json
{
  "OPENAI_API_KEY": "你的API密钥"
}
```

### 第五步：开始使用 Claude Code

现在你可以开始使用 Claude Code 了！

#### 启动 Claude Code

```bash
claude
```

#### 在特定项目中使用

```bash
# 进入你的项目目录
cd /path/to/your/project

# 启动 Claude Code
claude
```

### 🔧 macOS 常见问题解决

<details>
<summary><strong> 安装时提示权限错误</strong></summary>

**解决方案：**
```bash
# 使用 sudo 安装
sudo npm install -g @anthropic-ai/claude-code

# 或者修改 npm 权限
sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
```

</details>

<details>
<summary><strong> macOS 安全设置阻止运行</strong></summary>

**解决方案：**
1. 打开"系统偏好设置" → "安全性与隐私"
2. 在"通用"标签页中，点击"仍要打开"
3. 或者在终端中运行：
   ```bash
   sudo spctl --master-disable
   ```

</details>

<details>
<summary><strong> 环境变量不生效</strong></summary>

**解决方案：**
1. 确保修改了正确的配置文件（`.zshrc` 或 `.bash_profile`）
2. 重新启动终端应用
3. 检查当前使用的 shell：
   ```bash
   echo $SHELL
   ```

</details>

---

## 🐧 Linux 安装

### 第一步：安装 Node.js 环境

Claude Code 需要 Node.js 环境才能运行。

#### 方法一：使用官方仓库（推荐）

```bash
# 添加 NodeSource 仓库
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -

# 安装 Node.js
sudo apt-get install -y nodejs
```

#### 方法二：使用系统包管理器

虽然版本可能不是最新的，但对于基本使用已经足够：

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install nodejs npm

# CentOS/RHEL/Fedora
sudo dnf install nodejs npm
```

#### Linux 注意事项

- 某些发行版可能需要安装额外的依赖
- 如果遇到权限问题，使用 `sudo`
- 确保你的用户在 npm 的全局目录有写权限

#### 验证安装是否成功

安装完成后，打开终端，输入以下命令：

```bash
node --version
npm --version
```

如果显示版本号，说明安装成功了！

### 第二步：安装 Claude Code

打开终端，运行以下命令：

```bash
# 全局安装 Claude Code
npm install -g @anthropic-ai/claude-code
```

如果遇到权限问题，可以使用 sudo：

```bash
sudo npm install -g @anthropic-ai/claude-code
```

#### 验证 Claude Code 安装

安装完成后，输入以下命令检查是否安装成功：

```bash
claude --version
```

如果显示版本号，恭喜你！Claude Code 已经成功安装了。

### 第三步：设置环境变量

为了让 Claude Code 连接到你的中转服务，需要设置两个环境变量。

#### 方法一：临时设置（当前会话）

在终端中运行以下命令：

```bash
export ANTHROPIC_BASE_URL="https://use.codecodx.ai/api"
export ANTHROPIC_AUTH_TOKEN="你的API密钥"
```

> 💡 记得将 **"你的API密钥"** 替换为在管理后台 "API Keys" 标签页中创建的实际密钥。

#### 方法二：永久设置

编辑你的 shell 配置文件：

```bash
# 对于 bash（默认）
echo 'export ANTHROPIC_BASE_URL="https://use.codecodx.ai/api"' >> ~/.bashrc
echo 'export ANTHROPIC_AUTH_TOKEN="你的API密钥"' >> ~/.bashrc
source ~/.bashrc

# 对于 zsh
echo 'export ANTHROPIC_BASE_URL="https://use.codecodx.ai/api"' >> ~/.zshrc
echo 'export ANTHROPIC_AUTH_TOKEN="你的API密钥"' >> ~/.zshrc
source ~/.zshrc
```

### 第四步：高级配置（可选）

#### 配置 Gemini CLI 环境变量

如果你使用 Gemini CLI，需要设置以下环境变量：

**终端设置方法：**
```bash
export CODE_ASSIST_ENDPOINT="https://use.codecodx.ai/gemini"
export GOOGLE_CLOUD_ACCESS_TOKEN="你的API密钥"
export GOOGLE_GENAI_USE_GCA="true"
```

**永久设置方法：**
```bash
# 对于 bash（默认）
echo 'export CODE_ASSIST_ENDPOINT="https://use.codecodx.ai/gemini"' >> ~/.bashrc
echo 'export GOOGLE_CLOUD_ACCESS_TOKEN="你的API密钥"' >> ~/.bashrc
echo 'export GOOGLE_GENAI_USE_GCA="true"' >> ~/.bashrc
source ~/.bashrc

# 对于 zsh
echo 'export CODE_ASSIST_ENDPOINT="https://use.codecodx.ai/gemini"' >> ~/.zshrc
echo 'export GOOGLE_CLOUD_ACCESS_TOKEN="你的API密钥"' >> ~/.zshrc
echo 'export GOOGLE_GENAI_USE_GCA="true"' >> ~/.zshrc
source ~/.zshrc
```

**验证 Gemini CLI 环境变量：**
```bash
echo $CODE_ASSIST_ENDPOINT
echo $GOOGLE_CLOUD_ACCESS_TOKEN
echo $GOOGLE_GENAI_USE_GCA
```

#### 配置 Codex 环境变量

如果你使用支持 OpenAI API 的工具（如 Codex），需要设置以下环境变量：

**在 `~/.codex/config.toml` 文件中添加以下配置：**
```toml
model_provider = "crs"
model = "gpt-5-codex"
model_reasoning_effort = "high"
disable_response_storage = true
preferred_auth_method = "apikey"

[model_providers.crs]
name = "crs"
base_url = "https://use.codecodx.ai/openai"
wire_api = "responses"
```

**在 `~/.codex/auth.json` 文件中配置API密钥：**
```json
{
  "OPENAI_API_KEY": "你的API密钥"
}
```

### 第五步：开始使用 Claude Code

现在你可以开始使用 Claude Code 了！

#### 启动 Claude Code

```bash
claude
```

#### 在特定项目中使用

```bash
# 进入你的项目目录
cd /path/to/your/project

# 启动 Claude Code
claude
```

### 🔧 Linux 常见问题解决

<details>
<summary><strong> 安装时提示权限错误</strong></summary>

**解决方案：**
```bash
# 使用 sudo 安装
sudo npm install -g @anthropic-ai/claude-code

# 或者修改 npm 权限
sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
```

</details>

<details>
<summary><strong> 缺少依赖库</strong></summary>

**解决方案：**
```bash
# Ubuntu/Debian
sudo apt-get install build-essential

# CentOS/RHEL/Fedora
sudo dnf groupinstall "Development Tools"
```

</details>

<details>
<summary><strong> 环境变量不生效</strong></summary>

**解决方案：**
1. 确保修改了正确的配置文件
2. 重新启动终端
3. 检查当前使用的 shell：
   ```bash
   echo $SHELL
   ```

</details>

---

## 🎉 恭喜你！

你已经成功安装并配置了 Claude Code，现在可以开始享受 AI 编程助手带来的便利了。

### 🚀 下一步

1. **开始第一个项目**：在项目目录中运行 `claude`
2. **探索功能**：尝试代码生成、重构、调试等功能
3. **加入社区**：获取更多使用技巧和最佳实践

### 📚 相关资源

- [使用教程](./BLOGGING_GUIDE.md) - 详细的使用指南
- [开发者配置](./DEVELOPER_CONFIG_GUIDE.md) - 高级配置选项
- [官方文档](https://docs.anthropic.com/) - Anthropic 官方文档

### 💬 需要帮助？

如果在使用过程中遇到任何问题，可以：

- 查看上方的常见问题解决方案
- 访问 [GitHub Issues](https://github.com/codecodx-ai/codecodx.github.io/issues)
- 加入我们的 [Telegram 群组](https://t.me/codecodx_ai)

---

<div align="center">

**🌟 开始你的 AI 编程之旅！**

[🏠 返回首页](/) | [📖 使用教程](./BLOGGING_GUIDE.md) | [⚙️ 开发者配置](./DEVELOPER_CONFIG_GUIDE.md)

---

© 2025 CodeCodex - 探索 AI 编程的无限可能

</div>