# MangaReader Design System

为漫画阅读器优化的视觉规范，专为长时间阅读设计。

## PATTERN: Content-First + Navigation-Dense

**适用场景**: 内容消费型应用，高频导航元素，设置便捷访问

**布局结构**:
```
+-------------------------------------------------+
|  ← 书架 | 发现 | 搜索 | 更多...          [用户] |
+-------------------------------------------------+
|                                                 |
|  [搜索栏]                                       |
|                                                 |
+-------------------------------------------------+
|                                                 |
|  📚 继续阅读                                     |
|  ┌────┐ ┌────┐ ┌────┐                         |
|  │ cover1 │ cover2 │ cover3 │                 |
|  └────┘ └────┘ └────┘                         |
|                                                 |
|  🎯 推荐作品                                     |
|  ┌────┐ ┌────┐ ┌────┐ ┌────┐                  |
|  │ cover4 │ cover5 │ cover6 │ cover7 │        |
|  └────┘ └────┘ └────┘ └────┘                  |
|                                                 |
|  ⚙️ 设置、主题、书源管理...                     |
|                                                 |
+-------------------------------------------------+
```

## STYLE: Dark Mode (OLED) + Minimalism

**核心理念**:
- 真黑色背景 (`#000000`) 减少 OLED 耗电
- 最大对比度提高文字可读性
- 减少视觉干扰，聚焦内容
- 细微的微交互增强反馈

**最佳效果**: 阅读类、媒体消费、夜间使用场景

## COLORS

### 主色调

| 用途 | 颜色 | 说明 | 对比度 |
|------|------|------|--------|
| 背景（OLED） | `#000000` | 纯黑背景 | 21:1 |
| 背景（深灰） | `#121212` | 卡片背景 | 15:1 |
| 表面（Elevated） | `#1E1E1E` | 浮动元素 | 12:1 |
| 边框/分割线 | `#2D2D2D` | 1px 边框 | 8:1 |

### 主色（交互元素）

| 用途 | 颜色 | 说明 |
|------|------|------|
| Primary | `#3B82F6` | 标准蓝色，按钮、链接 |
| Primary Hover | `#2563EB` | 加深 15% |
| Primary Active | `#1D4ED8` | 加深 30% |
| Secondary | `#8B5CF6` | 紫色，可选操作 |
| Accent | `#F59E0B` | 琥珀色，关注、收藏 |

### 语义色

| 用途 | 颜色 | 说明 |
|------|------|------|
| Success | `#10B981` | 绿色 |
| Warning | `#F59E0B` | 黄色/琥珀 |
| Error | `#EF4444` | 红色 |
| Info | `#3B82F6` | 蓝色 |

### 文字

| 元素 | 颜色 | 对比度 | 字号（示例） |
|------|------|--------|-------------|
| 标题 H1 | `#FFFFFF` | 21:1 | 28px |
| 标题 H2 | `#F3F4F6` | 18:1 | 24px |
| 正文 | `#E5E7EB` | 15:1 | 16px |
| 辅助文字 | `#9CA3AF` | 6:1 | 14px |
| 禁用 | `#6B7280` | 4.5:1 | 14px |

## TYPOGRAPHY

### 字体栈

```css
/* UI 字体 - 清晰、现代 */
font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
             "Helvetica Neue", Arial, sans-serif;

/* 阅读字体 - 舒适、易读 */
font-family: "Noto Sans SC", "PingFang SC", "Microsoft YaHei",
             "Source Han Sans CN", sans-serif;
```

### 字号比例

| 标签 | 像素 | rem (base=16) | 行高 |
|------|------|---------------|------|
| H1 | 28px | 1.75rem | 1.3 |
| H2 | 24px | 1.5rem | 1.4 |
| H3 | 20px | 1.25rem | 1.4 |
| H4 | 18px | 1.125rem | 1.5 |
| Body | 16px | 1rem | 1.6 |
| Small | 14px | 0.875rem | 1.5 |
| Caption | 12px | 0.75rem | 1.4 |

**阅读视图优选配置**:
```css
.reader-content {
  font-size: 18px;
  line-height: 1.8;
  max-width: 800px;
  letter-spacing: 0.02em;
}
```

## SPACING

### 间距比例

```css
:root {
  --space-1: 4px;   /* 0.25rem */
  --space-2: 8px;   /* 0.5rem */
  --space-3: 12px;  /* 0.75rem */
  --space-4: 16px;  /* 1rem */
  --space-5: 24px;  /* 1.5rem */
  --space-6: 32px;  /* 2rem */
  --space-8: 48px;  /* 3rem */
  --space-10: 64px; /* 4rem */
  --space-12: 96px; /* 6rem */
}
```

### 组件间距

| 组件 | 内边距 | 间隙 |
|------|--------|------|
| 按钮 | 12px 24px | N/A |
| 卡片 | 16px | 子元素 12px |
| 列表项 | 16px | 1px 分割线 |
| 导航栏 | 12px 16px | 菜单项 8px |

## RADIUS

```css
:root {
  --radius-sm: 4px;   /* 小标签、徽章 */
  --radius-md: 8px;   /* 卡片、按钮 */
  --radius-lg: 12px;  /* 模态框、浮层 */
  --radius-full: 9999px; /* 圆形头像、药丸形状 */
}
```

## SHADOWS

```css
/* 浅色背景上的轻微阴影 */
--shadow-sm: 0 1px 2px rgba(0, 0, 0, 0.5);
--shadow-md: 0 4px 6px rgba(0, 0, 0, 0.6);
--shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.7);
--shadow-xl: 0 20px 25px rgba(0, 0, 0, 0.8);
```

**注意**: 深色模式下阴影强度要比浅色高 30-50% 才能达到相同视觉效果。

## TRANSITIONS

```css
--duration-fast: 150ms;
--duration-normal: 250ms;
--duration-slow: 400ms;

--ease-default: cubic-bezier(0.4, 0, 0.2, 1);
--ease-bounce: cubic-bezier(0.34, 1.56, 0.64, 1);
--ease-smooth: cubic-bezier(0.25, 0.1, 0.25, 1);
```

### 组件动画持续时间

| 动作 | 时长 | 缓动 |
|------|------|------|
| 页面切换 | 250ms | ease-default |
| 按钮悬停 | 150ms | ease-default |
| 模态框进入 | 300ms | ease-smooth |
| 徽章解锁 | 400ms + 100ms delay | ease-bounce |
| 骨架屏 | 800ms infinite | ease-default |

## KEY EFFECTS

- **Smooth transitions**: 所有状态变化 150-300ms
- **Gentle hover states**: 微妙的亮度/透明度变化
- **Gesture feedback**: 触摸时的 95% 透明度
- **Toast notifications**: 底部滑入，3s 自动消失

## AVOID (Anti-patterns)

- ❌ 亮色系渐变（破坏沉浸感）
- ❌ 刺眼的动画（长阅读应减少视觉干扰）
- ❌ 字体花样过多（最多 2 种）
- ❌ 过多的阴影层次（最多 3 层）
- ❌ 闪烁或频闪效果
- ❌ 自动播放视频/音频

## PRE-DELIVERY CHECKLIST

- [ ] 所有文字对比度 ≥ 4.5:1 (正文) / 7:1 (小字)
- [ ] 按钮有 `cursor: pointer`
- [ ] 悬停状态平滑过渡 (150-300ms)
- [ ] 浅色模式可选（如果支持）
- [ ] 焦点状态可见（键盘导航）
- [ ] `prefers-reduced-motion` 受尊重
- [ ] 响应式断点：375px, 768px, 1024px, 1440px
- [ ] 触摸目标 ≥ 44×44px

## 断点

```css
/* Tailwind 风格命名 */
--breakpoint-sm: 640px;   /* 手机竖屏 */
--breakpoint-md: 768px;   /* 手机横屏/小平板 */
--breakpoint-lg: 1024px;  /* 平板/小桌面 */
--breakpoint-xl: 1280px;  /* 桌面 */
--breakpoint-2xl: 1536px; /* 大屏 */
```

## 组件库建议

推荐使用以下组件库并自定义主题：

| 框架 | 推荐 | 适配说明 |
|------|------|----------|
| Vue 3 + Tailwind | 原生 Tailwind + 自定义配置 | 最灵活 |
| Nuxt UI | Nuxt UI + 主题覆盖 | 开箱即用 |
| shadcn-vue | shadcn-vue + 深色主题修改 | 高质量基础 |

### Tailwind 配置示例

```js
// tailwind.config.js
module.exports = {
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        background: '#000000',
        surface: '#1E1E1E',
        primary: {
          50: '#EFF6FF',
          100: '#DBEAFE',
          500: '#3B82F6',
          600: '#2563EB',
          700: '#1D4ED8',
        }
      },
      fontFamily: {
        sans: ['"Noto Sans SC"', 'system-ui', 'sans-serif'],
      },
      spacing: {
        '18': '4.5rem',
      }
    }
  }
}
```

## 阅读模式专用样式

### 竖向滚动模式
```css
.reader-scroll {
  overflow-y: auto;
  scroll-behavior: smooth;
  -webkit-overflow-scrolling: touch;
  /* 预加载相邻图片 */
  image-rendering: -webkit-optimize-contrast;
}
```

### 翻页模式
```css
.reader-paged {
  overflow-x: scroll;
  scroll-snap-type: x mandatory;
}
.reader-page {
  scroll-snap-align: start;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}
```

### 条漫模式
```css
.reader-webtoon {
  display: flex;
  flex-direction: column;
}
.reader-webtoon img {
  width: 100%;
  height: auto;
  display: block;
}
```

## 更新日志

- 2026-05-16: 初始版本，深色主题为主
