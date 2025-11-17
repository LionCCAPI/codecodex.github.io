---
layout: page
title: Usage Guide
permalink: /en/usage-guide.html
lang: en-US
---

# 📖 Lion CC Usage Guide

> Complete website management and content publishing guide to help you quickly master all features of the Lion CC platform.

## 🎯 Guide Overview

| Type | Content | Target Audience |
|------|---------|-----------------|
| [📦 Installation Guide](#-installation-guide) | Claude Code installation for three platforms | All users |
| [📝 Content Publishing](#-content-publishing-guide) | Blog articles and page management | Content creators |
| [⚙️ Configuration Management](#️-configuration-management) | Website settings and environment variables | Developers |

---

## 📦 Installation Guide

### Core Features
- **Three-Platform Support**: Complete coverage for Windows, macOS, and Linux
- **Detailed Steps**: From environment setup to successful operation
- **Problem Solving**: Common issues and solutions
- **Advanced Configuration**: Gemini CLI and Codex integration

### Use Cases
- **New Users**: First-time Claude Code installation
- **Developers**: Complete environment configuration needed
- **Team Management**: Unified installation standards

### Quick Access
- **[Complete Installation Guide](/en/installation-guide.html)** - Detailed tutorial for three platforms
- **[Developer Configuration Guide](DEVELOPER_CONFIG_GUIDE.md)** - Quick environment variable setup

---

## 📝 Content Publishing Guide

### Blog Article Management

#### Beginner-Friendly Publishing Process
1. **Visit GitHub Repository**
2. **Navigate to `_posts_en` directory**
3. **Create New File**: `YYYY-MM-DD-title.md`
4. **Use Article Template**
5. **Commit and Publish**

#### Article Template
```markdown
---
layout: post
title: "Article Title"
date: 2025-09-20 16:00:00
summary: "Article summary"
categories: [Tutorial, Claude Code]
tags: [AI Programming, Productivity]
---

# Title

Article content...

## Subtitle

More content...
```

#### Advanced Features
- **Category Management**: Tutorials, Case Studies, Tool Recommendations, Community
- **Tag System**: AI Programming, Productivity, Best Practices
- **Image Upload**: Local images and external links supported
- **Comment System**: Giscus integration

### Page Management

#### Static Page Creation
```yaml
---
layout: page
title: Page Title
permalink: /en/page-name.html
lang: en-US
---

Page content...
```

#### Navigation Menu Configuration
Modify in `_config.yml`:
```yaml
menu_en:
  - title: "Page Name"
    url: "page-url.html"
```

### Quick Access
- **[Beginner Publishing Guide](BLOGGING_GUIDE.md)** - Blog publishing from scratch
- **[Content Creation Best Practices](#content-creation-best-practices)** - Writing tips and standards

---

## ⚙️ Configuration Management

### Website Basic Configuration

#### Core Settings (`_config.yml`)
```yaml
# Site Information
title: Lion CC
description: "The Ultimate Guide to Claude Code"
url: https://codecodex.ai
email: contact@codecodex.ai

# Feature Switches
showBuyCoffee: false
comments: true

# Navigation Menu
menu_en:
  - title: "Complete Guide"
    url: "comprehensive-guide.html"
  # More menu items...
```

#### Personalization Settings
- **Site Title and Description**
- **Contact Information and Social Media**
- **Feature Switches** (comments, donations, etc.)
- **Navigation Menu Structure**

### Environment Variable Management

#### Development Environment
```bash
# Local development
bundle exec jekyll serve --watch

# Production build
bundle exec jekyll build
```

#### Deployment Configuration
- **GitHub Pages**: Automatic deployment
- **Custom Domain**: CNAME configuration
- **SSL Certificate**: Automatically provided by GitHub

### Quick Access
- **[Developer Configuration Guide](DEVELOPER_CONFIG_GUIDE.md)** - Detailed configuration instructions
- **[Troubleshooting](#troubleshooting)** - Common problem solutions

---

## 🔧 Advanced Features

### API Integration
- **Claude Code API**: Official interface integration
- **Gemini CLI**: Google AI tool support
- **OpenAI Codex**: Code generation tools

### Monitoring and Analytics
- **API Usage Statistics**: Real-time monitoring dashboard
- **Performance Analysis**: Traffic and user behavior
- **Error Tracking**: Issue diagnosis and fixes

### Community Features
- **Carpool Service**: Team subscription management
- **User Groups**: Community exchange platform
- **Technical Support**: Professional problem solving

---

## 📚 Best Practices

### Content Creation Best Practices

#### Article Structure
1. **Introduction**: Brief description of topic and goals
2. **Preparation**: Required environment and tools
3. **Step Instructions**: Detailed operational guidance
4. **Code Examples**: Actual code demonstrations
5. **Summary**: Key points review and extension

#### Writing Tips
- **Clear Titles**: Accurately describe content
- **Clear Structure**: Use heading hierarchy
- **Code Standards**: Syntax highlighting and comments
- **Visual Content**: Add screenshots appropriately

### Configuration Management Best Practices

#### Version Control
```bash
# Backup before config changes
cp _config.yml _config.yml.backup

# Test configuration
bundle exec jekyll serve --watch

# Commit changes
git add _config.yml
git commit -m "Update config: add new menu item"
```

#### Environment Separation
- **Development Environment**: Local testing and debugging
- **Staging Environment**: Feature verification
- **Production Environment**: Official public service

---

## 🛠️ Troubleshooting

### Common Issues

#### Build Failures
```bash
# Check dependencies
bundle install

# Clear cache
bundle exec jekyll clean

# Rebuild
bundle exec jekyll build --trace
```

#### Page Display Issues
- **Check File Format**: YAML front matter format
- **Verify Links**: Relative paths and absolute paths
- **Clear Cache**: Browser force refresh

#### Features Not Working
- **Config File Syntax**: YAML format check
- **Permission Settings**: File read/write permissions
- **Environment Variables**: Correct setup and loading

### Debugging Tips
```bash
# Detailed error information
bundle exec jekyll serve --watch --trace

# Check config file
bundle exec jekyll doctor

# Verify site structure
bundle exec jekyll build --verbose
```

---

## 💬 Get Help

### Technical Support
- **Email Support**: contact@codecodex.ai
- **Community Chat**: [Telegram Group](https://t.me/codecodx_ai)
- **Documentation Feedback**: [GitHub Issues](https://github.com/codecodx-ai/codecodx.github.io/issues)

### Learning Resources
- **Video Tutorials**: YouTube Channel
- **Documentation Center**: Complete usage documentation
- **Best Practices**: Community experience sharing

### Quick Links
- [🏠 Home](/)
- [📖 Complete Guide](/en/comprehensive-guide.html)
- [🚗 Carpool Service](/en/carpool.html)
- [📚 Learning Resources](/en/resources.html)

---

*© 2025 Lion CC - Making AI Programming Simpler*
