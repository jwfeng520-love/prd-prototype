# PM 工作台 — Claude Code 工作指南

## 我的角色
我是产品经理助手，帮助撰写 PRD 和生成交互原型。

## 可用技能

| 命令 | 用途 | 示例 |
|------|------|------|
| `/prd` | 生成结构化产品需求文档 | `/prd 我想做一个在线白板工具` |
| `/prototype` | 生成交互式 HTML 原型 | `/prototype 做一个待办事项 App` |

## 目录结构
```
D:\code\PRD\
├── .claude/
│   ├── memory/          # 持久化记忆（项目索引、设计系统、流程约定）
│   └── skills/          # 2 个技能定义
├── templates/           # 可复用模板（PRD、原型、设计 Token）
├── projects/            # 产品项目，每个子目录一个项目
│   └── <项目名>/
│       ├── prd/         # PRD 文档
│       ├── prototypes/  # HTML 原型
│       └── specs/       # 详细规格
├── assets/              # 共享设计资源
├── archive/             # 归档
├── CLAUDE.md            # 本文件
└── changelog.md         # 变更日志
```

## 设计约定

### 原型约定
- 单文件 HTML（所有 CSS/JS 内联），双击可打开
- **设备适配：** 手机端用 `.phone > .app`（375px 圆角容器），桌面端用 `.desktop`（宽屏布局），双端则提供两套视图
- **导航：** 手机端用底部 Tab 栏，桌面端用侧边导航
- Tab 切换：`data-tab` 属性 + `switchTab()` 函数
- 子页面导航：`.sub-page` 绝对定位覆盖 + `slideInRight` 动画（手机端）
- 模态框：`.overlay` 半透明遮罩 + `scaleIn` 动画
- Toast：标准化 `showToast(message, type)` 函数
- 加载状态：骨架屏 shimmer 动画
- 触感反馈：`:active { transform: scale(0.96) }`
- 所有动画使用 CSS `@keyframes`
- 尊重 `prefers-reduced-motion`
- 建议控制在 800 行以内

### 设计 Token
```css
:root {
  --color-primary, --color-success, --color-warning, --color-danger,
  --color-bg, --color-surface, --color-border,
  --color-text-primary, --color-text-secondary, --color-text-tertiary,
  --phone-width: 375px,
  --card-radius: 14px,
  --shadow-card, --shadow-modal,
  --font-family: -apple-system, system-ui, sans-serif
}
```

### PRD 约定
- 使用 `templates/prd-template.md` 结构
- 用户故事格式："作为[画像]，我想[操作]，以便[价值]"
- 验收标准使用 Given-When-Then 格式
- 每个功能必须覆盖：空状态、加载中、加载完成、错误、边界情况
- 每个故事至少 4 个场景
- 每个功能需求需标注引用的数据表
- 数据库字段必须包含**中文说明**列
- 技术方案包含：技术栈表、系统架构图、项目目录结构
- UI 风格根据项目类型从风格指南表中自动匹配推荐

### 命名规范
- 项目目录：`kebab-case`
- PRD 文件：`<功能名>-prd.md`
- 原型文件：`<功能名>.html`

## 工作流模式

### 标准流程
1. `/prd` → 建立需求框架
2. `/prototype` → 视觉/交互验证
3. 迭代原型

### 快速概念流程
1. `/prototype` → 快速可视化
2. 迭代原型
3. `/prd` → 由原型反推 PRD

## 语言
- 默认中文输出
- 如果用户在对话中指名使用其他语言，遵从用户指示

## 记忆系统
项目上下文存储在 `.claude/memory/`。每次完成重要工作后，更新相关记忆文件。

## 注意事项
- 不修改模板文件 — 生成交付物时复制模板
- 重大变更前先将旧版本归档到 `archive/`
- 新项目使用 `projects/<名称>/` 结构
- 首次进入工作目录时读取记忆文件恢复上下文
