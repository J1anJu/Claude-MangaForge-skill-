# Usage Guide / 使用指南

## Getting Started with New Features / 开始新功能开发

### Example 1: "Continue Reading" Shelf / 示例：继续阅读书架

1. **Planning Session** (triggers `brainstorming`)
   ```
   I want to add a "Continue Reading" shelf feature to the manga reader,
   showing the user's 3-5 most recently read series with cover, title, and current chapter.
   Please help me plan the implementation.
   ```

   ```
   我想为漫画阅读器添加一个"继续阅读"书架功能，
   显示用户最近阅读的3-5个系列，包括封面、标题、当前章节。
   请帮我规划实现方案。
   ```

2. **Expected Output**:
   - Design document (`docs/DESIGN_BRIEF.md`)
   - User journey map
   - MVP scope definition
   - Design system references

3. **Implementation Steps**:
   ```
   /brainstorm
   /plan  (based on design document)
   /dev-story --story "continue-reading-shelf"
   ```

4. **Quality Check**:
   ```
   /code-review
   /ux-review
   ```

### Example 2: Achievement System / 示例：成就系统

1. **Data Model Design** (triggers `gamification`)
   ```
   I need to design a reading achievement system with:
   - First reading badge
   - Consecutive reading streak milestones
   - Total reading time achievements
   - Series completion badges

   Please provide data model and implementation suggestions.
   ```

2. **Expected Output**:
   - TypeScript interface definitions
   - Dexie database schema
   - Component structure
   - XP calculation formulas

### Example 3: Design System Generation / 示例：界面设计

```
Generate a dark theme design system for the manga reader page.
Requirements: comfortable for long reading, night mode support, high contrast.

Please generate complete design specifications.
```

This triggers `manga-design-system`, calling the UI/UX Pro Max engine to create `design-system/MASTER.md`.

## Quick Reference / 速查表

| Task / 任务 | Trigger Phrase / 触发短语 | Skill / 技能 |
|------------|--------------------------|--------------|
| Plan new feature / 规划新功能 | Describe the requirement in natural language | brainstorming |
| Generate design system / 生成设计系统 | "design system" + product description | design-system |
| Add gamification / 添加游戏化 | "achievement", "level", "streak", "XP", "stats" | gamification |
| Reading tracker / 阅读追踪 | "continue reading", "shelf", "history", "updates" | continuity |
| Release / 发布 | "release", "build", "deploy", "publish" | release |
| Testing / 测试 | "test", "QA", "verify", "bug" | qa |

## Complete Development Workflow / 完整开发流程

### Phase 1: Planning / 规划阶段
```
User: I want to add bookmark feature
→ manga-brainstorming
→ Output: docs/DESIGN_BRIEF.md
```

### Phase 2: Design / 设计阶段
```
User: Design the UI for this feature
→ manga-design-system
→ Output: design-system/ (or pages/override.md)
```

### Phase 3: Implementation / 实现阶段
```
User: /dev-story --story "bookmark-feature"
→ Technical Director coordinates
→ UI Programmer implements
→ Agent review
```

### Phase 4: Testing / 测试阶段
```
User: /qa-plan --feature bookmarks
→ QA Specialist creates test plan
→ Execute tests
```

### Phase 5: Release / 发布阶段
```
User: /release-checklist
→ manga-release
→ Verify checklist
→ Deploy
```

## Skill Activation Triggers / 技能触发条件

| Skill / 技能 | Trigger Keywords / 触发关键词 | Does NOT Trigger / 不触发场景 |
|-------------|-----------------------------|------------------------------|
| `brainstorming` | "规划", "设计", "想法", "功能", "feature", "idea", "proposal" | Pure technical implementation questions |
| `design-system` | "设计系统", "UI", "主题", "配色", "风格", "design", "theme", "appearance" | When design system is already specified/clear |
| `gamification` | "成就", "等级", "XP", "连续阅读", "streak", "stat", "stats", "achievement", "level" | Data operations unrelated to statistics |
| `continuity` | "继续阅读", "书架", "历史", "更新", "bookmark", "history", "updates", "tracking" | File system bookmarks only |
| `qa` | "测试", "QA", "验证", "bug", "test", "verify", "quality" | Testing currently working features manually |
| `release` | "发布", "构建", "部署", "build", "release", "deploy", "publish" | Code optimization without version change |

## Reader-Specific Features / 阅读器相关功能

### Reading Experience Enhancements
- **Mode Switching**: UI Programmer + Creative Director
- **Gesture Polish**: See Continuity skill for gesture patterns
- **Two-Page Spread**: Landscape layout, UX review needed
- **Night Mode**: Already covered in design system
- **Reading Stats**: Use Gamification's ReadingProgress model

### Source Script Considerations
- **New Source Format**: Sandbox security rules apply
- **Script Validation**: source-manager/validator integration
- **Error Handling**: Thread-safe catch patterns in workers

## Performance Optimization / 性能优化

### 1. Image Loading / 图片加载
- Use WebP format when browser supports
- Chunk-based preloading for chapters
- Be mindful of memory when using Canvas

### 2. IndexedDB / 数据库
- Batch writes (< 50ms transaction time)
- Create indexes for search queries
- Periodic cleanup of old data

### 3. Web Workers / 工作线程
- Avoid large object serialization
- Worker pooling recommended (manciyuan-series sources)
- Implement timeout controls

## Resources / 相关资源

- [Architecture Documentation](ARCHITECTURE.md) / [架构文档](ARCHITECTURE.md)
- [Project CLAUDE.md](../CLAUDE.md) / [项目说明](../CLAUDE.md)
- [Design System Spec](design-system/MASTER.md) / [设计系统规范](design-system/MASTER.md)

---

**Note**: Skills are auto-triggered based on conversation context. No manual invocation needed - just describe your goals naturally.

**提示**: 技能基于对话上下文自动触发，无需手动调用。只需自然地描述你的需求即可。
