# Cursor Global Rules

Global rule files for Cursor IDE, applicable to all projects.

## Statistics

- **Total**: 20 core rules (Chinese + English versions)
- **Chinese**: 20 files in `zh/` directory
- **English**: 20 files in root directory
- **Total Lines**: ~550 (Chinese) + ~550 (English) = 1100 lines
- **Streamlining**: Reduced from 4166 to 550 lines (87% reduction) while maintaining strong control

## Rule Categories

### Core Execution Rules (8)
| File | Description |
|------|-------------|
| `00-CORE-ENFORCEMENT.mdc` | Core enforcement rules (highest priority) |
| `zero-speculation-mandatory.mdc` | Zero speculation enforcement (thinking self-check) |
| `diagnose-before-action.mdc` | Diagnose first, act later - no blind fixes |
| `solve-not-suppress.mdc` | Solve problems, don't suppress them |
| `no-reckless-file-deletion.mdc` | Prohibit reckless file deletion |
| `plan-approval-mandatory.mdc` | Mandatory plan confirmation before execution |
| `ask-timeout-retry-mandatory.mdc` | Must retry AskQuestion on timeout |
| `single-turn-resolution.mdc` | Complete resolution in single turn |

### User Interaction Rules (2)
| File | Description |
|------|-------------|
| `decision-change-approval.mdc` | All user choices must use AskQuestion tool |
| `no-unnecessary-divergence.mdc` | Prohibit unnecessary thought divergence |

### Core Principle Rules (7)
| File | Description |
|------|-------------|
| `adaptive-thinking.mdc` | Adaptive thinking depth control |
| `no-assumption-core.mdc` | Zero assumption principle |
| `no-inference-verification-required.mdc` | No inference, must verify |
| `data-driven-decisions.mdc` | Data-driven decision making |
| `task-vs-question-identification.mdc` | Task vs question identification |
| `no-report-files.mdc` | Prohibit generating report documents |
| `plan-before-implementation.mdc` | Plan before implementation |

### Workflow Rules (3)
| File | Description |
|------|-------------|
| `essential-problem-focus.mdc` | Focus on essential problems |
| `rules-self-check.mdc` | Rules self-check mechanism |
| `context-compression.mdc` | Context compression strategy |

## Usage

### Method 1: Clone Repository to Global Rules Directory

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

### Method 2: Manual Copy

Place `.mdc` files in Cursor global rules directory:

- **Windows**: `%USERPROFILE%\.cursor\rules\`
- **macOS/Linux**: `~/.cursor/rules/`

### Proxy Environment

If you need to access GitHub through a proxy:

```bash
export HTTPS_PROXY=http://127.0.0.1:7897
export HTTP_PROXY=http://127.0.0.1:7897
```

For detailed proxy configuration and GitHub CLI usage, refer to Skills repository documentation.

## Rule Format

All rule files use `.mdc` format (Markdown + YAML front-matter):

```yaml
---
description: Brief rule description
globs:              # Empty = no file type restriction
alwaysApply: true   # true = auto-enabled
---
```

- `alwaysApply: true` — Mandatory rules automatically enforced for all projects

## Rules vs Skills

### Rules (Behavioral Constraints)
- **Characteristics**: Mandatory, auto-enabled (alwaysApply: true)
- **Content**: NEVER/MUST principles, prohibitions, mandatory checks
- **Format**: 🚫 NEVER / ✅ MUST / Self-check lists
- **Location**: `~/.cursor/rules/*.mdc`

### Skills (Method Guides)
- **Characteristics**: On-demand, not auto-enabled
- **Content**: Operation steps, technical guides, HOW TO
- **Format**: Step-by-step instructions, command examples
- **Location**: `~/.cursor/skills/*/SKILL.md`

**Examples**:
- ✅ Rule: `diagnose-before-action.mdc` - Prohibit blind fixes without diagnosing root cause (mandatory constraint)
- ✅ Skill: `github-cli-setup` - GitHub CLI installation and configuration steps (operation guide)
