<div align="center">

# CoDock

### 本地 Coding Agent 桌面工作台与终端集成中心
### Local Coding Agent Workbench & Unified Terminal Dock

[![Release](https://img.shields.io/github/v/release/juejijianghuaa/CoDock-Release?color=blue&logo=github)](https://github.com/juejijianghuaa/CoDock-Release/releases)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-brightgreen)](https://github.com/juejijianghuaa/CoDock-Release/releases)
[![License](https://img.shields.io/badge/License-MIT-orange.svg)](https://github.com/juejijianghuaa/CoDock-Release/blob/main/LICENSE)

<p align="center">
  <b>一个界面，聚合 9+ 个主流 Coding Agent</b><br/>
  Claude Code · Codex · Gemini CLI · Antigravity (agy) · Grok · Pi · Opencode · CodeBuddy · Cline
</p>

[下载最新版本 (Releases)](https://github.com/juejijianghuaa/CoDock-Release/releases/latest) • [提交 Bug / 需求反馈](https://github.com/juejijianghuaa/CoDock-Release/issues)

</div>

---

## 什么是 CoDock？ / What is CoDock?

**CoDock** 是一个面向专业开发者的本地 Coding Agent 桌面工作台与终端控制台：
- **多 Agent 并行执行**：支持在一个窗口内多 Tab 运行 Claude Code、Codex、Gemini CLI、Antigravity、Grok Build、Pi、Opencode 等，告别杂乱的独立黑窗口。
- **全历史与用量看板**：本地直接解析各 Agent 的原生日志与 SQLite/JSONL 数据，聚合按项目、模型、日期的 Token 用量与成本统计。
- **专为 Coding 打造的终端增强**：基于 xterm.js 与原生 ConPTY 封装，支持滚轮穿透、图片快速粘贴、拖拽文件注入绝对路径、全局快捷键呼出。
- **Markdown Composer 独立浮窗**：专为长提示词编写设计的全功能 Markdown 输入层，支持模板复用、提示词优化与一键投递。
- **手机/平板与局域网协同**：自适应移动端 Web 交互、配对令牌安全门禁与受控只读/可写会话分享。

---
<img width="1744" height="975" alt="33dc2fec-6b9b-4867-a137-d7b075c1698c" src="https://github.com/user-attachments/assets/23a96241-0178-4d6f-8a9a-1ad1ce1409ba" />
<img width="672" height="606" alt="image" src="https://github.com/user-attachments/assets/a4a57c54-08e4-40bc-8d39-c89415f3922f" />

<img width="674" height="612" alt="image" src="https://github.com/user-attachments/assets/1aa90411-2970-4b2b-a087-34c5c331ba17" /><img width="670" height="603" alt="image" src="https://github.com/user-attachments/assets/b6257210-40c0-463c-ab8a-c888d0e51ec1" />


## 快速下载 / Downloads

请前往 [**Latest Release**](https://github.com/juejijianghuaa/CoDock-Release/releases/latest) 下载适用于您操作系统的版本：

| 操作系统 | 推荐安装包 | 备用便携版 / 适用架构 |
| :--- | :--- | :--- |
| **Windows** (Win 10 1809+) | [**CoDock-Setup-x64.exe**](https://github.com/juejijianghuaa/CoDock-Release/releases/latest) *(安装程序，含开始菜单/快捷方式)* | [**codock-windows-amd64.exe**](https://github.com/juejijianghuaa/CoDock-Release/releases/latest) *(单文件绿色版)* |
| **macOS (Apple Silicon)** | [**codock-mac-arm64.dmg**](https://github.com/juejijianghuaa/CoDock-Release/releases/latest) *(适用于 M1/M2/M3/M4 系列)* | 打开 dmg 拖入 Applications |
| **macOS (Intel)** | [**codock-mac-amd64.dmg**](https://github.com/juejijianghuaa/CoDock-Release/releases/latest) *(适用于 Intel 处理器 Mac)* | 打开 dmg 拖入 Applications |
| **Linux (x64)** | [**codock-linux-amd64**](https://github.com/juejijianghuaa/CoDock-Release/releases/latest) *(独立二进制)* | `chmod +x codock-linux-amd64` |

---

## 安装与运行指引 / Installation & Tips

### Windows
1. 下载 `CoDock-Setup-<version>-x64.exe` 并运行安装。
2. Windows 桌面版内置了针对 Windows 10/11 优化的 ConPTY 驱动与无边框自绘标题栏，默认支持最小化到系统托盘运行。
3. 也可以在设置中启用 Windows 资源管理器右键菜单集成（在任意文件夹右键直接启动 CoDock 任务）。

### macOS
1. 下载对应芯片架构的 `.dmg` 文件，双击打开并将 `CoDock.app` 拖入 `Applications`（应用程序）目录。
2. 如遇 macOS 安全机制拦截提示“未验证的开发者”：
   - 可以在“系统设置” -> “隐私与安全性”中点击“仍要打开”；
   - 或在终端中执行解隔离命令：
     ```bash
     xattr -cr /Applications/CoDock.app
     ```

### Linux
1. GUI 桌面版运行需要系统具备 `libwebkit2gtk-4.0` 运行环境（Ubuntu/Debian 执行 `sudo apt install libwebkit2gtk-4.0-37`）。
2. 如需在无 GUI 的远程服务器运行，可使用 `--tags nogui` 构建的 Server 模式：
   ```bash
   ./codock-server -addr :9527
   ```

---

## 安全与网络边界 / Security Notice

1. **本地运行优先**：CoDock 在您本机启动 PTY 会话，所有数据仅落盘在您本地目录（如 `~/.codock/`），不设远程数据中转。
2. **局域网配对门禁**：CoDock 默认开启局域网保护门禁。非本机回环（Loopback）访问时，必须携带配对令牌（可在应用内设置生成），防止局域网不可信设备直接访问控制台。
3. **Agent 自动确认机制**：CoDock 启动各 Agent CLI 时会遵循安全配置（例如跳过重复的权限弹窗）。请在受信任的开发环境中使用，切勿将端口未经认证映射到公开互联网。

---

## 问题反馈与交流 / Feedback & Community

本仓库为 **CoDock 官方发布与用户反馈仓库**。
- 如果您在日常使用中遇到 Bug、界面异常或终端交互问题，请前往 [**Issues -> New Issue**](https://github.com/juejijianghuaa/CoDock-Release/issues) 提交反馈。
- 提交 Issue 时请提供您的操作系统版本、使用的 Agent 种类以及复现步骤。
- 如果 CoDock 对您的日常 Coding 有帮助，欢迎给本仓库点一个 **Star ⭐️** 支持作者持续更新！
