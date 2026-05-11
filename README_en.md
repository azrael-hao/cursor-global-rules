# Cursor Global Rules

Optimized Cursor global rules set, all rules automatically apply to all projects.

[中文版本](./README.md)

## 📍 Rules Location

**Global Rules**: `~/.cursor/rules/` (Windows: `%USERPROFILE%\.cursor\rules\`)

## 📊 Statistics

### Chinese Rules (17)
- Total Lines: **521 lines**
- Average Lines/File: **30.6 lines**
- Largest Rule: `zero-speculation-mandatory.mdc` (70 lines)
- Smallest Rule: `essential-problem-focus.mdc` (17 lines)

### English Rules (17)
- Location: `~/.cursor/rules/en/`
- Total Lines: **521 lines**
- Fully corresponds to Chinese version

### Streamlining Effect
- Original Total Lines: **4,166 lines**
- After Streamlining: **521 lines**
- **87.5% Reduction**, maintaining strong control

## 📋 Current Active Rules (17)

All rules configured with `alwaysApply: true`, automatically active in all conversations.

### 🔴 Core Execution Rules (7 - CRITICAL)
1. **00-CORE-ENFORCEMENT.mdc** (49 lines) - Core enforcement rules, must follow for all operations
2. **zero-speculation-mandatory.mdc** (70 lines) - Zero speculation enforcement, thinking must self-check
3. **solve-not-suppress.mdc** (33 lines) - Solve problems, don't suppress them
4. **no-reckless-file-deletion.mdc** (40 lines) - No reckless file deletion
5. **plan-approval-mandatory.mdc** (38 lines) - Mandatory approval before plan execution
6. **ask-timeout-retry-mandatory.mdc** (31 lines) - Must re-ask after AskQuestion timeout
7. **no-unnecessary-divergence.mdc** (37 lines) - No unnecessary divergence, focus on user's actual problem

### 🔴 User Interaction Rules (1 - CRITICAL)
8. **decision-change-approval.mdc** (34 lines) - All user selections must use AskQuestion tool

### ⚠️ Core Principle Rules (7)
9. **adaptive-thinking.mdc** (23 lines) - Adaptive thinking depth control
10. **no-assumption-core.mdc** (22 lines) - No assumption principle
11. **no-inference-verification-required.mdc** (21 lines) - No inference, must verify
12. **data-driven-decisions.mdc** (23 lines) - Data-driven decisions
13. **task-vs-question-identification.mdc** (18 lines) - Task vs question identification
14. **no-report-files.mdc** (20 lines) - No report file generation
15. **plan-before-implementation.mdc** (21 lines) - Plan before implementation principle

### ℹ️ Workflow Rules (2)
16. **essential-problem-focus.mdc** (17 lines) - Essential problem focus
17. **rules-self-check.mdc** (24 lines) - Rules self-supervision mechanism

## 🌍 Internationalization Support

English version rules are located in `~/.cursor/rules/en/` directory, with filenames matching the Chinese version.

## 🎯 Usage Guide

### Automatic Rule Loading
All rules automatically apply in all conversations via `alwaysApply: true`, no manual reference needed.

### Core Principles Quick Reference
- 🔴 Zero Speculation: Verify first, execute later
- 🔴 Mandatory Ask: All user interactions must use AskQuestion tool
- 🔴 Plan Approval: Must request user approval after creating plan before execution
- 🔴 Solve Problems: Never hide, delete, or ignore errors
- 🔴 Stay Focused: No unnecessary divergence, go directly to goal

## 📈 Optimization History

### 11th Round Streamlining (2026-05)
- **Major Streamlining**: From 4166 lines to 521 lines, 87.5% reduction
- **Strategy**: Remove redundant examples, merge duplicate content, keep core mandatory requirements
- **Effect**: Maintain strong control, improve loading and comprehension efficiency
- **Internationalization**: Created 17 English version rules, unified in en/ folder
- **Structure Optimization**:
  - Chinese rules: `~/.cursor/rules/*.mdc`
  - English rules: `~/.cursor/rules/en/*.mdc`
- **Streamlining Comparison**:
  - 00-CORE-ENFORCEMENT: 388 lines → 49 lines (87.4% reduction)
  - zero-speculation-mandatory: 316 lines → 70 lines (77.8% reduction)
  - no-unnecessary-divergence: 884 lines → 37 lines (95.8% reduction)
  - decision-change-approval: 323 lines → 34 lines (89.5% reduction)
  - Other rules average 90%+ reduction

## 📚 Related Resources

- **Skills Repository**: https://github.com/azrael-hao/cursor-coding-rules-skills
- **Best Practices**: See examples and explanations in each rule file
- **Issue Feedback**: Provide feedback via GitHub Issues

## ⚠️ Important Notice

These rules are mandatory constraints on AI behavior. Violating any rule is considered a serious error. AI must perform self-checks in thinking before each operation.
