# PM 技能包 — 独立版

> 两个可移植的 AI 技能，粘贴到任何 AI 智能体的自定义指令中即可使用。

---

## 目录结构

```
standalone-skills/
├── prd/
│   └── SKILL.md          # PRD 生成器（~15KB）
├── prototype/
│   └── SKILL.md          # 原型生成器（~18KB）
└── README.md             # 本文件
```

## 安装方法

### claude.ai Projects
1. 新建 Project → 项目设置 → **Custom Instructions**
2. 粘贴 `prd/SKILL.md` 或 `prototype/SKILL.md` 的全部内容
3. 在对话中直接说需求即可

### ChatGPT 自定义 GPT
1. Create a GPT → **Instructions** 字段中粘贴技能内容
2. 命名并保存

### Cursor
1. 项目根目录创建 `.cursorrules` 文件
2. 粘贴技能内容

### 直接使用
1. 将 SKILL.md 全部内容复制
2. 粘贴到任何 AI 对话中，说"请按照以上规则执行"

## 技能说明

| 技能 | 文件 | 用途 | 输出 |
|------|------|------|------|
| **PRD 生成器** | `prd/SKILL.md` | 生成结构化产品需求文档 | Markdown 格式的 15 节完整 PRD |
| **原型生成器** | `prototype/SKILL.md` | 生成交互式 HTML 原型 | 单文件 HTML（双击即开） |

### PRD 技能包含
- 15 节完整模板结构
- 30+ 产品类型的 UI 风格自动匹配表
- 数据库设计规范（含中文字段说明）
- 验收标准 Given-When-Then 格式
- 技术方案四件套（技术栈 + 架构图 + 目录 + 关键决策）
- 质量检查清单

### 原型技能包含
- 完整设计 Token 系统
- 移动端/桌面端双容器方案
- 全部 CSS 组件样式
- JS 交互函数（Tab切换、子页面、模态框、Toast、加载模拟）
- iOS / Apple Minimal 风格快速覆盖 Token
- 手机端快速 HTML 骨架
- 质量检查清单

## 使用技巧

**合并使用：** 把两个 SKILL.md 的内容合并粘贴到同一个 AI 的自定义指令中，AI 会根据你的需求自动判断生成 PRD 还是原型。

**定制 Prompt：** 如果 AI 输出太短，告诉它"严格按照模板结构输出"；如果原型缺少交互，提醒它"检查交互覆盖清单"。
