# 影视技法大词库（Cinematography Vocabulary）

> 通用、跨风格可复用的**镜头运动 / 景别 / 构图 / 灯光 / VFX** 词库。来源综合 `ai9app/AI-Cinematic-Prompt-Director`（250 影视词典）、`ELK-milu/Seedance2-skill`（100+ 运镜词）、`lmr1123/seedance-video-prompt`（运镜手册）、Runway 官方 prompting guide。
> 用法：各风格文件（`styles-风格库/01-*.md` 等）里的「景别/光影/动作运动」模块可直接引用本词库，不必重复罗列。提示词正文英文，中文作注释。

---

## 00 镜头运动（Camera Movement）

| 英文 tag | 中文 | 何时用 / 情绪 |
|---|---|---|
| `static shot / locked-off camera` | 固定机位 | 稳定、压迫、观察；情绪特写首选 |
| `slow dolly in / push in` | 缓慢推镜 | 逼近、沉默压迫、情绪卷入（CyberJ 微表情常用） |
| `dolly out / pull back` | 拉镜 | 揭示环境、分离、疏离 |
| `tracking shot / follow` | 跟拍 | 平行跟随主体，代入感 |
| `handheld (subtle shake)` | 手持轻微抖 | 临场、纪录感、紧张 |
| `steadicam (smooth follow)` | 斯坦尼康 | 顺滑跟随，不静止 |
| `crane shot / jib` | 升降臂 | 上下大幅改变视角与权力关系 |
| `drone ascending / aerial` | 无人机升起 | 宏大、规模感、上帝视角 |
| `FPV racing / low weaving` | 第一视角低飞穿梭 | 速度、肾上腺素 |
| `pan left/right` | 横摇 | 建立地理、跟随横移动作 |
| `tilt up/down` | 纵摇 | 揭示尺度/高度 |
| `whip pan` | 快速甩镜 | 转场、能量爆发 |
| `slow reveal pan` | 缓慢揭示横摇 | 悬念铺垫 |
| `dolly zoom (vertigo effect)` | 希区柯克变焦 | 不安、眩晕（心理失衡） |
| `orbit / arc shot` | 环绕 | 审视、重要感、神秘 |
| `SnorriCam (camera on actor)` | 贴身固定（背景动） | 眩晕、迷失、强度 |
| `rack focus / focus pull` | 变焦转换焦点 | 引导注意力在前后景间切换 |
| `parallax move` | 视差横移 | 2.5D 层次、MG 常用 |
| `truck left/right / pedestal` | 平移/升降（人物不动） | 稳定横移取景 |
| `over-the-shoulder (OTS)` | 过肩 | 对话戏基准机位 |

**联动规则**
- 每条 prompt **只选一种主运动**；多种方向混写 → AI 混乱不可用。
- 特写 + `push in` 情绪最强；大场面 + `crane/drone` 显规模。
- 微表情/眼泪戏用 `static` 或极缓 `push in`，不要用 `whip pan`。

---

## 01 景别与焦段（Shot Size & Lens）

| 英文（景别） | 中文 | 焦段 / 光圈建议 |
|---|---|---|
| `extreme close-up (ECU)` | 大特写（眼/唇/泪） | 85–100mm macro，f/2 |
| `big close-up (BCU)` | 超近特写（脸占满） | 85mm，f/1.8 |
| `close-up (CU)` | 特写（头肩） | 85mm，f/1.8 |
| `medium close-up (MCU)` | 中近景（胸上） | 50–85mm，f/2 |
| `medium shot (MS)` | 半身 | 50mm，f/2.8 |
| `cowboy shot` | 七分身（膝上） | 50mm |
| `full shot (FS)` | 全身带景 | 35–50mm |
| `wide shot (WS) / establishing` | 全景/远景 | 24–35mm |
| `extreme wide / epic` | 大远景 | 16–24mm |

**规则**
- 广角（≤35mm）拍面部特写会鼻大脸变形 → 特写一律 85mm 起。
- 大光圈 + 侧脸须写 `focus on the near eye`，否则焦点跑鼻尖。
- 情绪递进：防御期 `MCU` → 暴露期 `BCU/ECU`（CyberJ 规则）。

---

## 02 构图（Composition）

- `rule of thirds` 三分法 · `symmetrical composition` 对称构图（韦斯·安德森） · `leading lines` 引导线 · `dutch angle` 荷兰角（失衡/紧张） · `frame within frame` 框中框 · `negative space` 负空间（留白/孤独） · `centered / centered framing` 居中（仪式感/压迫） · `foreground bokeh` 前景虚化 · `low angle (power)` 微仰（气场） · `high angle (submissive)` 微俯（弱势） · `eye-level` 平视。

---

## 03 灯光（Lighting）

| 英文 | 中文 | 用途 |
|---|---|---|
| `volumetric lighting` | 体积光 | 尘埃/雾气光束，电影感 |
| `key light + fill + rim` | 主光+补光+轮廓光 | 标准三点布光 |
| `hard light / low-key` | 硬光/低调 | 悬疑、阴影、诺兰式 |
| `soft diffuse / high-key` | 柔光/高调 | 治愈、广告、日系 |
| `neon (cyberpunk)` | 霓虹 | 赛博朋克、夜景 |
| `chiaroscuro` | 明暗对比 | 戏剧、伦勃朗光 |
| `practical light` | 道具光（灯/屏/烛） | 真实感光源 |
| `anamorphic streaks` | 变形宽镜光芒 | 电影质感 |
| `golden hour` | 黄金时刻 | 暖、治愈、史诗 |
| `overhead fluorescent` | 顶光荧光 | 隔离、冷感、办公 |
| `candlelight flicker` | 烛光闪动 | 亲密、复古 |

**色温 × 情绪速查**：暖（3200K）亲密/怀旧 ↔ 冷（6500K）疏离/科技；冷暖对撞（teal-orange）科幻/商业。

---

## 04 VFX / 质感（Texture & Lens FX）

- `film grain` 胶片颗粒 · `anamorphic lens flare` 变形宽镜眩光 · `bloom` 辉光 · `bokeh` 散景 · `chromatic aberration` 色散 · `motion blur` 动态模糊 · `slow motion (high-speed)` 慢动作 · `time-lapse` 延时 · `light leak` 漏光 · `lens distortion` 镜头畸变 · `vignette` 暗角。

---

## 05 与风格文件的联动（速记）

- **PV/音乐 MV**（styles-风格库/01）：多用 `whip pan / orbit / rack focus / beat-sync move`，节奏驱动。
- **CG**（styles-风格库/02）：`volumetric lighting / anamorphic / bloom`，电影级渲染。
- **手绘**（styles-风格库/04）：避免 `photorealistic lens`，用 `flat shading, minimal grain`；`boiling line` 生死线。
- **AI 漫剧**（styles-风格库/05）：`dolly zoom`（希区柯克）、`OTS` 对话、`push in` 情绪。
- **商业**（styles-风格库/06）：`product hero lighting / soft diffuse / macro rotate`。
- **建筑**（styles-风格库/07）：`wide shot + golden hour + volumetric`。
- **写真**（styles-风格库/08）：`85mm CU + shallow DOF + window light`。
- **二创整活**（styles-风格库/10）：`seamless loop`（鬼畜）、`shot-for-shot`（复刻）。
