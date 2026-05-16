# Installation Guide / 安装指南

## Prerequisites / 前置要求

- **Claude Code** installed and configured
- **Node.js 18+** with **pnpm** package manager
- **Python 3.10+** (for design system generation)

## Installation Steps / 安装步骤

### 1. Copy Configuration / 复制配置

```bash
# From your manga reader project root / 在漫画阅读器项目根目录执行
cp -r D:/MangaForge/.claude ./
```

This creates the `.claude/` directory with:
- `settings.json` - Skill configuration
- `agents/` - 4 agent definitions
- `skills/` - 6 core skills
- `hooks/` - 5 automation scripts
- `rules/` - 3 path-scoped rules

### 2. Install Additional Dependencies / 安装依赖技能包

MangaForge integrates with existing skill ecosystem. Install these recommended packages:

#### Superpowers (Workflow Automation)
```bash
# Through Claude Marketplace
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```

Reference: [Superpowers Installation](https://github.com/obra/superpowers)

#### UI/UX Pro Max (Design Intelligence)
```bash
npm install -g uipro-cli
uipro init --ai claude
```

This provides the design system generation engine.

#### Webnovel Writer (Optional - Continuity Features)
```bash
# Via Marketplace (recommended)
/plugin marketplace add lingfengQAQ/webnovel-writer --scope project
/plugin install webnovel-writer@webnovel-writer-marketplace --scope project
```

Note: Game Studios agent architecture is built into MangaForge natively.

### 3. Restart Claude Code / 重启会话

Close and reopen your Claude Code session to load the new configuration.

### 4. Verify Installation / 验证安装

```bash
/skill-test
```

Expected output:
```
✓ manga-brainstorming (PASS)
✓ manga-design-system (PASS)
✓ manga-gamification (PASS)
✓ manga-continuity (PASS)
✓ manga-qa (PASS)
✓ manga-release (PASS)
```

## Optional: Generate Initial Design System / 生成初始设计系统

On first use, generate the design system:

```bash
# Uses UI/UX Pro Max engine
python3 .claude/skills/ui-ux-pro-max/scripts/search.py \
  "manga reading app dark mode" \
  --design-system \
  --persist \
  -p "MangaReader"
```

This creates `design-system/MASTER.md` with complete design specifications for your manga reader.

## Troubleshooting / 故障排除

### Skills Not Triggering
- Check `.claude/settings.json` for syntax errors
- Ensure skills are listed in `skills.autoload`
- Restart the session (settings load on startup)

### Python Script Not Found
Verify Python is in PATH:
```bash
python3 --version
```

Windows: You may need to add Python to PATH or configure the full path in settings.

### Hooks Not Executing
Set execute permissions:
```bash
chmod +x .claude/hooks/*.sh
```

On Windows with Git Bash, this is usually automatic.

### Reset Configuration / 重置配置

If you need to start over:
```bash
rm -rf .claude
# Then recopy from D:/MangaForge/
```

Uninstall upstream packages through their respective marketplaces or by removing their directories.

## Uninstallation / 卸载

Remove MangaForge from your project:

```bash
rm -rf .claude
```

Note: Upstream packages (Superpowers, UI/UX Pro Max, etc.) must be uninstalled separately.

