# Cursor Global Rules

Cursor IDE 全局规则文件，适用于所有项目。

## 规则统计

- **总数**: 20个核心规则（中文版+英文版）
- **中文版**: 20个文件，位于 `zh/` 目录
- **英文版**: 20个文件，位于根目录
- **总行数**: 约550行（中文） + 约550行（英文） = 1100行
- **精简效果**: 从原4166行精简至550行，减少87%，保持强控制力

## 规则分类

### 核心执行规则（8个）
| 文件 | 说明 |
|------|------|
| `00-CORE-ENFORCEMENT.mdc` | 核心强制执行规则（最高优先级） |
| `zero-speculation-mandatory.mdc` | 零臆想强制执行（thinking自检） |
| `diagnose-before-action.mdc` | 先诊断后行动，禁止盲目修复 |
| `solve-not-suppress.mdc` | 解决问题而非干掉问题 |
| `no-reckless-file-deletion.mdc` | 禁止粗暴删除文件 |
| `plan-approval-mandatory.mdc` | 方案执行前强制确认 |
| `ask-timeout-retry-mandatory.mdc` | AskQuestion超时必须重新提问 |
| `single-turn-resolution.mdc` | 单轮完整解决问题 |

### 用户交互规则（2个）
| 文件 | 说明 |
|------|------|
| `decision-change-approval.mdc` | 所有用户选择必须使用AskQuestion工具 |
| `no-unnecessary-divergence.mdc` | 禁止不必要的思维发散 |

### 核心原则规则（7个）
| 文件 | 说明 |
|------|------|
| `adaptive-thinking.mdc` | 自适应思考深度控制 |
| `no-assumption-core.mdc` | 零臆想原则 |
| `no-inference-verification-required.mdc` | 禁止推断，必须验证 |
| `data-driven-decisions.mdc` | 数据驱动决策 |
| `task-vs-question-identification.mdc` | 任务与问题识别 |
| `no-report-files.mdc` | 禁止生成报告文档 |
| `plan-before-implementation.mdc` | 计划优先原则 |

### 工作流程规则（3个）
| 文件 | 说明 |
|------|------|
| `essential-problem-focus.mdc` | 本质问题聚焦 |
| `rules-self-check.mdc` | Rules自我监督机制 |
| `context-compression.mdc` | 上下文压缩策略 |

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

详细代理配置与 GitHub CLI 使用方法可参考 Skills 仓库中的相关文档。

## 规则格式

所有规则文件使用 `.mdc` 格式（Markdown + YAML front-matter）：

```yaml
---
description: 规则简要描述
globs:              # 留空表示不限文件类型
alwaysApply: true   # true=自动生效
---
```

- `alwaysApply: true` — 对所有项目自动生效的强制规则

## Rules vs Skills 区别

### Rules（行为约束）
- **特征**: 强制性、自动生效（alwaysApply: true）
- **内容**: NEVER/MUST原则、禁止事项、必须检查点
- **格式**: 🚫 NEVER / ✅ MUST / 自检清单
- **位置**: `~/.cursor/rules/*.mdc`

### Skills（方法指南）
- **特征**: 按需触发、非自动生效
- **内容**: 操作步骤、技术指南、HOW TO
- **格式**: 步骤说明、命令示例、操作流程
- **位置**: `~/.cursor/skills/*/SKILL.md`

**示例**：
- ✅ Rule: `diagnose-before-action.mdc` - 禁止未诊断根因就盲目修复（强制约束）
- ✅ Skill: `github-cli-setup` - GitHub CLI安装配置步骤（操作指南）
