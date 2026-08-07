# 提示词模板库（Prompt Templates · 跨风格速查）

> 每个核心风格一套可直接套用的英文模板，含中文注释与关键词替换表。
> **权威完整版**：每个风格的 §00 范例 + §14 组装公式已写入 `references-参考资料/styles-风格库/NN-xxx.md`（15 模块深度，含词库/速查表/联动规则/禁止组合）。本文件是跨风格快速索引；做具体风格时优先读对应风格文件。
> 原则（来自 2026 评测共识）：
> 1. **英文正文 + 中文注释**：多数视频模型英文遵循度优于中文。
> 2. **结构化 prompt**：镜头类型 + 主体 + 动作 + 环境 + 光影 + 风格修饰 + 负向词。
> 3. **能用参考图就用参考图**：I2V / 首尾帧 比纯文本更稳。
> 4. **同 prompt 多生成 3–5 条再选**：AI 视频随机性强，迭代 > 精调单条。

---

## 模板 A — PV / 动漫 MV

```
[镜头类型] Close-up to wide shot transition,
[主体] a silver-haired idol girl in glowing stage costume,
[动作] executing a dynamic spin with hair and ribbons fluttering, beat-synced camera cuts every 2 beats,
[环境] neon-lit concert stage with volumetric haze and crowd silhouettes,
[光影] rim light in cyan and magenta, additive glow, chromatic aberration on impact frames,
[风格] anime PV, cel shading, vibrant color grading, 2.5D parallax background, speed lines,
[后期] motion blur on fast moves, snap zoom, impact shake,
[负向] blurry, deformed face, extra limbs, static camera, photorealistic, 3D render.
```
中文注释：用 `beat-synced` / `every 2 beats` 表达卡点；用 `rim light cyan/magenta` + `additive glow` 锁定 anime 打光；负向词务必排除 `photorealistic` 与 `3D render` 以免被洗成写实。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 主体 | virtual singer, game character, original avatar, band member |
| 动作 | leap, pose change, wink close-up, hair flip, choreographed dance |
| 环境 | festival stage, cyber city rooftop, school rooftop at sunset |
| 打光 | pink/blue dual tone, golden hour, stage spotlight |

---

## 模板 B — CG / 三维渲染

```
[镜头类型] Cinematic establishing shot, slow aerial drone pull-up,
[主体] a massive sci-fi fortress rendered in 3D,
[动作] energy shields ripple across the surface, secondary motion on antennae and banners,
[环境] orbiting asteroids, volumetric god rays through dust,
[光影] global illumination, ray-traced reflections on metal, depth of field, HDR environment,
[风格] 3D rendered, PBR materials, Unreal Engine 5 cinematic style, clean topology,
[后期] subtle film grain, lens flare,
[负向] melting geometry, broken topology, 2D, hand-drawn, noisy, low poly artifacts.
```
中文注释：明确写 `3D rendered, not real footage` 防止被当实拍；`clean topology, no melting` 规避几何融化；写实 CG 走 Veo/Sora，卡通 3D 走 Wan/Vidu。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 路线 | `toon shaded 3D, cel shaded, outline render`(卡通3D) / `PBR, subsurface scattering`(写实) |
| 主体 | product hero shot, character turntable, creature, vehicle |
| 运镜 | orbit around subject, camera fly-through, steadycam follow |

---

## 模板 C — MG / 动态图形

```
[镜头类型] Isometric camera push-in,
[主体] a clean vector logo assembling from scattered particles and lines,
[动作] kinetic typography pops in word by word with overshoot easing, data bars grow to full,
[环境] gradient background with subtle grid pattern and floating geometric shapes,
[光影] flat design, neon glow accents, glassmorphism panels,
[风格] motion graphics, after effects style, brand color palette (#0A84FF / #FF375F), loopable,
[后期] clean morph transitions, no film grain,
[负向] photorealistic, noisy texture, messy lines, illegible text, 3D render, live action.
```
中文注释：**MG 不要交给 Veo/Sora**，用 Animora/Runway/Pika/Wan。强调 `clean vector shapes, flat design, no noise`；需要屏内可读文字用 Wan 2.7（支持 12 国语言）。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 主体 | infographic, app UI mockup, chart animation, title sequence |
| 动作 | morph transition, path animation, stagger reveal |
| 风格 | `isometric explainer`, `tech promo`, `data visualization` |

---

## 模板 D — 手绘 2D 动画

```
[镜头类型] Side-scroll follow shot,
[主体] a small fox spirit drawn in ink and watercolor,
[动作] running with squash and stretch, anticipation before a leap, subtle boiling line,
[环境] hand-painted forest with paper grain, limited animation background,
[光影] soft watercolor washes, warm afternoon light,
[风格] hand-drawn animation, frame-by-frame, cel animation, limited palette, flat color,
[后期] paper grain, slight scan texture,
[负向] 3D render, CGI, smooth vector, photorealistic, clean digital anime.
```
中文注释：用 `frame-by-frame, hand-painted, boiling line` 锁定手绘感；负向必须排除 `3D render / CGI` 否则被洗成 3D anime。MiniMax H3 / Vidu Q3 对手绘-anime 友好。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 材质 | `pencil sketch`, `gouache`, `crayon`, `rough animation` |
| 动作 | `expressive facial animation`, `exaggerated pose`, `anticipation` |
| 氛围 | `studio ghibli`, `spider-verse hand drawn`, `vintage cartoon` |

---

## 模板 E — AI 漫剧 / 叙事型（国风玄幻 / 科幻 / 都市言情 / MV）

```
[镜头类型] Cinematic establishing shot pulling into a hero close-up,
[主体] a young cultivator in flowing white robe with ink-black hair,
[动作] drawing a glowing sword, energy qi surges as cloth and hair flutter, slow-motion impact on the strike,
[环境] an ancient floating mountain pavilion above a sea of clouds, distant lightning,
[光影] golden hour rim light, volumetric mist, ink-wash color grading with crimson accents,
[风格] cinematic AI donghua, cel shaded 3D, xianxia aesthetic, character consistency, multi-shot narrative,
[后期] subtle film grain, lens flare, energy blast VFX,
[负向] inconsistent character face, changing costume, deformed hands, melting geometry, photorealistic, 3D render artifacts, flickering.
```
中文注释：AI 漫剧的核心不是单条风格，而是**跨镜头一致性**——务必配合参考图 / 首尾帧 / 角色锁定（Wan 2.7、Vidu Q3、Seedance 2.0、Kling 3.0）。用 `cinematic donghua, xianxia, cel shaded 3D` 锚定国风审美；科幻换 `neon dystopia, sci-fi`，都市言情换 `campus romance, soft cinematic`。拆成 shot list 逐镜生成再剪。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 子类型 | `xianxia`(仙侠) / `neon dystopia, sci-fi`(科幻) / `campus romance`(都市言情) / `music video choreography`(MV) |
| 主体 | cultivator, mecha pilot, schoolgirl, warrior princess, spirit beast |
| 动作 | sword qi slash, energy blast, dance routine, emotional close-up |
| 打光 | golden hour rim, cold blue neon, soft pastel |

---

## 模板 F — 商业 / 电商 / 产品视频

```
[镜头类型] Macro push-in to hero turntable,
[主体] a diamond ring on a model's hand / a sneaker floating,
[动作] slow rotation revealing material detail, subtle light glint travels across surface,
[环境] clean studio backdrop with soft gradient,
[光影] softbox key light, rim light, clear glass refraction, accurate jewelry reflection,
[风格] commercial beauty shot, high-end product render, e-commerce hero, studio lighting,
[后期] subtle bloom on highlights, no noise,
[负向] plastic look, fake material, blurry reflection, deformed hand, watermark, extra fingers.
```
中文注释：商业产品视频核心是材质真实 + 干净打光；强调 `real material, accurate reflection, no plastic`；文字/LOGO 用 Wan 2.7 屏内文字或后期；电商换装用 I2V + 首尾帧锁姿态。汽车/大片走 Veo/Sora/Kling O03。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 主体 | `jewelry macro`, `car commercial low angle`, `sneaker on foot`, `3C gadget hero`, `cosmetic bottle` |
| 打光 | `window light`, `ring light`, `golden hour`, `studio softbox` |
| 风格 | `e-commerce model try-on`, `brand TVC 25-grid`, `product unboxing` |

---

## 模板 G — 建筑 / 室内写实渲染

```
[镜头类型] Slow aerial orbit then push through the window,
[主体] a modern concrete and glass villa,
[动作] camera glides along the facade, daylight shifts from morning to golden hour,
[环境] landscaped garden, interior visible through floor-to-ceiling glass,
[光影] natural daylight, soft shadows, ray-traced reflections on glass, global illumination,
[风格] architectural visualization, photoreal interior, Unreal Engine 5 archviz,
[后期] subtle film grain,
[负向] distorted structure, wrong scale, blurry glass, overexposed, messy text.
```
中文注释：建筑渲染靠参考图/草图 I2V 锁结构比例；强调 `architectural visualization, ray tracing`；玻璃幕墙用 `clear reflections`；尺寸标注后期加；模型走 Veo/Sora/Seedance/Wan。季节变换用 `season change morph`，毛坯转精装用 `before-after renovation morph`。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 主体 | `interior living room`, `skyscraper facade`, `renovated apartment`, `concrete staircase` |
| 动作 | `season change`, `before-after morph`, `walkthrough one-shot` |
| 风格 | `Twinmotion style`, `Blender architecture`, `sketch to realistic` |

---

## 模板 H — 写真 / 人像摄影

```
[镜头类型] Slow push-in to close-up,
[主体] a woman in a flowing dress,
[动作] hair drifts in wind, subtle breath, glance toward camera,
[环境] window with sheer curtain, soft morning light,
[光影] window light through sheer fabric, rim light, dreamy bokeh,
[风格] portrait photography, editorial fashion, softbox light, film grain,
[后期] gentle skin retouch,
[负向] deformed face, extra limbs, plastic skin, messy hair, cartoon.
```
中文注释：写实人像走 Veo/Kling/Seedance；厚涂风换 `impasto painting portrait, painterly, not photorealistic` 并走 MiniMax H3/Vidu/Wan；锁脸用参考图 + 首尾帧；Y2K 换 `Y2K fashion, cyber y2k`；萌宠换 `pet portrait studio`；婚纱换 `romantic wedding light`。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 子流派 | `impasto painting portrait`(厚涂) / `Y2K fashion, cyber y2k`(千禧) / `high-end editorial black red`(黑红) / `children portrait soft`(儿童) / `pet portrait studio`(萌宠) |
| 打光 | `雾凇冷白光`, `窗台薄纱光`, `丁达尔光影`, `麦芒夕阳逆光` |
| 氛围 | `dreamy bokeh`, `romantic light`, `film grain editorial` |

---

## 模板 I — 字体 / 排版动画

```
[镜头类型] Center frame,
[主体] the brand name rendered in liquid metal,
[动作] letters assemble stroke by stroke then glitch and settle, beat-synced pop,
[环境] dark gradient with floating particles,
[光影] neon rim on edges, specular highlight travel,
[风格] kinetic typography, liquid metal text, neon font, brand color,
[后期] glow bloom,
[负向] illegible text, garbled font, messy layout.
```
中文注释：屏内可读文字优先 Wan 2.7（12 国语言）；纯 T2V 文字易乱码，重要字幕/标题建议 AE/PR 后期；图形化字效可走 Animora。歌词字幕用 `beat-synced subtitles`，片名用 `title sequence, handwritten animation`。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 主体 | `lyric subtitle motion`, `brand slogan`, `movie title`, `handwritten name` |
| 动作 | `stroke drawing`, `glitch settle`, `liquid flow`, `beat-synced pop` |
| 风格 | `neon font`, `liquid metal text`, `glitch text`, `3D extruded type` |

---

## 模板 J — 二创整活 / 换脸 / 复刻 / 鬼畜

```
[身份参考图] reference image locks identity (face / original shot / character),
[镜头类型] shot-for-shot recreation, slow-motion tracking dolly,
[主体] a swordsman in tattered coat (design kept from original),
[动作] motion matched frame by frame, cloth and embers trailing,
[环境] burning corridor with falling debris, volumetric smoke,
[光影] teal-orange cinematic grade, hard key light through fire,
[风格] anime remake of live-action scene, cel shading, 2.5D, homage to the original,
[后期] film grain, slight chromatic aberration on impact,
[负向] composition drift, wrong angle, identity drift, deformed face, extra limbs, photorealistic, 3D render.
```
中文注释：二创整活本质是「参考图 / 原作驱动 + 场景或风格改写」。复刻必须附**原镜截图 I2V** 锁构图；换脸用**人脸参考图 + 首尾帧**（Wan 2.7 / Vidu Q3 / Kling 3.0，专业换脸走开源 insightface + Wan/Hunyuan）；鬼畜 loop 必须**首尾帧一致**才能无缝循环；风格迁移用 `anime-ify / pixel-ify` 并排原画风词（如 `photorealistic`）。真人换脸需授权或注明虚构 parody。详见 `styles-风格库/10-fanwork-二创整活.md`。

**关键词替换表**
| 槽位 | 可替换词 |
|---|---|
| 子类型 | `shot-for-shot recreation`(名场面复刻) / `face-swap remix`(换脸) / `seamless beat-synced loop`(鬼畜) / `crossover, universe fusion`(跨IP) / `anime-ify, pixel-ify`(风格迁移) / `meme to video`(梗图动起来) |
| 身份参考 | `celebrity face reference`(换脸) / `original shot screenshot`(复刻) / `character design reference`(联动) |
| 动作 | `motion matched frame by frame`(复刻) / `zoom punch loop`(鬼畜) / `fish-out-of-water movement`(跨IP反差) / `reaction face morph`(梗图) |

---

## 模板 K — MiniMax H3 三段式（多模态参考 / 编辑 / 带声音）

H3 提示词采用「参考素材说明 + 核心创意 + 画面过程说明」三段式；上传素材必须用 `@图片1/@视频1/@音频1` 标注用途。

```
【参考素材说明】@图片1：人物参考（锁这位女子的脸与汉服）；@视频1：动作参考（用里面的舞剑动作）；@音频1：情绪参考（古风配乐，音频整体复用）
【核心创意】10秒，16:9，一位穿汉服的年轻女子在樱花纷飞的庭院里舞剑，古典国风，电影质感，一镜到底。
【画面过程说明】
Shot 1 — 全景建立空间：樱花庭院，女子背对镜头立于树下，浅景深，飘落花瓣。
Shot 2 — 中景承载动作：女子拔剑起势，衣摆随转身扬起，运镜缓慢推进。
Shot 3 — 特写强调细节：剑光与面部特写交替，眼神专注；台词/吟唱与口型对齐。
Shot 4 — 回到中景收势：舞剑完毕归剑入鞘，花瓣落定；画面出现标题“剑舞·春”，字体清晰可读。
负向：现代元素、字幕水印、动画感、过曝、deformed face。
```

中文注释：
- **参考素材说明**：每个上传文件写清编号与用途——`人物参考(锁脸)` / `物体参考` / `场景参考` / `关键帧(首尾帧)` / `音色参考` / `风格参考` / `动作参考` / `运镜参考` / `视频编辑(增删改)`。未上传素材则整段跳过。
- **核心创意**：一句话锁主体+地点+事件+题材风格+特殊运镜（航拍/一镜到底/慢动作）；环绕运镜写 `truck left+pan right` 而非"环绕"。
- **画面过程说明**：按 shot 分段，每段含 景别+内容+运镜+动作+台词+音效；**台词长短对齐镜头**（避免 3s shot 说大段话致口型问题）；需出现的文字/Logo/标题**写出原文**。
- **三类模式**：①多模态融合（图+视频+音频各标用途）；②图生视频（1 张=首或尾帧，2 张=首+尾帧不自动切镜）；③纯文字（更具体，大全景+中景+特写分层）。
- **声音**：H3 所有结果自带原生双声道；直接写声场/对白/音效，跨 shot 的 J-cut/L-cut 明确写出即可；TTS 支持 11 种语言（含中文）。
- **避坑**：只写一段话没分段→按三段式拆；素材传了没说用途→补 `@图片1 是XX参考`；想脸一致没传图→必须传人物参考图并标「人物参考」；提示词太短（无素材时）→至少主体外观+场景+动作+风格。
- **深入**：`@标注` 完整 13 类分类、3 段公式子清单、镜头拆分铁律(J-cut/L-cut/台词对齐)、三类模式详例、6 条避坑表、真实示例（大字幕 MV / 国风舞剑 / 游戏 UI 分秒分镜 / 精准编辑）→ 见 **`references-参考资料/h3-prompt-cookbook-提示词实战手册.md`**（写 H3 提示词前必看）。

---

## 通用英文负向词库（按场景取用）

- 结构：`deformed, extra limbs, mutated hands, broken anatomy, melting geometry`
- 画质：`blurry, low resolution, noise, artifacts, jpeg artifacts`
- 风格污染：`photorealistic`(做非写实时), `3D render`(做手绘时), `live action`(做动画时)
- 运动：`static camera`(需要动时), `jittery, flickering, inconsistent character`

## 提示词语序建议
**主体 → 动作 → 环境 → 光影 → 风格修饰 → 镜头 → 后期 → 负向**。把最重要的风格词（如 `anime PV`、`hand-drawn`）放在靠前的显著位置，模型权重更高。
