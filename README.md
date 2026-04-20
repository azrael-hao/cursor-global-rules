# Cursor Global Rules

Cursor IDE 全局规则文件，适用于所有项目。

## 规则列表

| 文件 | 类型 | alwaysApply | 说明 |
|------|------|:-----------:|------|
| `adaptive-thinking.mdc` | 规则 | ✅ | 强制双重思考验证：复杂任务必须进行至少2次深度思考分析 |
| `context-compression.mdc` | 规则 | ✅ | 上下文接近容量上限时自动压缩，保持会话连续性 |
| `decision-change-approval.mdc` | 规则 | ✅ | 决策变更或路径切换必须切换 Plan 模式征询用户同意 |
| `remote-process-cleanup.mdc` | 规则 | ✅ | 终止本地进程时必须同时清理远端源头进程 |
| `github-cli-setup.mdc` | Skill | ❌ | GitHub CLI 安装、代理配置与全局规则仓库同步方法 |

## 使用方法

### 方式一：克隆仓库到全局规则目录

```bash
# Windows (Git Bash)
cd ~/.cursor/rules/
git init
git remote add origin https://github.com/azrael-hao/cursor-global-rules.git
git pull origin master

# macOS/Linux
cd ~/.cursor/rules/
git init
git remote add origin https://github.com/azrael-hao/cursor-global-rules.git
git pull origin master
```

### 方式二：手动复制

将 `.mdc` 文件放置到 Cursor 全局规则目录：

- **Windows**: `%USERPROFILE%\.cursor\rules\`
- **macOS/Linux**: `~/.cursor/rules/`

### 代理环境

如果需要通过代理访问 GitHub：

```bash
export HTTPS_PROXY=http://127.0.0.1:7897
export HTTP_PROXY=http://127.0.0.1:7897
```

详细代理配置与 GitHub CLI 使用方法参见 `github-cli-setup.mdc`。

## 规则格式

所有规则文件使用 `.mdc` 格式（Markdown + YAML front-matter）：

```yaml
---
description: 规则简要描述
globs:              # 留空表示不限文件类型
alwaysApply: true   # true=自动生效, false=按需引用
---
```

- `alwaysApply: true` — 对所有项目自动生效的强制规则
- `alwaysApply: false` — 按需引用的 Skill（如工具使用指南）
