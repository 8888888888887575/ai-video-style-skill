# 10 · 二创整活类（Fanwork / Meme Remix / 整活整蛊）

> **定位**：把已有 IP / 角色 / 名场面 / 梗图拿来做「二次创作 + 整活」——换脸、名场面复刻、鬼畜卡点、跨 IP 联动、角色现代整活、梗图动起来、风格迁移整活。
> 这是短视频平台（抖音 / B 站 / TikTok / YouTube Shorts）最卷、最易爆的品类之一，本质是 **「参考图 / 原作驱动 + 场景 / 风格改写」**，而非从零创作。
> 最大约束：**身份一致性（脸 / 角色认得出）+ 梗的可识别性（原梗 / 名场面被认出）**。换脸与复刻务必用参考图 / 首尾帧锁身份，否则出陌生人、构图漂。

---

## 00 · 范例（完整英文 Prompt + 中文注释）

**例 0-1 · 名场面复刻（经典电影镜头用 anime 重演）**
```
[镜头] Shot-for-shot recreation of the famous hallway fight, slow-motion tracking dolly,
[主体] a swordsman in tattered coat performing the signature spin slash,
[动作] motion matched frame by frame to the original, cloth and embers trailing,
[环境] burning corridor with falling debris, volumetric smoke,
[光影] teal-orange cinematic grade, hard key light through fire,
[风格] anime remake of live-action scene, cel shading, 2.5D, homage to the original film,
[后期] film grain, slight chromatic aberration on impact,
[负向] composition drift, wrong angle, deformed face, extra limbs, photorealistic, 3D render.
```
中文注释：复刻必须**附原镜截图作 I2V 参考**锁构图；用 `shot-for-shot recreation, motion matched frame by frame` 表达逐帧复刻；风格改写用 `anime remake of live-action scene` 锚定「原作→目标风格」。

**例 0-2 · 换脸整活（名人脸放进搞笑场景）**
```
[镜头] Medium close-up 50mm, eye-level,
[主体] a well-known celebrity face (use reference image to lock identity),
[动作] doing an exaggerated spit-take then deadpan stare at camera, comedic timing,
[环境] mundane office break room, fluorescent light,
[光影] flat sitcom lighting, slight overexposure for comedy,
[风格] comedic face-swap remix, realistic skin but exaggerated expression,
[后期] meme caption overlay "when the deadline hits", comedic sfx beat,
[负向] identity drift, wrong person, face morph, deformed face, extra limbs.
```
中文注释：换脸整活**必须参考图锁脸**（Wan 2.7 / Vidu Q3 / Kling 3.0 的 I2V + 首尾帧；专业换脸走开源 insightface + Wan/Hunyuan）。负向词强调 `identity drift, wrong person` 防出陌生人。涉及真人肖像需获授权 / 注明虚构娱乐用途，避免误导。

**例 0-3 · 鬼畜 / loop 卡点（表情包循环）**
```
[镜头] Center frame, locked composition,
[主体] a reaction meme face (shocked expression),
[动作] seamless loop: zoom-in punch then snap back, repeat every 4 beats, beat-synced,
[环境] solid color background,
[光影] high-saturation comedy key light,
[风格] meme loop, comedic exaggeration, thumbnail-core,
[后期] comedic zoom sfx, glitch pop,
[负向] seam break, jump cut, flickering, inconsistent face.
```
中文注释：鬼畜 / loop 的关键是**首尾帧一致才能无缝循环**；用 `seamless loop, beat-synced, repeat every N beats`；PixVerse 的 loop 模式 / MiniMax H3 / Runway 运动笔刷都适合。负向必须防 `seam break`。

**例 0-4 · 跨 IP 联动（把 A 角色放进 B 世界）**
```
[镜头] Wide establishing then push-in,
[主体] a cute cartoon bear (reference image) now in a cyberpunk neon city,
[动作] the bear awkwardly riding a hover-bike, comedic fish-out-of-water,
[环境] rainy neon street, reflections, crowd of androids,
[光影] cyan-magenta neon noir, wet reflections,
[风格] crossover fanwork, universe fusion, character consistency with original design,
[后期] lens flare, anime speed lines,
[负向] character design change, inconsistent costume, deformed, melting.
```
中文注释：跨 IP 联动靠**参考图锁原角色设计** + 场景改写；用 `crossover, universe fusion, character consistency with original design` 防角色被洗。Kling 3.0 / Seedance / Sora 2 擅长。

**例 0-5 · 风格迁移整活（3D 真人 → anime）**
```
[镜头] Match original framing,
[主体] a live-action movie hero reimagined,
[动作] same walk-cycle, same gesture,
[环境] same location but redrawn,
[光影] same light direction, anime shading,
[风格] anime-ify the live-action footage, cel shading, Studio Trigger line style,
[后期] subtle grain,
[负向] photorealistic, 3D render, wrong art style, deformed face.
```
中文注释：风格迁移用 `anime-ify / pixel-ify / live-action-ify` 明确方向；锚定目标美术（如 `Studio Trigger line style`）；Wan 2.7 / MiniMax H3 / Vidu Q3 风格化强。负向排 `photorealistic` 防洗回写实。

---

## 01 · 场景主题（子类型 + 速查表）

| 子类型 | 英文锚词 | 典型意图 | 必带参考 |
|---|---|---|---|
| 名场面复刻 / 致敬 | `shot-for-shot recreation, homage, remake` | 复刻经典镜头 / 名场面 | 原镜截图（I2V） |
| 换脸整活 | `face-swap, face replacement, deepfake-style remix` | 名人 / 角色脸换到别处 | 人脸参考图 |
| 鬼畜 / 卡点 | `loop, beat-sync, meme, comedic repeat` | 循环梗 / 卡点洗脑 | 原表情参考（可选） |
| 跨 IP 联动 / 混搭 | `crossover, fandom mashup, universe fusion` | A 进 B 世界 | 角色参考图 |
| 角色现代整活 | `character does modern things, character interview` | 角色说现代话 / 干现代事 | 角色参考图 |
| 梗图 / 表情包动起来 | `meme to video, reaction face animation` | 静态梗动起来 | 梗图参考 |
| 影视 what-if / 类型互换 | `alternate universe, genre swap` | 把喜剧拍成恐怖等 | 原作参考 |
| 风格迁移整活 | `anime-ify, pixel-ify, live-action-ify, clay-ify` | 改画风不换内容 | 原片段参考 |

---

## 02 · 景别构图（Shot Size / 角度 / 设备 / 焦段 / 构图）

- **景别**：`close-up`（表情梗）/ `medium shot`（换脸整活全身）/ `wide shot`（跨 IP 世界）/ `center frame locked`（鬼畜 loop）/ `match original shot size`（复刻）。
- **角度**：`eye-level`（访谈整活）/ `low angle hero`（名场面）/ `over-the-shoulder`（对话梗）/ `match original camera angle`（复刻必做）。
- **设备**：`50mm`（自然对话）/ `85mm portrait`（换脸特写）/ `24mm wide`（世界联动）/ `static tripod`（鬼畜锁定构图）。
- **焦段**：`shallow DOF`（人物整活）/ `deep focus`（世界联动）/ `locked focus`（loop 防跳焦）。
- **构图**：`rule of thirds` / `centered symmetry`（鬼畜）/ `match original composition`（复刻核心）。

**联动规则**：
- 复刻 / 风格迁移 → **必须附原镜截图作 I2V 参考**，否则构图、角度、人物位置漂移，梗就失效。
- 鬼畜 loop → 构图必须 `locked`，首尾帧一致才能无缝循环。
- 跨 IP → 世界用 wide，角色用参考图锁设计，避免被环境风格吃掉。

---

## 03 · 主体特征（角色 / IP / 名人脸）

- 身份锁词：`use reference image to lock identity` / `character consistency with original design` / `known franchise hero`。
- 名人整活：`celebrity face (reference locked)` / `public-figure cameo`；**合规提示**：涉及真人肖像需授权或明确虚构娱乐用途，避免误导、避免冒犯。
- 角色设计：`original costume kept` / `signature hairstyle` / `iconic outfit`（联动时保原设计）。
- 解剖：`correct face structure` / `consistent features across frames`。

**联动规则**：换脸 / 联动 / 复刻三类，**参考图是必选**；纯文本 T2V 做整活身份必然漂移。

---

## 04 · 服装造型（选读）

- 复刻：`original costume replicated` / `period-accurate outfit`。
- 现代整活：`modern casual wear` / `office attire` / `street fashion`（反差萌）。
- 联动：`keep original outfit in new world`（防被新世界风格同化）。
- 换装：`outfit swap, same pose`（电商换装技术可复用，见 styles/06-commercial.md）。

---

## 05 · 光影氛围（布光 / 色温 × 情绪）

| 意图 | 英文布光词 | 色温 × 情绪 |
|---|---|---|
| 复刻原作 | `match original lighting` | 还原原作基调 |
| 整活反差 | `flat sitcom light, slight overexposure` | 亮堂喜剧感 |
| 鬼畜卡点 | `high-saturation comedy key` | 高饱和洗脑 |
| 跨 IP 世界 | `neon noir, wet reflections` | 冷调反差 |
| 风格迁移 | `same light direction, anime shading` | 保光向改材质 |

---

## 06 · 动作运动（视频核心 → 静态 / 动态 / 过渡 / 招牌运动）

- **复刻运动**：`motion matched frame by frame` / `shot-for-shot` / `slow-motion tracking` / `抽帧复刻`。
- **鬼畜 / loop**：`seamless loop` / `beat-synced loop` / `repeat every N beats` / `zoom punch loop` / `comedic repeat`。
- **表情包动效**：`reaction face morph` / `exaggerated blink` / `wobble` / `meme shake` / `deadpan stare`。
- **跨 IP 反差**：`fish-out-of-water movement` / `character does impossible action` / `awkward comedic gesture`。
- **风格迁移**：`same walk-cycle, same gesture`（动作保原，画风改）。

**联动规则**：
- loop / 鬼畜 → **首尾帧必须一致**（seamless），否则循环处有跳切。
- 复刻 → 运动节奏要对齐原片段（慢放 / 抽帧），否则「神韵」丢。
- 卡点 → 需原生音频模型（Kling 3.0 / MiniMax H3 / Vidu Q3）或后期对轨。

---

## 07 · 表情表演（选读）

- 梗表情：`shocked reaction` / `deadpan stare` / `side-eye` / `smug smile` / `spit-take`。
- 表演阶段：`setup → beat → punchline`（整活三拍）；`deadpan before comedic hit`。
- 夸张：`overacted expression` / `cartoonish reaction`。

---

## 08 · 风格滤镜（美术方向 / 胶片 / 参考锚点）

- **风格迁移词**：`anime-ify` / `pixel-ify` / `live-action-ify` / `clay-ify` / `GTA-ify` / `vaporwave-ify`。
- **原作锚定**：`reference the original art style of <franchise>` / `Studio Trigger line style` / `Ghibli remake`。
- **整活滤镜**：`meme caption overlay` / `glitch` / `VHS` / `thumbnail-core` / `comedy grade`。
- **复刻锚定**：`homage to <film/director>` / `remake of <scene>`。

**联动规则**：风格迁移必须**明确目标风格词 + 负向排原风格词**（如 anime-ify 必排 `photorealistic`），否则被洗回原画风。

---

## 09 · 材质细节（选读）

- 换脸：`realistic skin but exaggerated expression` / `consistent skin texture`。
- 复刻：`materials matched to original` / `same fabric, same metal`。
- 联动：`character design kept crisp against stylized world`。

---

## 10 · 后期特效（选读）

- 换脸合成：`face-swap composite` / `identity lock`。
- 梗字幕：`meme caption overlay` / `subtitle punchline`。
- 音效梗：`comedic sfx beat` / `record scratch` / `ba-dum-tss`。
- 风格化：`glitch transition` / `VHS overlay` / `split-screen original vs remake`。
- 分屏对比：`side-by-side original | remake`（复刻 / 迁移整活常用）。

---

## 11 · 道具场景（选读）

- 原作道具：`iconic prop kept` / `signature object`。
- 现代混搭：`modern gadget in fantasy world` / `coffee cup in battle scene`（反差梗）。
- 梗物件：`rubber duck` / `cricket bat` / `sunglasses`（meme 标配）。

---

## 12 · 负向规则（Negative + 禁止组合 + 冲突避免）

**Negative 词库**：
- 换脸：`identity drift, wrong person, face morph, deformed face, uncanny`。
- 复刻：`composition drift, wrong angle, perspective shift`。
- 鬼畜 loop：`seam break, jump cut, flickering, inconsistent face`。
- 风格迁移：`photorealistic`(做 anime-ify 时) / `wrong art style` / `3D render`(做手绘化时)。
- 通用：`extra limbs, mutated hands, melted geometry`。

**禁止组合（Forbidden）**：
- ❌ 换脸整活却**不附人脸参考图** → 出陌生人 / 身份漂移。
- ❌ 名场面复刻却**不附原镜截图** → 构图、角度、人物位置全漂，梗失效。
- ❌ 鬼畜 loop 却**首尾帧不一致** → 循环处有硬跳切。
- ❌ 风格迁移却**没排原画风词** → 被洗回原风格（anime-ify 不排 photorealistic 会出写实脸）。
- ❌ 跨 IP 联动却**不锁原角色设计** → 角色被新世界风格同化，认不出。

**合规与边界**：
- 真人换脸 / 名人整活需授权或明确虚构娱乐用途，注明「虚构 / parody」，避免误导与冒犯；不针对未成年人。
- 不生成恶意伪造、诽谤、或以假乱真的欺骗性内容。

---

## 13 · 推荐模型（风格 → 模型映射，见 models.md）

| 子类型 | 主推模型 | 备选 | 为何契合 |
|---|---|---|---|
| 换脸整活 | Wan 2.7（I2V + 首尾帧） | Vidu Q3 / Kling 3.0 | I2V + 首尾帧锁脸最稳；专业换脸走开源 insightface + Wan/Hunyuan/LTX；动漫角色脸用 MiniMax H3 / HappyHorse 1.1（口型） |
| 鬼畜 / loop / 卡点 | MiniMax H3 | PixVerse（loop 模式）/ Runway（运动笔刷）/ Pika | loop 模式与运动笔刷精控循环；卡点需原生音频 |
| 名场面复刻 / what-if | Kling 3.0 | Seedance 2.0 / Sora 2（电影感）/ Vidu Q3 | 电影感复刻 + 首尾帧；Sora 2 叙事长镜强 |
| 跨 IP 联动 / 混搭 | Kling 3.0 | Seedance 2.0 / Sora 2 / Vidu Q3 | 角色参考图 + 世界改写，保身份一致 |
| 风格迁移整活（anime-ify 等） | Wan 2.7 | MiniMax H3 / Vidu Q3 | 风格化强，参考图驱动改写画风 |

> 口播 / 访谈整活若需对口型：HeyGen / Hedra（真人）/ HappyHorse 1.1（动漫角色）。

---

## 14 · 组装公式（本风格槽位顺序）

```
[身份参考图 / 原镜截图]（必选：换脸·复刻·联动·迁移都必须）
+ [01 场景主题：子类型锚词] + [02 景别构图：match original / locked]
+ [03 主体特征：reference lock identity / original design kept]
+ [05 光影氛围：match original / comedy grade]
+ [06 动作运动：loop / motion-matched / comedic gesture]
+ [08 风格滤镜：anime-ify / homage / crossover]
+ (选读 3–5：04 服装 / 07 表情 / 09 材质 / 10 后期 / 11 道具)
+ [12 负向规则：identity drift / seam break / 排原风格词]
→ 推荐模型见 [13]
```

**必选槽位**：身份参考图（换脸/复刻/联动/迁移）+ 01 + 02 + 03 + 05 + 06 + 08 + 12 + 13 + 14。
**选读**：04 / 07 / 09 / 10 / 11。
**最小可用示例**（鬼畜 loop）：
```
Center frame locked, a reaction meme face (reference image),
seamless beat-synced loop, zoom punch repeat every 4 beats,
high-saturation comedy key light, meme loop, comedic exaggeration,
meme caption overlay, glitch pop.
负向：seam break, jump cut, flickering, inconsistent face.
```
