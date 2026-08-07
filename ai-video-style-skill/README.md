# AI Video Style Advisor — 使用说明

一个**可移植**的「AI 视频风格 / 美术风格 → 模型选择 + 提示词工程」知识包。
既能被 **OpenAI Codex** 直接作为上下文读取，也能作为 **WorkBuddy Skill** 加载。

## 这个包解决什么
做 AI 视频时，最大的两个不确定性是：
1. **选错模型** —— 比如用电影级写实模型硬做 Motion Graphics，或用动漫模型硬做产品写实。
2. **提示词不对路** —— 不同风格有完全不同的运动语法与视觉词汇，套用通用模板效果差。

本包把「风格 × 模型 × 提示词模板」三层知识结构化，让 agent 在收到简报时自动给出
**推荐模型 + 完整英文提示词 + 中文说明**。

## 目录结构
```
ai-video-style-skill/
├── SKILL.md                      # 主指令（agent 入口；WorkBuddy 兼容 frontmatter）
├── README.md                     # 本文件
├── references/
│   ├── styles.md                 # 风格库【索引 + 装配公式 + 15 模块结构总览】
│   ├── styles/                   # 每个风格一个模块化文件（00–14 共 15 节）
│   │   ├── _TEMPLATE.md          # 母版：统一模块化模板（装配顺序分类法）
│   │   ├── 01-pv.md              # PV / 动漫 MV
│   │   ├── 02-cg.md              # CG / 3D CGI
│   │   ├── 03-mg.md              # MG / 动态图形
│   │   ├── 04-handdrawn.md       # 手绘 2D 动画
│   │   ├── 05-ai-drama.md        # AI 漫剧 / 短剧（含 CG 漫剧 vs 2D 漫剧·命名美学）
│   │   ├── 06-commercial.md      # 商业 / 电商 / 产品视频
│   │   ├── 07-architecture.md    # 建筑 / 室内写实渲染
│   │   ├── 08-portrait.md        # 写真 / 人像摄影（厚涂/Y2K/婚纱/萌宠）
│   │   └── 09-nsfw-asian.md      # NSFW / 亚洲成人（含上游仓库引用）
│   │   └── 10-fanwork.md         # 二创整活 / 换脸 / 名场面复刻 / 鬼畜 / 跨IP联动
│   ├── models.md                 # 2026 模型能力矩阵
│   ├── prompt-templates.md       # 跨风格英文提示词模板速查（A–K，含 MiniMax H3 三段式 模板 K）+ 负向词库
│   ├── h3-guide-H3完整提示词指南.md   # 【H3 完整指南】App端@写法(Part A) + API结构化格式(Part B) + @↔API映射(§3)，已合并cookbook与official-format
│   ├── cinematography.md         # 【技法】运镜/景别/构图/灯光/VFX 大词库
│   ├── sound-design.md           # 【技法】声音桥 J-cut/L-cut、声场、音画同步
│   ├── continuation.md           # 【技法】续拍/分镜串联/长剧情拆分/视频接龙
│   ├── style-combos.md           # 【技法】导演风格速查、风格组合矩阵、27 视觉风格
│   ├── timestamp-storyboard.md   # 【技法】秒级分镜法（模板 B / 史诗结构）
│   ├── creativity-gate.md        # 【技法】创意闸门四关（记忆点/意外感/情绪/叙事）
│   ├── emotion-shot.md           # 【技法】情绪→镜头/微表情设计、对话双表演轨
│   └── decision-matrix.md        # 风格→模型→风格文件 决策映射 + 输出格式
└── examples/
    └── example-briefs.md         # 示例简报 + 期望输出（11 例，用于验证）
```

## 在 OpenAI Codex 中使用
Codex 是面向代码仓库的 agentic 模型。把本文件夹放入你的项目/仓库任意位置，
然后在给 Codex 的指令（或在 `AGENTS.md` / 顶层 prompt）里这样引用：

> 做 AI 视频相关的选型或提示词时，先读 `ai-video-style-skill/SKILL.md`，
> 再按需读 `ai-video-style-skill/references/` 下的对应文件，按其中的输出格式回复。

Codex 会读取 `SKILL.md` 作为指令，并根据需要打开 `references/*.md` 获取具体知识。
所有文件都是纯 Markdown，无需任何运行时依赖。

## 在 WorkBuddy 中使用
- 把 `ai-video-style-skill/` 放入工作区的 `.workbuddy/skills/` 目录（用户级放 `~/.workbuddy/skills/`），
  WorkBuddy 会识别 `SKILL.md` 的 frontmatter 并可在对话中调用。
- 对话中直接说「帮我做一个 anime MV 的提示词」「这个风格用哪个模型」即可触发。

## 语言约定
- **提示词正文用英文**（多数视频模型英文遵循度最佳）。
- **说明与注释用中文**，便于理解。
- 风格名、模型名保留原文（PV / CG / MG / Sora / Kling …）。

## 维护
- 模型能力随版本快速迭代：`models.md` 中的价格/时长/音频支持请以各模型当前官网为准。
- 新增风格：复制 `references/styles/_TEMPLATE-模板.md` → `references/styles/NN-xxx.md`，按 00–14 节填充，在 `references/styles-风格索引.md` 索引表登记，并同步更新 `models.md`、`prompt-templates.md`、`decision-matrix.md`。
- 数据基准：2026-08 公开评测与厂商规格。
