# MangaForge Architecture / 架构文档

## System Overview / 系统概述

**MangaForge** is an integrated development empowerment suite designed specifically for modern manga reader applications. It orchestrates multiple automation layers to provide end-to-end support from initial concept to deployed application.

## Component Architecture / 组件架构

```
┌────────────────────────────────────────────────────────────┐
│              Claude Code Session / 会话                      │
├────────────────────────────────────────────────────────────┤
│  Skills Layer (Auto-triggered / 自动触发)                     │
│  ┌─────────────────┐ ┌─────────────────┐                   │
│  │ brainstorming   │ │ design-system   │                   │
│  └─────────────────┘ └─────────────────┘                   │
│  ┌─────────────────┐ ┌─────────────────┐                   │
│  │ gamification    │ │ continuity      │                   │
│  └─────────────────┘ └─────────────────┘                   │
│  ┌─────────────────┐ ┌─────────────────┐                   │
│  │ qa              │ │ release         │                   │
│  └─────────────────┘ └─────────────────┘                   │
├────────────────────────────────────────────────────────────┤
│  Agent Layer (On-demand / 按需调用)                          │
│  ┌─────────────────┐ ┌─────────────────┐                   │
│  │ creative-director│ │ technical-director│                  │
│  └─────────────────┘ └─────────────────┘                   │
│  ┌─────────────────┐ ┌─────────────────┐                   │
│  │ qa-specialist   │ │ ui-programmer    │                   │
│  └─────────────────┘ └─────────────────┘                   │
├────────────────────────────────────────────────────────────┤
│  Rules & Hooks (Automation / 自动化)                         │
│  • sandbox-security     • vue-components                   │
│  • gamification-implementation                              │
│  • validate-commit.sh   • validate-assets.sh              │
│  • session-start.sh     • session-stop.sh                 │
├────────────────────────────────────────────────────────────┤
│  External Integrations / 外部集成                             │
│  • UI/UX Pro Max Engine (Design Generation)                │
│  • Superpowers Workflow (TDD, Review)                      │
└────────────────────────────────────────────────────────────┘
```

## Skill Deep Dive / 技能详解

### 1. manga-brainstorming (Planning Phase)

**Triggers on**: Feature requests, requirement gathering, architecture discussions

**Workflow**:
1. **Clarify Objectives** - Ask about business goals and user personas
2. **Multi-Domain Exploration** - Simultaneously evaluate UI, gamification, technical feasibility
3. **Chunked Design Output** - Break design into digestible sections
4. **Save Design Document** - Create `docs/DESIGN_BRIEF.md` for reference

**Expected Output Structure**:
```markdown
# Design Brief: [Feature Name]

## Problem Statement
What user problem does this solve?

## Target Personas
- Casual reader: ...
- Power user: ...

## User Journey
1. Land on home → seeContinueReading shelf
2. Tap series → resume to last page
3. ...

## MVP Scope / 最小可行范围
- Core: ...
- Out of scope for v1: ...

## Design System Reference
- Base: design-system/MASTER.md
- Custom additions: ...
```

### 2. manga-design-system (Design Phase)

**Triggers on**: "design system", "theme", "UI", "colors", "appearance"

**Integration**: Directly invokes UI/UX Pro Max Python engine

**Process**:
1. Classify product type → Maps to "Content Platform" + "Dark Mode"
2. Generate design system → `search.py ... --design-system`
3. Persist to `design-system/MASTER.md` (and optional `pages/*.md` overrides)
4. Guide component development using generated specs

**Auto-Applied Configuration**:
- **Pattern**: Content-first + Navigation-dense
- **Style**: Dark Mode (OLED optimized) + Minimalism
- **Color Scheme**: Pure black (#000000), Blue primary (#3B82F6), Amber accent (#F59E0B)
- **Typography**: System fonts for UI, 18px/1.8 for reading content
- **Effects**: Smooth transitions (250ms), subtle micro-interactions, no reading disruption

### 3. manga-gamification (Engagement Engine)

**Triggers on**: "achievement", "streak", "level", "XP", "stats", "gamification"

**Core Systems**:
- **Reading Streak**: Track consecutive days with reading activity
- **Achievements**: Milestone-based badge system
- **Collections**: Series completion tracking
- **Levels & XP**: Progression system with exponential growth curve

**Data Model Example**:
```typescript
interface ReadingProgress {
  userId: string;
  chaptersCompleted: number;
  pagesRead: number;
  readingMinutes: number;
  lastActivity: Date;
  currentStreak: number;
  longestStreak: number;
}

interface Achievement {
  id: string;
  title: string;
  description: string;
  icon: string;
  condition: AchievementCondition;
  unlockedAt?: Date;
  progress?: number; // 0-100 for progressive achievements
}

interface StreakDay {
  date: string; // YYYY-MM-DD format
  chaptersRead: number;
  goalMet: boolean;
}
```

**Storage**: IndexedDB via Dexie with proper indexing

### 4. manga-continuity (Reading Continuity)

**Triggers on**: "continue reading", "bookmark", "history", "updates", "tracking"

**Features**:
- **Bookmark System**: Per-chapter and per-series position tracking
- **Auto-Resume**: Jump to exact page where user left off
- **Reading History**: Complete timestamped log of reading activity
- **Series Tracking**: Monitor ongoing series for new chapters
- **Update Detection**: Compare local chapter count with remote source

**Sync Strategy**: Local IndexedDB with optional cloud sync extension

### 5. manga-qa (Quality Assurance)

**Triggers on**: "test", "QA", "verify", "bug", "quality check"

**Test Categories**:
- **Source Script Tests**: Script loading, parsing, error handling
- **Reading Mode Tests**: Scroll, paged, webtoon, auto mode transitions
- **PWA Tests**: Installation, offline support, service worker
- **Cross-Platform**: Android (Capacitor), iOS, Web browser

**Workflow**: Superpowers TDD methodology
1. Write failing test first
2. Implement minimal code to pass
3. Refactor while keeping green
4. Commit with proper message

### 6. manga-release (Deployment Pipeline)

**Triggers on**: "release", "build", "deploy", "publish", "version"

**Three-Platform Synchronization**:
- **Web**: `pnpm build` → PWA assets → Deploy to hosting
- **Android**: `pnpm build:android` → Capacitor sync → Build APK/AAB
- **iOS**: `pnpm build:ios` → Xcode project → Build IPA

**Versioning**: Semantic Versioning shared across all three platforms

---

## Agent Team / 代理团队

### Creative Director (`creative-director`)
- **Focus**: Design system consistency, gamification strategy, reading UX
- **Scope**: `design-system/`, UI components, gamification UI
- **Model**: Opus (for creative insights)

### Technical Director (`technical-director`)
- **Focus**: System architecture, performance, security, cross-platform
- **Scope**: All `packages/`, `capacitor/`, infrastructure
- **Model**: Opus (for architectural decisions)

### QA Specialist (`qa-specialist`)
- **Focus**: Test planning, bug triage, release certification
- **Scope**: `tests/`, release validation, user feedback
- **Model**: Sonnet

### UI Programmer (`ui-programmer`)
- **Focus**: Vue 3 components, Pinia stores, PWA integration
- **Scope**: `packages/web/src/`
- **Model**: Sonnet

**Collaboration Model**:
- Vertical delegation: Directors → Leads → Specialists
- Horizontal consultation: Peer agents can consult but cannot bind decisions
- Conflict resolution: Escalate to shared parent director
- Change coordination: Technical Director manages cross-department updates

---

## Path-Scoped Rules / 路径规则

### sandbox-security.md
**Applies to**: `packages/sandbox/src/**`

**Mandatory**:
- No DOM access (`window`, `document`, `localStorage`)
- All `fetch` calls must use `safeFetch(domain, ...)`
- Only exposed APIs: `fetch`, `cheerio`, `crypto`, `utils`
- No `eval()`, `new Function()`, or dynamic code execution
- All worker errors must be caught and serialized

**Violations** → Build/commit blocked

### vue-components.md
**Applies to**: `packages/web/src/**/*.vue`

**Mandatory**:
- Composition API with `<script setup>`
- Props must have TypeScript types
- No direct store mutations in components → use store actions
- ARIA labels on interactive elements without text content
- Keyboard navigation support

**Violations** → Lint error

### gamification-implementation.md
**Applies to**: `packages/web/src/stores/**/*gamification*`

**Mandatory**:
- Achievement unlocks must be atomic transactions
- Streak calculation based on calendar days, not consecutive reading
- XP curve uses exponential formula: `base × multiplier^(level-1)`
- Frequent updates must be debounced (< 5ms per operation)
- All achievements must have unique IDs

**Violations** → Code review fail

---

## Hook System / 钩子系统

| Hook / 钩子 | Trigger / 触发 | Purpose / 作用 |
|-------------|---------------|----------------|
| `session-start.sh` | Session open | Display current branch, recent commits, available skills |
| `session-stop.sh` | Session close | Archive `active.md`, record git activity |
| `validate-commit.sh` | `git commit` | Check for unreferenced TODOs, hardcoded secrets |
| `validate-push.sh` | `git push` | Warn about protected branches |
| `validate-assets.sh` | Write/Edit | Validate design-system structure |
| `validate-skill-change.sh` | Edit `.claude/skills/` | Prompt to run `/skill-test` |

**Hook Location**: `.claude/hooks/`
**Registration**: `settings.json` → `hooks.preToolUse` / `hooks.postToolUse`

All hooks exit with `0` when conditions not met (graceful no-op).

---

## Integration with Upstream Packages / 上游集成

MangaForge is **not a fork** of upstream packages. It is an **integration layer**:

| What MangaForge Provides | How It Integrates |
|--------------------------|-------------------|
| Domain-specific workflow | Binds skills to manga reader context |
| Pre-configured agents | Custom definitions, not from upstream |
| Automation & rules | Original hooks and path rules |
| Design system template | Generated via UI/UX Pro Max engine |
| Release process | Custom for Web/Android/iOS triad |

**Required Upstream Installations**:
- **Superpowers**: Provides TDD, code review, systematic debugging skills
- **UI/UX Pro Max**: Provides design intelligence engine (`search.py`)
- **(Optional) Webnovel Writer**: Additional continuity patterns

**Game Studios**: Agent architecture concepts adapted, but implemented natively.

---

## Extending MangaForge / 扩展指南

### Adding a New Skill / 添加新技能

```bash
mkdir .claude/skills/my-skill-name
```

Create `SKILL.md`:

```markdown
---
name: my-skill-name
description: One-line description of what this skill does
---

# Full Skill Documentation

## Trigger
When this skill activates...

## Purpose
What it accomplishes...

## Process
Step-by-step procedure...
```

### Modifying Agents / 修改代理

Edit `.claude/agents/[agent-name].md` frontmatter:

```yaml
---
name: my-agent
model: sonnet  # or "opus", "haiku", "inherit"
description: Updated description
---
```

Change `scope` or `responsibilities` in the body as needed.

### Custom Hooks / 自定义钩子

1. Create script in `.claude/hooks/`
2. Make executable: `chmod +x .claude/hooks/myscript.sh`
3. Register in `settings.json`:
```json
{
  "hooks": {
    "preToolUse": [".claude/hooks/myscript.sh", ...],
    "postToolUse": [".claude/hooks/another.sh", ...]
  }
}
```

---

## Maintenance / 维护

### Updating Design System / 更新设计系统

```bash
# Backup existing
cp design-system/MASTER.md design-system/MASTER.md.bak

# Generate new
python3 .claude/skills/ui-ux-pro-max/scripts/search.py \
  "manga reader app" \
  --design-system \
  --persist \
  -p "MangaForge"

# Manually merge changes you want to keep from backup
```

### Checking Health / 健康检查

```bash
# Skill validation
/skill-test

# Hook status
ls -la .claude/hooks/*.sh

# Configuration syntax
python3 -m json.tool .claude/settings.json
```

---

## License / 许可证

MIT License - Free to use, modify, and distribute.

MangaForge is an **independent integration project**, not affiliated with or endorsed by Anthropic, Superpowers, UI/UX Pro Max, Game Studios, or Webnovel Writer projects.

---

**Last Updated**: 2026-05-16
**Version**: 1.0.0
**Location**: `D:/MangaForge`
