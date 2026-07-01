# DESIGN.md — 康乃尔公司介绍落地页视觉规范

## 项目定位

**这不是传统网站，是用网页形式替代 PPT 讲解的企业介绍落地页。**
- 用途：销售人员对着客户滚动讲解 / 发链接让客户自己浏览
- 形态：单页长滚动（SPA），无跳转
- 语言：中文
- 风格：浅色洁净制造 + 材料科技感

## 全局色板

```
/* 主色 */
--brand-blue: #1B3A5B;        /* 深工业蓝，用于标题、关键文字 */
--brand-blue-light: #2E5A8A;  /* 中蓝，用于副标题、图标 */
--brand-blue-50: #EBF2F8;     /* 极浅蓝，用于区块底色交替 */

/* 中性色 */
--bg-primary: #FFFFFF;         /* 白底主色 */
--bg-secondary: #F7F8FA;       /* 浅灰底，交替区块 */
--text-primary: #1A1A2E;       /* 主文字 */
--text-secondary: #5A6477;     /* 次文字 */
--text-muted: #8E96A8;         /* 辅助文字 */
--border: #E2E5EB;             /* 分割线、卡片边框 */

/* 点缀色 */
--accent-cyan: #00A6B6;        /* 青绿，用于 TPU/AquaChill 等舒适材料 */
--accent-steel: #4A5568;       /* 钢灰，用于工业过滤/吸附区块 */
--accent-warm: #D4A537;        /* 暖金，用于荣誉/资质强调 */

/* 功能色 */
--cta-blue: #1565C0;           /* CTA 按钮蓝 */
--cta-blue-hover: #0D47A1;     /* CTA hover */
```

## 字体系统

```
/* 标题 */
--font-heading: "Source Han Sans SC", "Noto Sans SC", "PingFang SC", "Microsoft YaHei", sans-serif;

/* 正文 */
--font-body: "Source Han Sans SC", "Noto Sans SC", "PingFang SC", "Microsoft YaHei", sans-serif;

/* 数字（英文等宽，数据展示用） */
--font-number: "Inter", "SF Pro Display", system-ui, sans-serif;

/* 字号阶梯（clamp 响应式） */
--fs-hero: clamp(2.5rem, 1.2rem + 5vw, 4.5rem);     /* Hero 主标题 */
--fs-h1: clamp(2rem, 1rem + 4vw, 3rem);              /* 区块标题 */
--fs-h2: clamp(1.5rem, 0.8rem + 3vw, 2rem);          /* 子标题 */
--fs-h3: clamp(1.1rem, 0.9rem + 1vw, 1.35rem);       /* 卡片标题 */
--fs-body: clamp(0.95rem, 0.88rem + 0.3vw, 1.1rem);  /* 正文 */
--fs-small: 0.85rem;                                  /* 辅助文字 */
--fs-stat: clamp(2.5rem, 1rem + 4vw, 4rem);          /* 大数字 */
```

## 间距与布局

```
/* 区块内边距 */
--section-padding: clamp(4rem, 8vw, 7rem) clamp(1.5rem, 5vw, 4rem);

/* 内容最大宽度 */
--max-width: 1200px;

/* 卡片圆角 */
--radius-sm: 8px;
--radius-md: 12px;
--radius-lg: 16px;

/* 阴影 */
--shadow-sm: 0 1px 3px rgba(27, 58, 91, 0.06);
--shadow-md: 0 4px 20px rgba(27, 58, 91, 0.08);
--shadow-lg: 0 12px 40px rgba(27, 58, 91, 0.12);
--shadow-hover: 0 8px 30px rgba(27, 58, 91, 0.15);

/* 过渡 */
--transition: 0.3s cubic-bezier(0.4, 0, 0.2, 1);
```

## 动效规范

```
/* 滚动入场：元素从下方 30px 淡入上移 */
[data-animate] {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
[data-animate].visible {
  opacity: 1;
  transform: translateY(0);
}

/* 数字递增动画：大数字从 0 滚动到目标值 */
/* 卡片 hover：translateY(-4px) + shadow-hover */
/* 区块背景：白/浅灰交替，过渡用渐变模糊带 */
/* Hero 背景：微妙的几何线条 + 浅蓝渐变，不用视频/动画 */
```

## 区块交替底色规则

奇数区块（§1, §3, §5...）：`--bg-primary` 白底
偶数区块（§2, §4, §6...）：`--bg-secondary` 浅灰底

## 导航

- 顶部固定半透明导航栏（白底 + 毛玻璃 + 底部细线）
- 左侧 LOGO/公司名
- 右侧锚点导航：集团背书 / 产品矩阵 / 质量保障 / 联系合作
- 滚动时自动高亮当前区块
- 移动端收为汉堡菜单

## 响应式断点

```
--bp-mobile: 640px;
--bp-tablet: 768px;
--bp-desktop: 1024px;
--bp-wide: 1280px;
```

## 产品区块色彩分配

| 产品板块 | 点缀色 | 说明 |
|----------|--------|------|
| TPU 弹性透气材料 | --accent-cyan | 舒适/亲肤/透气 |
| AquaChill 凉感材料 | --accent-cyan | 凉感/清凉 |
| MaxiScrub 清洁擦拭 | --brand-blue-light | 清洁/日常 |
| PBT 耐高温过滤 | --accent-steel | 工业/高温 |
| 工业吸附与擦拭 | --accent-steel | 工业/重工况 |
| 空气与液体过滤 | --accent-steel | 工程/过滤 |
| 口罩熔喷 | --brand-blue-light | 医卫/防护 |

## 图片处理原则

- 产品实拍照：圆角 12px + shadow-md，不加滤镜
- 工厂/产线照：全宽展示 + 轻微暗角
- 数据卡片：不用图片，纯 CSS 卡片
- 结构示意图：用现有素材，不加特效
- 图标：统一线性风格，stroke-width 1.5px，颜色跟随区块点缀色

## 禁止事项

- ❌ 不用 hero eyebrow / kicker / badge / pill 标签
- ❌ 不用渐变文字
- ❌ 不用 emoji
- ❌ 不用占位图（lorem ipsum / placeholder）
- ❌ 不编造数据
- ❌ 不写客户名称（保密红线）
- ❌ 不宣称医疗功效
- ❌ 不用花哨的 3D / 粒子特效
- ❌ 不自动播放视频或音频
