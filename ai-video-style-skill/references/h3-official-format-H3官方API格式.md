# MiniMax H3 官方提示词格式规范（中英对照蒸馏 / Official Prompt Format）

> 蒸馏自 MiniMax 官方 HuggingFace 仓库 `MiniMaxAI/MiniMax-H3` 两份文档：
> - `docs/VIDEO_PROMPT_WRITING_GUIDE_base_en.md` —— **Base 四模式**（T2VA / I2VA / FL2VA / L2VA）
> - `docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md` —— **Full-Reference Mode（全参考模式）**
>
> **本文件与 `h3-prompt-cookbook.md` 的关系（两套范式，语义对应）：**
> - `h3-prompt-cookbook.md` = 海螺 **App / 网页端**的 `@图片1 人物参考` 自然语言标注写法（面向交互界面）。
> - 本文件 = H3 **API 实际接受的结构化提示词格式**——字段名 / 标签（如 `integrated_multimodal_description`、`<Subject 1>`、`[Shot 1]`）就是 API 真实 token。
> - 给 Codex / Claude / Cursor 等 agent **直接调 API** 时，用本文件的结构；用海螺网页/App 时，用 cookbook 的 `@` 写法。两者可互相映射（见 §3）。

---

## 0. 两套范式对照（App `@` vs API 结构化）

| 意图（中文） | 海螺 App 端（`@` 写法，见 cookbook） | H3 API 结构化（本文件） |
|---|---|---|
| 人物参考 / 锁脸 | `@图片1 是人物参考` | `<Subject 1> is the person in <Picture 1>...` + `subject_definitions` 段 |
| 场景 / 风格参考 | `@图片2 是场景参考` | `<Subject 2> is the environment in <Picture 2>...` |
| 首帧图 | `@图片1 作为开头` | I2VA 指令：`at 0.00 seconds ... <Picture 1> (from [Shot 1]) is fully referenced.` |
| 尾帧图 | `@图片2 作为结尾` | L2VA 指令：`<Picture 1> (from [Shot N]) aligns with the S.SS-second mark` |
| 运镜参考视频 | `@视频1 是运镜参考` | `<Video 1> is the camera-movement reference`（task type = `reference generation`） |
| 音色参考 | `@音频1 是音色参考` | `<Audio 1> is the voice-timbre reference for <Subject X> (Sx)` |
| 台词 | `@人物 说："……"` | `(S1) says: <d>[Chinese] ……</d>` |

---

## 1. Base 四模式（T2VA / I2VA / FL2VA / L2VA）

四种模式区别只在"是否给参考图、图放在开头还是结尾"：

| 模式 | 英文全称 | 中文 | 首帧指令 |
|---|---|---|---|
| **T2VA** | Text-to-Video (Audio) | 纯文生视频 | 无（直接写三核心字段） |
| **I2VA** | Image-init T2VA | 图生视频（图=首帧） | 有，指定首帧 |
| **FL2VA** | First-Last T2VA | 首+尾帧生视频 | 有，指定首帧+尾帧 |
| **L2VA** | Last T2VA | 尾帧生视频（倒推开头） | 有，指定尾帧 |

### 1.1 终稿结构（Final Prompt Structure）

**Part One — 对齐指令（Instruction，仅 I2VA / FL2VA / L2VA 有；T2VA 没有，直接进 Part Two）**

- **I2VA（首帧）**——必须作为最终提示词的第一行，其后空一行再写核心字段：
  ```text
  For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.
  ```
- **FL2VA（首+尾帧）**：
  ```text
  How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot N) aligns with the S.SS-second mark of the target video.
  ```
- **L2VA（尾帧）**：
  ```text
  How the reference pictures align with the target video — <Picture 1> (from [Shot N]) aligns with the S.SS-second mark of the target video.
  ```
  > `N` = 实际尾镜序号；`S.SS` = 视频有效时长，保留两位小数。指令必须是第一行，空一行后接核心字段。

**Part Two — 三核心字段（Three Core Fields）**

```text
integrated_multimodal_description: [Shot 1] ...

overall_soundscape: ...

non_diegetic_music: ...
```

| 字段（英文原文，API 真实 token） | 中文含义 | 写法要点 |
|---|---|---|
| `integrated_multimodal_description` | 多模态整合描述 | 沿时间线描述视觉、动作、镜头、说话人、台词、歌唱、画内音 |
| `overall_soundscape` | 整体声景 | 1–4 句英文，概括环境音 / 物理动作音 / 非语言人声（台词/歌已在上面） |
| `non_diegetic_music` | 非剧情音乐 | 1–3 句，只描述"角色听不到、仅观众可听"的配乐（乐器/速度/节奏/动态） |

### 1.2 沿时间线展开 multimodal description

- `[Shot 1]` 开头**不写时间戳**；后续镜头用 `[Shot N] At MM:SS.mmm, ...`（切镜时间必须严格递增且在视频时长内）：
  ```text
  [Shot 1] Live-action, cinematic, a medium-wide shot frames...
  [Shot 2] At 00:03.500, the camera cuts to...
  ```
- `[Shot 1]` 开头先定**整体风格 + 初始构图**。常用风格词（保留英文）：
  `Cinematic` / `live-action` / `2D-animated` / `3D CG` / `claymation`(黏土) / `watercolor`(水彩) / `vintage film`(复古胶片)
- 图生任务从参考图推导风格；纯文生从用户文字选风格。

### 1.3 镜头与切镜（Shots and Cuts）

- 普通切镜动词：`the camera cuts to` / `the shot cuts to` / `the shot transitions to` / `the shot changes to` / `the shot switches to`。
- 用户明确要求时可用 cross-dissolve(叠化) / fade(淡入淡出) / wipe(擦除)。
- 切镜必须带来**新信息**（主体/空间/状态/视角/时间）。若只改距离或微角度，优先用**运镜**而非切镜。
- 跨 cut 的连续性写法：`continues seamlessly across the cut` / `continues uninterrupted into the next shot` / `carries over from the previous shot` / `remains audible across the transition`.

### 1.4 运镜三维度（Motion Type + Amplitude + Speed）

完整运镜词表（保留英文原词，配中文）：

| 维度 | 可用表达（英文原文） | 中文 |
|---|---|---|
| Motion type | `Zoom In` / `Zoom Out` | 变焦（机身不动，焦距变） |
| Motion type | `Push In` / `Pull Out` | 推 / 拉（机位前后移动） |
| Motion type | `Pan Left` / `Pan Right` | 平移（机身不动，镜头水平转） |
| Motion type | `Truck Left` / `Truck Right` | 横移（机位水平平移） |
| Motion type | `Tilt Up` / `Tilt Down` | 俯仰（机身不动，镜头垂直转） |
| Motion type | `Pedestal Up` / `Pedestal Down` | 升降（整机上下移动） |
| Motion type | `Arc Shot` | 弧线运动（绕主体弧移） |
| Motion type | `Tracking Shot` | 跟拍（跟随移动主体） |
| Motion type | `Static Shot` | 固定机位 |
| Motion type | `Shake Slightly` / `Shake Strongly` | 轻微 / 强烈抖动 |
| Motion type | `POV` | 主观视角 |
| Motion type | `Roll Clockwise` / `Roll Counterclockwise` | 滚转（绕镜头轴顺时针/逆时针） |
| Amplitude | `with small amplitude` / `with large amplitude` | 小幅度 / 大幅度 |
| Speed | `at slow speed` / `at fast speed` | 慢速 / 快速 |

> 写法：把运镜写成镜头内的自然英文动作，不要堆在句尾当标签。幅度/速度仅在有意义时加（中幅度、正常速度通常省略）。
```text
The camera pushes in with small amplitude at slow speed toward the folded letter in her hands.
The camera pans right with large amplitude at fast speed, revealing the open doorway.
The camera holds a static shot as the runner exits the frame.
```

### 1.5 说话人 / 台词 / 歌唱（Speakers, Dialogue, Singing）

- 说话/歌唱/画外人声用**稳定 ID**：`(S1)` `(S2)`，多人同说用复合 ID `(S1,S2)`。同一说话人跨镜头 ID 不变；不发声的角色不给 ID。
- 台词格式：`<d>[语言标签] 原文</d>`——**原文逐字保留，不翻译不改写**：
  ```text
  The young woman with a quiet, breathy voice (S1) says: <d>[English] I get off at the next station.</d>
  The two children (S1,S2) shout together, <d>[English] Wait for us!</d>
  ```
- 首次出场要先用视觉+音频上下文建立稳定身份（角色类型/年龄/性别/是否在画内/音高/音色/语速/口音）。身份短语、`(Sx)`、动作、语气都在 `<d>` **外**；`<d>` 内只放语言标签 + 用户原文。
- **画外音（voiceover）**：用 `says in an off-screen voiceover`，并在其后注明 `while his lips remain completely closed`（嘴保持闭合）。
- **台词跨 cut**：在连接点两侧都用 `<scenetrans>`，并明确 `the audio continues across the cut`；视频结束截断用 `<cutoff>`。

### 1.6 屏幕文字（On-Screen Text）

- 画面里实际可见的标语/招牌/字幕/霓虹字，用**英文双引号**包裹，原文逐字保留（不翻译）：
  ```text
  A red neon sign reading "营业中" glows above the doorway.
  ```

### 1.7 overall_soundscape / non_diegetic_music 写法

- `overall_soundscape`：1–4 句英文连续段落，概括全程环境音/物理动作音/非语言人声（风、雨、交通、脚步、布料、撞击、呼吸、笑、喘）。台词/歌/画内乐已在 multimodal 里，这里不重复。用户要求全程静音才用 `N/A`。
  ```text
  overall_soundscape: Steady rain taps against the café windows while low room ambience continues underneath. The entrance bell rings once, followed by wet footsteps and the soft scrape of a chair.
  ```
- `non_diegetic_music`：1–3 句，描述角色听不到、仅观众可听的配乐，聚焦乐器/速度/节奏/动态变化，不用抽象情绪词、不解释情绪功能。无则用 `N/A`。
  ```text
  non_diegetic_music: Sparse piano notes at a slow tempo, joined by sustained low strings that gradually increase in volume before fading out.
  ```

### 1.8 四个官方 Case（原样保留英文，附中文要点）

**Case 1 — T2VA（纯文生）**
```text
integrated_multimodal_description: [Shot 1] Live-action, cinematic, a medium-wide shot frames a baker opening the shutters of a small street bakery before sunrise. The camera pushes in with small amplitude at slow speed as the middle-aged baker with a calm, slightly raspy voice (S1) places a fresh loaf on the wooden counter and says: <d>[English] First batch of the morning.</d> [Shot 2] At 00:05.000, the camera cuts to a close-up of steam rising from the sliced bread while the baker's final words carry over from the previous shot.

overall_soundscape: Wooden shutters scrape open over a quiet street as trays clink softly inside the bakery. The doorbell rings once, followed by light footsteps and the crisp sound of bread being sliced.

non_diegetic_music: A soft acoustic-guitar pattern at a moderate tempo, joined by sparse upright-bass notes and a gentle fade at the end.
```
> 中文要点：无参考图，纯文直接建时间线；可补场景/角色/动作/声音细节但需与用户意图一致；`<d>` 内英文原文不动；跨 shot 台词用 `carry over from the previous shot`。

**Case 2 — I2VA（图=首帧）**
```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, the young woman shown in <Picture 1> remains beside the rain-covered train window, preserving her appearance, clothing, seat position, and the carriage layout. The camera trucks right with small amplitude at slow speed as she lifts her gaze from the folded letter toward the passing city lights. Her reflection moves across the glass while the quiet, breathy young woman (S1) says: <d>[English] I get off at the next station.</d> She folds the letter along its existing crease.

overall_soundscape: The train wheels produce a steady metallic rhythm beneath a low ventilation hum. Rain ticks against the window while paper rustles softly in her hands.

non_diegetic_music: Sustained cello notes at a slow tempo with widely spaced piano tones, gradually decreasing in volume.
```
> 中文要点：先写首帧指令（第一行），再以 `<Picture 1>` 的**主体/构图/场景**为起点，描述后续发展；保持人物外观/服装/座位/车厢布局一致。

**Case 3 — FL2VA（首+尾帧，8 秒单镜头）**
```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot 1) aligns with the 8.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, a rain-soaked cyclist begins in the position and framing established by Picture 1, holding a closed black umbrella beside a silver bicycle. The camera pulls out with small amplitude at slow speed as she releases the bicycle handle, raises the umbrella above her shoulder, and presses the runner upward until the canopy opens. Water rolls from the expanding fabric while she steps beneath it, rotates the handle into the final angle, and settles into the pose, spacing, and composition established by Picture 2 at the end of the shot.

overall_soundscape: Rain falls steadily on the pavement, followed by the metallic click of the umbrella runner and the soft snap of the canopy opening. Water drips from the bicycle frame as distant traffic passes.

non_diegetic_music: N/A
```
> 中文要点：两图分别锚定开头和结尾；正文不重复两张静态图描述，而是给**连接它们的运动路径**。FL2VA 一般偏好单镜头以连续插值；仅明确需要时多用镜头；尾帧须由最后的 `[Shot N]` 抵达。结构：首帧状态 → 可观察中间变化 → 差异逐步收窄 → 尾帧状态。

**Case 4 — L2VA（尾帧，6 秒单镜头）**
```text
How the reference pictures align with the target video — <Picture 1> (from [Shot 1]) aligns with the 6.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Live-action, cinematic, a close shot begins with an intact drinking glass near the edge of a dark wooden table, while the same hand and sleeve visible in <Picture 1> approach from the right. The camera pushes in with small amplitude at slow speed as the fingertips strike the rim. The glass tips, falls, and hits the floor with a sharp impact; cracks spread through it as fragments slide outward. Toward the end, the moving pieces lose momentum and settle into the exact broken arrangement, hand position, camera angle, lighting, and final composition established by <Picture 1>.

overall_soundscape: Fingertips tap the glass before it scrapes across the tabletop, falls, and breaks with a sharp crash. Small fragments scatter and gradually stop sliding across the floor.

non_diegetic_music: A low electronic pulse at a slow tempo, ending immediately after the glass breaks.
```
> 中文要点：图只锚定最后瞬间；先推断一个兼容的更早状态，再让动作/物体状态/构图逐渐"落"到参考图。结构：合理前置状态 → 明确动作与过渡路径 → 末镜逐渐收敛 → 尾帧落地。

---

## 2. Full-Reference Mode（全参考模式）— 图/视频/音频参考 + 精准编辑

用于：上传参考图/视频/音频，或做角色/物体/背景/光影替换、台词/音色修改等精准编辑。输出是**六段固定结构**（全英文写，仅 `<d>` 内台词/歌词和画面可见文字保留原文语言）。

### 2.1 六段结构（顺序固定）

| 段（英文原文） | 中文 | 作用 |
|---|---|---|
| `subject_definitions` | 参考定义 | 定义被引用的内容与标签 |
| `summary` | 摘要 | 概括任务类型 / 目标视频 / 主要参考关系 |
| `retention_analysis` | 保留分析 | 每个参考内容如何被保留/转移/复用 |
| `detailed_description` | 详细描述 | 按播放顺序描述视觉/动作/镜头/声音/台词 |
| `overall_soundscape` | 整体声景 | 环境音/物理音 |
| `non_diegetic_music` | 非剧情音乐 | 仅观众可听配乐 |

### 2.2 四类参考标签（Reference Labels）

| 标签（英文原文） | 中文 | 用法 |
|---|---|---|
| `<Subject N>` | 可复用可见内容 | 人/动物/物、场景/背景、服装/道具/UI/特效、风格/动作/表情/姿态。是"将在目标视频中实际使用的內容单元"，非源文件本身 |
| `<Picture N>` | 参考图 | 作为某镜首帧/关键帧/尾帧/编辑关键帧/构图锚；或作为分镜参考 |
| `<Video N>` | 参考视频 | 编辑源、续拍起点、或整体时间结构（运镜/切镜/节奏） |
| `<Audio N>` | 参考音频 | 复制或引用的音频信号 |

- 标签一旦分配，在 `subject_definitions` / `summary` / `retention_analysis` / `detailed_description` / 音频段中**含义不变**。
- `<Subject N>` 可来自多张图/视频，组合说明各自提供什么：
  ```text
  <Subject 1> is the woman whose appearance comes from <Picture 1> and whose walking motion comes from <Video 1>.
  ```
- `<Picture N>` 仅当图本身作为帧/锚/分镜时才独立成行；若只用来定义角色/场景/服装/风格，在对应 `<Subject N>` 内引用即可。
- `<Video N>` 只留给"整视频关系"（编辑/续拍/结构）；视频里复用的人/物/动作仍归 `<Subject N>`。
- `<Audio N>` 若对应某说话人，复用其全局 `(Sx)`：`[Audio N] is the voice-timbre reference for <Subject X> (Sx).`

### 2.3 任务类型前缀（summary 开头，方括号）

| 任务类型（英文原文） | 中文 | 何时用 |
|---|---|---|
| `keyframe completion` | 关键帧补全 | 图作为首帧/关键帧/尾帧/编辑关键帧/具体帧锚 |
| `reference generation` | 参考生成 | 图/视频/音频为角色/场景/风格/动作/运镜/分镜提供生成指引（非具体帧、非被编辑/续拍的源视频） |
| `video editing` | 视频编辑 | 直接修改已有源视频（编辑图或图间生成不算） |
| `video continuation` | 视频续拍 | 新内容从源视频延续/扩展/过渡 |
| `audio reuse` | 音频复用 | 同一音频信号全部/部分复用 |
| `audio reference` | 音频参考 | 不直复信号，只参考音乐风格/音色/台词或歌词内容/音效质感/节奏/连续性 |

- 多关系用 `+` 组合不重复，如 `[video continuation + keyframe completion]`；编辑源视频且保留原音 → `[video editing + audio reuse]`。
- 视频编辑类 summary 以 `The target video is an edited version of <Video 1>.` 开头。

### 2.4 关系标记（Relationship Markers，固定英文值）

| 类别 | 标记（英文原文） | 中文 |
|---|---|---|
| 可见内容 | `fully_preserved` | 完全保留 |
| 可见内容 | `partially_preserved` | 部分保留（部分特征被改） |
| 可见内容 | `attribute_transfer` | 特征转移到另一可识别目标 |
| 可见内容 | `weak_reference` | 仅保留风格/类别/构图/氛围的宽泛相似 |
| 音频 | `fully_copy` | 完整源音频 = 目标完整终轨 |
| 音频 | `partially_copy` | 仅复制部分时间线/层，或复制后增删替 |
| 音频 | `reference` | 不复制信号，只参考音色/节奏/风格/台词/音效质感 |
| 音频 | `weak_reference` | 仅类别/氛围宽泛相似 |

```text
<Subject 1> (appears in [Shot 1], [Shot 3]): fully_preserved - ...
<Picture 2> ([Shot 1] first frame): fully_preserved - ...
<Video 1> (cut and pacing structure): weak_reference - ...
<Audio 1>: fully_copy - <Audio 1> is reused 1:1 as the target video's complete final audio track.
```

### 2.5 detailed_description 要点

- 生成任务通常 **350–500 英文词**；台词密集优先塞满台词时间线而非机械凑字数。视频编辑类随源视频复杂度伸缩。
- 风格在 `[Shot 1]` **之前**用 1–2 句英文开门：
  ```text
  The target video is in a cinematic, literary music-video style with soft lighting and a slightly desaturated color palette.
  [Shot 1] The scene opens in a crowded urban street...
  ```
- 标签在**首次清晰出现**处插入（描述其特征/画面位置/当前动作），后续镜头沿用同名标签不再重定义。
- 具体帧锚用自然短语：`the shot begins from <Picture 1>` / `the shot's keyframe corresponds to <Picture 2>` / `the shot ends on <Picture 3>`。
- 说话人/音频源：被引用主体实发声 → 同时写 `<Subject N> (Sx)`；同一主体画外音 → 同形式标 `off-screen`；说话人不对应已定义主体 → 稳定声音描述 + `(Sx)`。若人声只存在于直接复用的 BGM/完整音轨里、无具体人产生 → 用 `<Audio N>` 作可听源，**不要**另造 `(Sx)`。

### 2.6 完整官方示例（咖啡店 Samoyed 案例，原样保留英文）

```text
subject_definitions:
<Subject 1> is the coffee-shop environment in <Picture 1>, featuring an exposed brick wall, an orange tufted sofa with patterned pillows, a neon sign, and a wooden coffee table.
<Subject 2> is the fluffy white Samoyed in <Picture 2>, <Picture 3>, and <Picture 4>, with thick white fur, pointed ears, a dark nose, and a curved tail.
<Subject 3> is the young blonde woman in <Video 1>, with long blonde hair and a light-pink button-down shirt with rolled-up sleeves.
<Subject 4> is the young man in <Video 2>, with short wavy brown hair and a dark-grey hoodie with drawstrings.
<Audio 1> is the voice-timbre reference for <Subject 3> (S1), containing a spoken English vocal layer.

summary:
[reference generation + audio reference] The target video shows <Subject 3> eating a cookie in <Subject 1>. <Subject 4> enters with <Subject 2>, which lunges toward the cookie. The three-shot exchange uses <Audio 1> as the voice-timbre reference for <Subject 3> and ends with a canned audience laugh.

retention_analysis:
<Subject 1> (appears in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - the exposed brick wall, orange tufted sofa, patterned pillows, neon sign, and wooden coffee table are retained.
<Subject 2> (appears in [Shot 1], [Shot 2]): fully_preserved - the Samoyed's thick white fur, pointed ears, dark nose, and curved tail are retained.
<Subject 3> (appears in [Shot 1], [Shot 2], [Shot 3]): fully_preserved - the blonde woman's identity, long hair, and light-pink shirt are retained.
<Subject 4> (appears in [Shot 1], [Shot 2]): fully_preserved - the young man's short wavy brown hair and dark-grey hoodie are retained.
<Audio 1>: reference - its vocal timbre guides the dialogue delivery of <Subject 3> without copying the original signal.

detailed_description:
The target video uses a realistic multi-camera sitcom style with warm indoor lighting.
[Shot 1] A medium shot establishes <Subject 1>, the coffee shop with its exposed brick wall, orange tufted sofa, patterned pillows, neon sign, and wooden coffee table. <Subject 3> (S1), the young woman with long blonde hair and a light-pink button-down shirt with rolled-up sleeves, sits on the sofa holding a chocolate-chip cookie. From the left, <Subject 4>, the young man with short wavy brown hair and a dark-grey hoodie with drawstrings, enters holding the leash of <Subject 2>, the thick-furred white Samoyed with pointed ears, a dark nose, and a curved tail. The dog lunges toward the cookie and pulls the leash taut. <Subject 3> (S1) jerks her hand back and, using the clear youthful voice timbre referenced from <Audio 1>, exclaims with light annoyance, <d>[English] Hey! Watch your dog!</d> She closes her lips and guards the cookie while <Subject 4> pulls the dog back.
[Shot 2] At 00:03.000, the shot cuts to a close-up of <Subject 4> (S2), the young man in the dark-grey hoodie from Shot 1, sitting beside <Subject 3> on the sofa and holding <Subject 2> securely in his arms. <Subject 4> (S2) says in a casual young male voice with a playful tone and an easy conversational pace, <d>[English] He just likes cookies more than me.</d> He closes his mouth into an apologetic smile and strokes the dog's thick white fur.
[Shot 3] At 00:05.000, the shot cuts to a close-up of <Subject 3> (S1), the blonde woman in the light-pink shirt from Shot 1. Her annoyance softens as she looks toward the Samoyed. <Subject 3> (S1) replies in the same clear youthful voice referenced from <Audio 1> with an amused cadence, <d>[English] Well, he has good taste at least.</d> She smiles and raises the cookie in a small toast-like gesture. A classic canned audience laugh begins immediately after the line and continues through the final frame.

overall_soundscape:
Soft indoor coffee-shop room tone continues throughout the scene.

non_diegetic_music:
N/A
```
> 中文要点：六段齐全；`subject_definitions` 逐条定义标签与角色；`summary` 用 `[reference generation + audio reference]` 前缀；`retention_analysis` 用 `fully_preserved` / `reference` 标记；`detailed_description` 在 `[Shot 1]` 前先定喜剧风格，镜头内插入 `<Subject N> (Sx)`；`<d>` 内英文台词原样保留；笑声用 `continues through the final frame`。

---

## 3. 给中文用户的速查（飞书 `@` 写法 → 官方 API 字段映射）

| 你想做的（中文） | 海螺 App 端写法（cookbook） | 官方 API 结构化写法（本文件） |
|---|---|---|
| 锁脸 / 人物参考 | `@图片1 是人物参考` | `subject_definitions` 里 `<Subject 1> is the person in <Picture 1>...`；I2VA 首帧指令引用 `<Picture 1>` |
| 固定场景/服装 | `@图片2 是场景参考` | `<Subject 2> is the environment in <Picture 2>...` |
| 图做开头 | `@图片1 作为开头` | I2VA：`at 0.00 seconds ... <Picture 1> (from [Shot 1]) is fully referenced.` |
| 图做结尾 | `@图片2 作为结尾` | L2VA：`<Picture 1> (from [Shot N]) aligns with the S.SS-second mark` |
| 首尾两图 | `@图片1 开头 @图片2 结尾` | FL2VA 对齐指令 + 单镜头运动路径 |
| 视频运镜参考 | `@视频1 是运镜参考` | `<Video 1> is the camera-movement reference`（task type `reference generation`） |
| 续拍原视频 | `@视频1 接着拍` | `[video continuation]` + `<Video 1>` 结构引用 |
| 编辑原视频 | `@视频1 改一下` | `[video editing]` + `The target video is an edited version of <Video 1>.` |
| 音色克隆 | `@音频1 是音色参考` | `<Audio 1> is the voice-timbre reference for <Subject X> (Sx)`（`audio reference`） |
| 复用整段音频 | `@音频1 直接用` | `<Audio 1>: fully_copy - ...`（`audio reuse`） |
| 台词 | `@人物 说："……"` | `(S1) says: <d>[Chinese] ……</d>` |
| 跨镜头台词连贯 | 自然写 | `<scenetrans>` + `continues across the cut` |
| 屏幕字 | 自然写 | 英文双引号包裹原文，如 `"营业中"` |

> 简言之：**App 端用 `@` 随手标，API 端用本文件的字段/标签结构**。给外部 agent（Codex/Claude）写 H3 调用时，直接产出本文件的 `integrated_multimodal_description` / 六段结构即可，字段名即 API 真实 token。
