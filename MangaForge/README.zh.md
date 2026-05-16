# MangaForge / 漫画锻造工坊

[![许可证: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![版本: 1.0.0](https://img.shields.io/badge/Version-1.0.0-green.svg)](https://github.com/manga-forge/manga-forge)
[![面向: Vue 3 + Vite](https://img.shields.io/badge/For-Vue%203%20%2B%20Vite-brightgreen.svg)](https://vuejs.org)

> 为现代漫画阅读器打造的完整开发赋能系统

## 🌟 核心特性

| 模块 | 能力 | 适用场景 |
|------|------|----------|
| **设计系统** | 预配置深色主题，阅读优化 | UI/UX 界面设计 |
| **游戏化引擎** | 成就、连续阅读、等级、统计 | 用户参与度提升 |
| **连续性追踪** | 阅读历史、系列更新、书签 | 阅读体验管理 |
| **质量保证** | 书源安全、测试策略、发布清单 | 质量控制和发布 |
| **自动化工作流** | TDD、代码审查、调试流程 | 高效开发生命周期 |

## 🚀 快速开始

### 安装

```bash
# 1. 复制配置到项目根目录
cp -r D:/MangaForge/.claude ./

# 2. 重启 Claude Code 会话

# 3. 验证安装
/skill-test
```

### 使用示例

```
为漫画阅读器生成深色主题设计系统，适合长时间阅读
→ 触发设计系统生成

添加阅读成就系统，包括首次阅读、连续天数、系列完成
→ 触发游戏化引擎

实现"继续阅读"书架功能，显示最近阅读的3-5个系列
→ 触发连续性追踪和规划流程
```

## 📦 包含内容

### 技能组 (6个)

```
manga-brainstorming    # 功能规划与需求分析
manga-design-system    # 智能设计系统生成
manga-gamification     # 游戏化机制实现
manga-continuity       # 阅读连续性管理
manga-qa              # 质量保证策略
manga-release         # 多平台发布流程
```

### 智能代理 (4个)

```
creative-director     # 创意总监 - UI/UX设计与游戏化策略
technical-director    # 技术总监 - 架构、安全、性能
qa-specialist         # QA专家 - 测试与发布认证
ui-programmer         # UI程序员 - Vue 3组件实现
```

### 自动化 (5个钩子 + 3个规则)

```
钩子:
- session-start.sh      # 会话开始显示项目状态
- session-stop.sh       # 会话结束归档进度
- validate-commit.sh    # 提交前代码质量检查
- validate-assets.sh    # 设计系统文件验证
- validate-skill-change.sh  # 技能修改提醒

规则:
- sandbox-security         # 书源沙箱安全规范
- vue-components           # Vue 3 组件最佳实践
- gamification-implementation  # 游戏化实现规范
```

### 设计系统

预配置的深色主题设计规范：

- **背景**: 纯黑 (#000000) - OLED 优化
- **主色**: 蓝色 (#3B82F6) - 交互元素
- **强调**: 琥珀色 (#F59E0B) - 关注与收藏
- **文字**: 高对比度 ≥ 4.5:1
- **阅读**: 1.8 行高，18px 字号
- **动画**: 150-300ms 平滑过渡

完整规范见 `design-system/MASTER.md`

## 📚 文档中心

| 文档 | 语言 | 用途 |
|------|------|------|
| [README](README.md) | 中/英 | 项目概览与快速开始 |
| [INSTALL](INSTALL.md) | 中/英 | 详细安装步骤 |
| [docs/USAGE](docs/USAGE.md) | 中/英 | 使用指南与示例 |
| [docs/ARCHITECTURE](docs/ARCHITECTURE.md) | 中/英 | 系统架构详解 |
| [SUMMARY](SUMMARY.md) | 中/英 | 功能总结与集成说明 |

## 🎯 典型工作流

### 新功能开发

```
1. 规划阶段 - 用户描述需求
   → manga-brainstorming
   → 输出: docs/DESIGN_BRIEF.md

2. 设计阶段 - 生成设计系统
   → manga-design-system
   → 输出: design-system/

3. 实现阶段 - 编写实现代码
   → 自动触发技术总监协调
   → UI程序员实施

4. 测试阶段 - 质量验证
   → manga-qa
   → 回归测试清单

5. 发布阶段 - 部署上线
   → manga-release
   → 三平台发布流程
```

## 🔧 技术栈

- **前端**: Vue 3 + TypeScript + Vite 6
- **状态**: Pinia
- **路由**: Vue Router 4
- **PWA**: Vite Plugin PWA
- **跨平台**: Capacitor 7
- **数据**: IndexedDB (Dexie.js)
- **样式**: 预配置 Tailwind CSS (推荐)

## 📄 许可证

MIT License - 自由使用、修改、分发。

---

**MangaForge** - 让漫画阅读器开发更高效、更有趣 ✨
