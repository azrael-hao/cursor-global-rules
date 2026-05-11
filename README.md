# Cursor Global Rules

优化后的Cursor全局规则集合，所有规则自动在所有项目中生效。

[English Version](./README_en.md)

## 📍 规则位置

**全局Rules**: `~/.cursor/rules/` (Windows: `%USERPROFILE%\.cursor\rules\`)

## 📊 规则统计

### 中文规则（17个）
- 总行数：**521行**
- 平均行/文件：**30.6行**
- 最大规则：`zero-speculation-mandatory.mdc`（70行）
- 最小规则：`essential-problem-focus.mdc`（17行）

### 英文规则（17个）
- 位置：`~/.cursor/rules/en/`
- 总行数：**521行**
- 与中文版完全对应

### 精简效果
- 原始总行数：**4,166行**
- 精简后：**521行**
- **减少87.5%**，保持强效控制

## 📋 当前生效的Rules（17个）

所有规则配置了`alwaysApply: true`，自动在所有对话中生效。

### 🔴 核心执行规则（7个 - CRITICAL）
1. **00-CORE-ENFORCEMENT.mdc** (49行) - 核心强制执行规则，所有操作必须遵守
2. **zero-speculation-mandatory.mdc** (70行) - 零臆想强制执行，thinking必须自检
3. **solve-not-suppress.mdc** (33行) - 解决问题而非干掉问题
4. **no-reckless-file-deletion.mdc** (40行) - 禁止粗暴删除文件
5. **plan-approval-mandatory.mdc** (38行) - 方案执行前强制确认
6. **ask-timeout-retry-mandatory.mdc** (31行) - AskQuestion超时必须重新提问
7. **no-unnecessary-divergence.mdc** (37行) - 禁止不必要的思维发散，聚焦用户实际问题

### 🔴 用户交互规则（1个 - CRITICAL）
8. **decision-change-approval.mdc** (34行) - 所有用户选择必须使用AskQuestion工具

### ⚠️ 核心原则规则（7个）
9. **adaptive-thinking.mdc** (23行) - 自适应思考深度控制
10. **no-assumption-core.mdc** (22行) - 零臆想原则
11. **no-inference-verification-required.mdc** (21行) - 禁止推断，必须验证
12. **data-driven-decisions.mdc** (23行) - 数据驱动决策
13. **task-vs-question-identification.mdc** (18行) - 任务与问题识别
14. **no-report-files.mdc** (20行) - 禁止生成报告文档
15. **plan-before-implementation.mdc** (21行) - 计划优先原则

### ℹ️ 工作流程规则（2个）
16. **essential-problem-focus.mdc** (17行) - 本质问题聚焦
17. **rules-self-check.mdc** (24行) - Rules自我监督机制

## 🌍 国际化支持

英文版规则位于 `~/.cursor/rules/en/` 目录，文件名与中文版保持一致。

## 🎯 使用指南

### 规则自动加载
所有规则通过`alwaysApply: true`自动在所有对话中生效，无需手动引用。

### 核心原则速记
- 🔴 零臆想：先验证，后执行
- 🔴 强制Ask：所有用户交互必须用AskQuestion工具
- 🔴 方案确认：制定方案后必须征求用户同意才能执行
- 🔴 解决问题：禁止掩盖、删除、忽略错误
- 🔴 聚焦问题：禁止不必要的发散，直达目标

## 📈 优化记录

### 第十一轮精简（2026-05）
- **重大精简**：从4166行精简到521行，减少87.5%
- **策略**：删除冗余示例，合并重复内容，保留核心强制要求
- **效果**：保持强效控制，提升加载和理解效率
- **国际化**：创建17个英文版规则，统一放在en/文件夹
- **结构优化**：
  - 中文规则：`~/.cursor/rules/*.mdc`
  - 英文规则：`~/.cursor/rules/en/*.mdc`
- **精简对比**：
  - 00-CORE-ENFORCEMENT: 388行 → 49行（减少87.4%）
  - zero-speculation-mandatory: 316行 → 70行（减少77.8%）
  - no-unnecessary-divergence: 884行 → 37行（减少95.8%）
  - decision-change-approval: 323行 → 34行（减少89.5%）
  - 其他规则平均精简90%+

### 第十轮增强（2026-05）
- 新增规则：`no-unnecessary-divergence.mdc` - 思维聚焦规则
- 在核心规则中新增"思维聚焦"要求和检查项

### 第九轮增强（2026-05）
- 在核心规则中新增"上下文压缩"要求，明确16个核心规则永不压缩
- 更新context-compression技能，列出所有16个规则为不可压缩内容

### 第八轮增强（2026-05）
- 新增规则：`ask-timeout-retry-mandatory.mdc` - AskQuestion超时处理规则
- 在核心规则和decision-change-approval中强化AskQuestion强制使用要求

### 第七轮增强（2026-05）
- 新增规则：`plan-approval-mandatory.mdc` - 方案执行前强制确认规则
- 在核心规则中新增"方案执行"检查项

### 第六轮增强（2026-05）
- 新增规则：
  1. `solve-not-suppress.mdc` - 解决问题而非干掉问题规则
  2. `no-reckless-file-deletion.mdc` - 禁止粗暴删除文件规则

## 📚 相关资源

- **Skills仓库**: https://github.com/azrael-hao/cursor-coding-rules-skills
- **最佳实践**: 查看各规则文件中的示例和说明
- **问题反馈**: 通过GitHub Issues反馈

## ⚠️ 重要提示

这些规则是AI行为的强制约束，违反任何规则都视为严重错误。AI必须在每次操作前在thinking中进行自检。
