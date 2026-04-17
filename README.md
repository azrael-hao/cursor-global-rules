# Cursor Global Rules

Cursor IDE 全局规则文件，适用于所有项目。

## 规则列表

| 文件 | 说明 |
|------|------|
| `context-compression.mdc` | 上下文压缩规则 |
| `decision-change-approval.mdc` | 决策变更审批规则 — 任何决策变更或路径切换必须先征询用户同意 |

## 使用方法

将 `.mdc` 文件放置到 Cursor 全局规则目录：

- **Windows**: `%USERPROFILE%\.cursor\rules\`
- **macOS/Linux**: `~/.cursor/rules/`

所有规则均设置 `alwaysApply: true`，对所有项目自动生效。
