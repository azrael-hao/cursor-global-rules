# Cursor Global Rules

优化后的Cursor全局规则集合，所有规则自动在所有项目中生效。

[English Version](./README_en.md)

## 📍 规则位置

**全局Rules**: `~/.cursor/rules/` (Windows: `%USERPROFILE%\.cursor\rules\`)

## 📋 当前生效的Rules（16个）

所有规则配置了`alwaysApply: true`，自动在所有对话中生效。

### 🔴 最高优先级（2个）
1. **00-CORE-ENFORCEMENT.mdc** (102行) - 核心强制执行规则，所有操作必须遵守
2. **zero-speculation-mandatory.mdc** (348行) - 🔴 零臆想强制执行，thinking必须自检

### ⚠️ 核心原则（12个）
3. **adaptive-thinking.mdc** (79行) - 自适应思考深度控制，复杂任务至少思考2次
4. **no-assumption-core.mdc** (69行) - 零臆想原则，禁止假设和猜测
5. **no-inference-verification-required.mdc** (92行) - 禁止推断，必须验证
6. **data-driven-decisions.mdc** (218行) - 数据驱动决策，禁止使用预估值
7. **solve-not-suppress.mdc** (287行) - 🔴 解决问题而非干掉问题
8. **no-reckless-file-deletion.mdc** (380行) - 🔴 禁止粗暴删除文件
9. **plan-approval-mandatory.mdc** (447行) - 🔴 方案执行前强制确认
10. **ask-timeout-retry-mandatory.mdc** (420行) - 🔴 AskQuestion超时必须重新提问（NEW）
11. **task-vs-question-identification.mdc** (76行) - 任务与问题识别
12. **decision-change-approval.mdc** (323行) - 🔴 所有用户选择必须使用AskQuestion工具
13. **no-report-files.mdc** (85行) - 禁止生成报告文档
14. **plan-before-implementation.mdc** (126行) - 计划优先原则，复杂任务必须先规划

### ℹ️ 工作流程（2个）
15. **essential-problem-focus.mdc** (85行) - 本质问题聚焦（对比型问题）
16. **rules-self-check.mdc** (145行) - Rules自我监督机制

## 🎯 Rules vs Skills 区分

### Rules（本仓库）
- **目的**：强制约束和规范
- **触发**：`alwaysApply: true` 自动生效
- **场景**：必须遵守的规则，如编码规范、禁止行为
- **特点**：约束性、强制性、全局性

### Skills（另一仓库）
- **目的**：提供能力和方法
- **触发**：用户@引用 或 description触发条件
- **场景**：完成特定任务的技能
- **特点**：工具性、可选性、任务导向
- **仓库**：https://github.com/azrael-hao/cursor-coding-rules-skills

## 🔄 如何修改Rules

### 修改现有规则
```bash
cd ~/.cursor/rules
# 编辑需要修改的.mdc文件
# 提交到GitHub备份
git add .
git commit -m "Update rules"
export HTTPS_PROXY=http://127.0.0.1:7897
git push origin master
```

### 添加新规则
创建新的`.mdc`文件：
```yaml
---
description: 规则描述
globs:
alwaysApply: true
---

# 规则标题

规则内容...
```

## 📊 优化记录

- **第一轮优化**: 13个 → 9个规则文件（删除工具性内容和测试文件）
- **第二轮优化**: 9个 → 8个规则文件（删除重复摘要文件）
- **第三轮增强**: 8个 → 10个规则文件（新增plan-before-implementation和rules-self-check）
- **第四轮增强**: 10个 → 11个规则文件（新增data-driven-decisions）
- **第五轮增强**: 11个 → 12个规则文件（新增zero-speculation-mandatory）
- **第六轮增强**: 12个 → 13个规则文件（新增solve-not-suppress）
- **第七轮增强**: 13个 → 14个规则文件（新增no-reckless-file-deletion）
- **第八轮增强**: 14个 → 15个规则文件（新增plan-approval-mandatory）
- **第九轮增强**: 15个 → 16个规则文件（新增ask-timeout-retry-mandatory）
- **优化原则**: 
  - 删除了工具性内容（转为Skills）
  - 删除了测试文件和重复摘要
  - 保留了强制性约束规则
  - 新增了工作流程强化规则
  - 新增了数据驱动决策规则
  - 新增了thinking强制自检规则
  - 新增了解决问题方法论规则
  - 新增了文件删除安全规则
  - 新增了方案执行前强制确认规则
  - 新增了AskQuestion超时重试规则
  - 每个原则只保留一个版本

## 🌐 GitHub备份

- **仓库**: https://github.com/azrael-hao/cursor-global-rules
- **分支**: master
- **说明**: 所有Rules文件均有版本控制和历史记录

## ⚠️ 重要提示

1. **自动生效**: 所有规则自动在所有项目中生效，无需手动引用
2. **单一数据源**: 全局rules是唯一的规则来源，项目不需要重复维护
3. **保持同步**: 修改rules后推送到GitHub备份
4. **行数控制**: 建议每个规则文件控制在80行以内最优
5. **无重复**: 每个原则只有一个完整版本，避免维护冗余

## 📝 行数统计

```
00-CORE-ENFORCEMENT.mdc                102 lines ✅
adaptive-thinking.mdc                   79 lines ✅
ask-timeout-retry-mandatory.mdc        420 lines 🔴
data-driven-decisions.mdc              218 lines ⚠️⚠️
decision-change-approval.mdc           323 lines 🔴
essential-problem-focus.mdc             85 lines ✅
no-assumption-core.mdc                  69 lines ✅
no-inference-verification-required.mdc  92 lines ✅
no-reckless-file-deletion.mdc          380 lines 🔴
no-report-files.mdc                     85 lines ✅
plan-approval-mandatory.mdc            447 lines 🔴
plan-before-implementation.mdc         126 lines ⚠️
rules-self-check.mdc                   145 lines ⚠️
solve-not-suppress.mdc                 287 lines ⚠️⚠️
task-vs-question-identification.mdc     76 lines ✅
zero-speculation-mandatory.mdc         348 lines 🔴

总计: 16个文件，3282行
平均: 205.1行/文件
```

**说明**: 
- ✅ 80-100行：最优范围
- ⚠️ 100-150行：可接受范围（复杂规则）
- ⚠️⚠️ 150-300行：特殊规则（包含大量示例和模板）
- 🔴 300+行：CRITICAL级规则（强制自检+详细流程+验证模板+场景分类+多示例）

---

**最后更新**: 2026年5月11日
