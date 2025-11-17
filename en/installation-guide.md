---
layout: page
title: Claude Code Installation Guide
permalink: /en/installation-guide.html
lang: en-US
---

<div class="install-hero">
  <h1>📦 Claude Code Installation Guide</h1>
  <p class="subtitle">Complete guide for Windows / macOS / Linux - from environment setup to first run.</p>
  <div class="quick-actions">
    <a class="qa-btn" href="/en/carpool.html">🚀 Get Started</a>
    <a class="qa-btn ghost" href="/en/comprehensive-guide.html">📖 Complete Guide</a>
  </div>
</div>

## 🎯 Choose Your Operating System

<div class="installation-tabs">
  <div class="tab-buttons">
    <button class="tab-button active" data-tab="windows">
      <span class="tab-icon">🪟</span>
      <span class="tab-title">Windows</span>
      <span class="tab-subtitle">PowerShell + GUI</span>
    </button>
    <button class="tab-button" data-tab="macos">
      <span class="tab-icon">🍎</span>
      <span class="tab-title">macOS</span>
      <span class="tab-subtitle">Terminal + Homebrew</span>
    </button>
    <button class="tab-button" data-tab="linux">
      <span class="tab-icon">🐧</span>
      <span class="tab-title">Linux/WSL2</span>
      <span class="tab-subtitle">Command Line + Package Manager</span>
    </button>
  </div>

  <div class="tab-contents">
    <div class="tab-content active" id="windows">
      {% include installation_en/windows.html %}
    </div>

    <div class="tab-content" id="macos">
      {% include installation_en/macos.html %}
    </div>

    <div class="tab-content" id="linux">
      {% include installation_en/linux.html %}
    </div>
  </div>
</div>

---

## 🎉 Congratulations!

You've successfully installed and configured Claude Code. Now you can start enjoying the convenience of an AI programming assistant.

### 🚀 Next Steps

1. **Start Your First Project**: Run `claude` in your project directory
2. **Explore Features**: Try code generation, refactoring, debugging, etc.
3. **Join Community**: Get more tips and best practices

### 📚 Related Resources

- [Complete Guide](/en/comprehensive-guide.html) - One-stop service guide
- [Deployment Guide](/en/deployment-guide.html) - Step-by-step deployment tutorial
- [Carpool Service](/en/carpool.html) - Team subscription guide

### 💬 Need Help?

If you encounter any issues:

- Check the troubleshooting solutions above
- Visit [GitHub Issues](https://github.com/Jascenn/codecodex.ai/issues)
- Join our [Telegram Group](https://t.me/codecodx_ai)

---

<div class="install-footer-cta" role="contentinfo">
  <strong>🌟 Start Your AI Programming Journey!</strong>
  <div class="links">
    <a href="/en/">🏠 Home</a>
    <span>·</span>
    <a href="/en/deployment-guide.html">📖 Deployment Guide</a>
    <span>·</span>
    <a href="/en/carpool.html">🚗 Carpool Service</a>
  </div>
  <div class="copyright">© 2025 CodeCodex - Explore the Infinite Possibilities of AI Programming</div>
</div>

<style>
.installation-tabs {
  margin: 2rem 0;
}

.install-hero {
  margin: 0 0 1.25rem;
}
.install-hero .subtitle {
  margin: .5rem 0 1rem;
  color: #475569;
}
.quick-actions {
  display: flex;
  gap: .75rem;
}
.qa-btn {
  display: inline-block;
  padding: .5rem .9rem;
  border-radius: 8px;
  background: #2563eb;
  color: #fff !important;
  text-decoration: none;
  font-weight: 600;
}
.qa-btn.ghost {
  background: #eef2ff;
  color: #1e293b !important;
}

.tab-buttons {
  display: flex;
  border-bottom: 2px solid #e2e8f0;
  margin-bottom: 2rem;
  gap: 0.5rem;
}

.tab-button {
  background: none;
  border: none;
  padding: 1rem 1.5rem;
  cursor: pointer;
  border-radius: 8px 8px 0 0;
  transition: all 0.3s ease;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.25rem;
  min-width: 140px;
  border-bottom: 3px solid transparent;
}

.tab-button:hover {
  background-color: #f7fafc;
}

.tab-button.active {
  background-color: #3182ce;
  color: white;
  border-bottom-color: #3182ce;
}

.tab-icon {
  font-size: 2rem;
}

.tab-title {
  font-size: 1.1rem;
  font-weight: 600;
}

.tab-subtitle {
  font-size: 0.85rem;
  opacity: 0.8;
}

.tab-content {
  display: none;
  padding: 1.5rem;
  background-color: #f7fafc;
  border-radius: 8px;
  border: 1px solid #e2e8f0;
}

.tab-content.active {
  display: block;
}

.install-footer-cta {
  margin-top: 2rem;
  padding: 1.25rem;
  background: #f8fafc;
  border: 1px solid #e2e8f0;
  border-radius: 10px;
  text-align: center;
}
.install-footer-cta .links {
  margin-top: .5rem;
}
.install-footer-cta .links a {
  color: #334155;
  text-decoration: none;
}
.install-footer-cta .links span { color: #94a3b8; margin: 0 .5rem; }
.install-footer-cta .copyright {
  margin-top: .25rem;
  color: #94a3b8;
  font-size: .9rem;
}

@media (max-width: 768px) {
  .tab-buttons {
    flex-direction: column;
  }

  .tab-button {
    flex-direction: row;
    justify-content: flex-start;
    gap: 1rem;
    min-width: auto;
  }

  .tab-icon {
    font-size: 1.5rem;
  }
}
</style>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const tabButtons = document.querySelectorAll('.tab-button');
  const tabContents = document.querySelectorAll('.tab-content');

  tabButtons.forEach(button => {
    button.addEventListener('click', function() {
      const targetTab = this.getAttribute('data-tab');

      // Remove active class from all buttons and contents
      tabButtons.forEach(btn => btn.classList.remove('active'));
      tabContents.forEach(content => content.classList.remove('active'));

      // Add active class to clicked button and corresponding content
      this.classList.add('active');
      document.getElementById(targetTab).classList.add('active');
    });
  });
});
</script>
