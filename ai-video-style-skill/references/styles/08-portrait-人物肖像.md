# 08 · 写真 / 人像摄影流派（Portrait & Photography Styles）

> 定位：以「人像摄影 / 写真」为审美的 AI 视频——厚涂脸、Y2K 千禧街头、黑红高端时尚、儿童 / 婚纱、萌宠写真，以及雾凇冷白光、窗台薄纱光、丁达尔斑驳等招牌光效。AIX Studio 与社媒最主力的人像赛道。
> 与「写实/真人」的区别：**这里的核心变量是流派（genre）而非真实度**——同一张脸换一套流派词表就是另一个世界。
> 与漫剧的区别：**单人单场、无叙事**，全部预算压在脸、光、质感上。
> 结构严格对齐 `_TEMPLATE.md` 15 模块。提示词正文英文，中文仅作注释。

---

## 00 范例（Examples）

### 例 1 · 厚涂插画脸（最易被洗，负向最关键）
```
Painterly portrait of a young woman with an introspective gaze, turning her head slowly toward the light,
medium close-up, three-quarter face angle, shallow depth of field,
soft directional window light from camera left, warm ochre key with cool shadow,
impasto oil painting, thick visible brushstrokes, palette-knife texture on the cheekbone,
visible canvas weave, painterly edges that dissolve into the background, limited muted palette,
subtle breathing motion, hair edge softly catching the light, brushstroke texture stays consistent
--no photorealistic, photograph, real skin pores, 3D render, CGI, smooth airbrushed skin, plastic sheen
```
> 厚涂第一铁律：**必须 negative 掉 `photorealistic` 与 `real skin pores`**，否则模型 90% 概率洗成写实人像；同时正向要给"笔触的物理证据"（palette-knife / canvas weave）。

### 例 2 · 黑红高端时尚写真
```
High-end editorial fashion portrait of a woman in a structured black satin dress against a deep red backdrop,
medium shot, 85mm, eye level, slight chin lift, confident direct gaze,
dramatic low-key lighting: hard beauty dish key from above, black flag negative fill on the shadow side,
crimson rim light separating the shoulder from the background, deep falloff to black,
black and red palette only, glossy satin with sharp specular highlights, matte skin with defined structure,
slow push-in with the model holding a still pose, fabric catching light as she breathes
--no soft flat lighting, pastel colours, cluttered background, plastic skin, blown-out highlights, extra fingers
```
> 黑红靠**减光**成立：`black flag negative fill` + `deep falloff to black` 比加多少光都重要。

### 例 3 · Y2K 千禧街头
```
Y2K street fashion portrait of a girl with butterfly hair clips and tinted micro sunglasses,
medium shot, 35mm, slight low angle, handheld energy, subtle camera sway,
on-camera flash look with hard shadow behind her, harsh direct flash falloff, night street as dark background,
metallic silver puffer jacket, low-rise denim, chunky platform shoes, glossy lip gloss,
early 2000s digital compact camera aesthetic, slight overexposure, chromatic fringing, low-fi digital noise,
date stamp in the corner, she flicks her hair and tilts her head to the camera
--no modern cinematic grading, soft beauty lighting, clean high-end retouch, film grain, moody teal-orange
```
> Y2K 的灵魂是**直闪 + 数码劣质感**：`on-camera flash + hard shadow + low-fi digital noise + date stamp`；写成"电影感"就立刻不 Y2K 了。

### 例 4 · 婚纱 / 浪漫柔光
```
Romantic wedding portrait of a bride in a flowing tulle gown standing by a tall window,
medium-wide shot, 85mm, eye level, very slow push-in, shallow depth of field,
soft backlit window light through sheer curtains, warm 3200K haze, glowing rim on the veil,
Tyndall light shafts through the dust, creamy highlight rolloff, pastel ivory palette,
delicate tulle with translucent layering, subtle lace texture, natural skin with soft glow,
veil drifting gently in a light draught, she looks down then lifts her gaze
--no harsh direct sunlight, dark moody grading, plastic skin, warped hands, extra fingers, garbled text
```
> 婚纱靠 `backlit + haze + creamy rolloff` 三件套；纱的通透（`translucent layering`）是全部质感来源。

### 例 5 · 萌宠写真馆
```
Studio pet portrait of a fluffy orange cat sitting on a pastel blue backdrop, looking directly into the lens,
close-up, 85mm, eye level with the animal, shallow depth of field,
soft high-key studio lighting: large octabox key, twin fill panels, gentle catchlight in both eyes,
individual fur strands separated and backlit, natural fur direction, wet nose specular,
pastel candy palette, clean seamless background,
the cat blinks slowly and its ears twitch, whiskers subtly moving
--no human hands, distorted anatomy, extra limbs, matted plastic fur, harsh shadows, cluttered background
```
> 宠物成败在**毛发分离度与眼神光**：`individual fur strands backlit` + `catchlight in both eyes` 缺一不可。

---

## 01 场景主题（Genre & Setting）

### 子流派词库
- `impasto painterly portrait` — 厚涂插画脸
- `high-end editorial fashion portrait` — 黑红 / 高端时尚写真
- `Y2K street fashion portrait` — Y2K 千禧街头
- `children lifestyle portrait` — 儿童写真
- `romantic wedding portrait` — 婚纱 / 情侣
- `studio pet portrait` — 萌宠写真馆
- `natural light lifestyle portrait` — 日系生活写真
- `cinematic character portrait` — 电影感人物写真
- `graduation / uniform portrait` — 毕业 / 制服写真
- `boudoir soft light portrait` — 私房柔光（保持得体）
- `documentary street portrait` — 街头纪实人像

### 子流派替换词表（一表换风格 · 本文件核心）
| 子流派 | 光效 tag | 色板 tag | 造型 tag | 质感 tag | 必带 negative |
|---|---|---|---|---|---|
| 厚涂脸 | `soft directional window light` | `muted ochre + cool shadow` | `simple neutral top` | `impasto, palette-knife, canvas weave` | `photorealistic, real skin pores, 3D render` |
| 黑红高端 | `hard beauty dish + black flag` | `black and red only` | `structured satin, sharp tailoring` | `glossy satin specular, matte skin` | `soft flat lighting, pastel colours` |
| Y2K 千禧 | `on-camera direct flash, hard shadow` | `metallic silver, hot pink, ice blue` | `butterfly clips, low-rise denim, tinted shades` | `low-fi digital noise, chromatic fringing` | `cinematic grading, film grain, clean retouch` |
| 儿童写真 | `soft diffused daylight, floor bounce` | `cream, sky blue, warm beige` | `knit cardigan, cotton dress` | `soft skin, downy hair backlight` | `heavy makeup, dramatic shadow, adult styling` |
| 婚纱 | `backlit window + haze, Tyndall shafts` | `ivory, blush, pale gold` | `tulle gown, lace veil` | `translucent tulle, creamy rolloff` | `harsh sunlight, moody dark grading` |
| 萌宠 | `high-key octabox + twin fill` | `pastel candy` | `collar / bowtie prop` | `individual fur strands, wet nose specular` | `human hands, matted plastic fur` |
| 日系生活 | `overcast soft light, window diffusion` | `low saturation, milky white` | `plain shirt, natural hair` | `fine film grain, gentle contrast` | `heavy contrast, saturated neon` |
| 电影感人物 | `single hard key + practical lamp` | `teal-orange or amber-black` | `coat, textured knit` | `anamorphic flare, 2.39:1` | `flat lighting, snapshot look` |

### 联动规则
- **换流派 = 整行替换**：光效 / 色板 / 造型 / 质感 / negative 五列必须同时换，只换一两列会出现"混血怪"。
- 流派词与 08 的参考锚点应同源（如 Y2K 配 `early 2000s digital compact`，不要配 `Kodak Portra`）。

---

## 02 景别构图（Shot Size & Composition）

### 景别词库
- `extreme close-up on the eyes` — 眼部大特写（情绪 / 眼神光）
- `close-up, head and shoulders` — 头肩特写（写真主力）
- `medium close-up, chest up` — 胸上中近景
- `medium shot, waist up` — 半身
- `medium-wide, knees up` — 七分身（展示服装）
- `full body with environment` — 全身带环境
- `over-the-shoulder from behind` — 背身回眸

### 角度 / 面向 / 焦段词库
- `three-quarter face angle` 三七侧脸（最显立体，最常用） · `full frontal` 正面（对称 / 强势） · `profile` 全侧
- `eye level` 平视 · `slight high angle` 微俯（显眼大脸小） · `slight low angle` 微仰（显气场）
- `chin slightly down, eyes up to lens` — 收下巴抬眼（万能显脸小）
- `50mm` 自然 · `85mm portrait lens` 人像标准（压缩 + 虚化） · `135mm` 强压缩 · `35mm` 环境人像
- `f/1.8 creamy bokeh` 奶油虚化 · `f/2.8 balanced` · `f/4 environment readable`

### 构图 → 用途 速查表
| 目的 | 景别 | 焦段 / 光圈 | 角度 | 附加 |
|---|---|---|---|---|
| 情绪 / 眼神 | `extreme close-up on the eyes` | 85mm / f/2 | eye level | `catchlight in the eyes` |
| 标准写真 | `close-up head and shoulders` | 85mm / f/1.8 | 三七侧脸 | `shallow depth of field` |
| 时尚硬照 | `medium shot` | 85–135mm / f/4 | slight low angle | `strong pose, negative space` |
| 展示服装 | `medium-wide knees up` | 50mm / f/2.8 | eye level | 全身比例正确 |
| 氛围环境 | `full body with environment` | 35mm / f/2.8 | eye level | 人占画面 1/3 以上 |
| 儿童 / 宠物 | `close-up` | 85mm / f/2 | **降到对象眼高** | 平视是关键 |

### 联动规则
- **儿童与宠物必须把机位降到对象眼高**（`eye level with the child / animal`），俯拍会显得居高临下且比例失真。
- 广角（35mm 以下）拍面部特写会鼻大脸变形：特写一律 85mm 起。
- 大光圈 + 三七侧脸时须写 `focus on the near eye`，否则焦点跑到鼻尖。

---

## 03 主体特征（Subject Features）

### 面部与形象词库
- `soft rounded features, gentle brow` 柔和五官 · `sharp cheekbones, defined jawline` 立体骨相
- `almond eyes with clear catchlight` 杏眼带眼神光 · `full lips with natural texture` 自然唇纹
- `freckles across the nose bridge` 鼻梁雀斑（真实感加分项）
- `natural skin texture with visible pores` 真实肤质 · `fine baby hairs along the hairline` 碎发（写实关键细节）
- `long straight black hair with soft sheen` / `loose wavy hair with volume` / `short bob with clean edge` — 发型

### 儿童 / 宠物专用
- `round toddler proportions, large forehead ratio` 幼儿头身比 · `downy hair backlit into a halo` 绒毛光晕
- `chubby cheeks with natural blush` 婴儿肥 · `natural unposed gesture` 自然非摆拍动作
- `fluffy long-haired cat with individual strand separation` 长毛猫毛丝分离 · `wet nose specular highlight` 湿鼻反光
- `expressive ears and whiskers` 耳与胡须（宠物表情全靠这两处）

### 一致性锚点
- `same face across shots, reference image guided` 跨镜同脸 + 参考图
- `consistent makeup and hairstyle` 妆发一致 · `identical accessory (e.g. pearl earring)` 具名配饰
- `facial structure locked` 面部结构锁定

### 联动规则
- **写实人像必带"不完美"**：`visible pores` + `baby hairs` + `freckles` 任选两项，否则出现蜡像脸。
- 厚涂 / 插画路线则**必须删掉**上述写实肤质词，改写 `painterly skin, brushstroke shading`。
- 手部是最高风险区：能不入画就不入画；必须入画时写 `hands relaxed, fingers separated, five fingers`。

---

## 04 服装造型（Styling & Makeup · 选读）

- `structured black satin dress with sharp shoulder` 硬挺缎面（高端）
- `metallic silver puffer jacket, low-rise denim` Y2K 银色羽绒 + 低腰牛仔
- `flowing tulle gown with lace veil` 婚纱薄纱与蕾丝
- `oversized knit cardigan in cream` 奶油色针织（日系 / 儿童）
- `crisp white shirt, minimal jewellery` 白衬衫极简
- `school uniform with pleated skirt` 制服百褶
- 妆容：`clean glowing skin makeup` 清透妆 · `bold red lip, sharp liner` 红唇眼线（黑红）· `glossy lip and frosted eyeshadow` 唇蜜 + 冷调眼影（Y2K）· `no visible makeup, natural brows` 素颜（儿童 / 日系）

### 联动规则
- 妆容浓度必须与流派匹配：儿童 / 日系写 `no visible makeup`，黑红写 `bold red lip`；错配立刻违和。
- 面料与 09 呼应：`satin` → `sharp specular`；`tulle` → `translucent layering`；`knit` → `visible rib texture`。

---

## 05 光影氛围（Lighting & Mood · 本类核心）

### 招牌布光词库（AIX 高频光效）
- `soft window light through sheer curtain` — 窗台薄纱光：最万能的柔光
- `Tyndall light shafts through dust` — 丁达尔斑驳光：氛围感天花板
- `cold white misty light (rime aesthetic)` — 雾凇感冷白光：清冷高级
- `hard beauty dish from above with black flag fill` — 美人碟 + 黑旗：时尚硬照
- `on-camera direct flash with hard shadow` — 直闪：Y2K / 街头
- `golden-hour backlight with hair halo` — 夕阳逆光发丝光
- `wheat-field rim light (麦芒逆光)` — 麦芒逆光：草叶发光
- `dappled light through leaves` — 树影斑驳
- `single practical lamp as motivated key` — 画内实用光源（电影感）
- `ring light with round catchlight` — 环形光（美妆 / 社媒）
- `high-key octabox with twin fill` — 高调柔光（儿童 / 宠物）

### 光效 × 情绪 × 流派 速查表
| 光效 | 情绪 | 主色温 | 适配流派 |
|---|---|---|---|
| `soft window + sheer curtain` | 温柔、私密 | 4000K 暖白 | 日系、婚纱、私房 |
| `Tyndall shafts` | 神性、回忆 | 3200K 暖 | 婚纱、文艺、儿童 |
| `cold white misty (rime)` | 清冷、疏离 | 7000K 冷 | 高级感、雪景、时尚 |
| `hard beauty dish + black flag` | 强势、高级 | 5000K 中性 | 黑红、时尚硬照 |
| `direct on-camera flash` | 生猛、街头 | 5600K 直白 | Y2K、纪实 |
| `golden-hour backlight` | 温暖、怀旧 | 3000K 强暖 | 情侣、毕业、生活 |
| `dappled leaf light` | 自然、清新 | 5000K | 儿童、日系 |
| `practical lamp key` | 电影、叙事 | 2700K 钨丝 | 电影感人物 |
| `high-key octabox` | 干净、可爱 | 5600K | 儿童、萌宠、电商 |

### 眼神光规则（Catchlight · 人像成败线）
- 必写 `clear catchlight in the eyes`；无眼神光的人像一律显死。
- 光源形状决定眼神光形状：`octabox` → 八角；`ring light` → 圆环；`window` → 方形。可显式写出。
- 宠物必须 `catchlight in both eyes`，单眼有光会显得瞎一只。

### 联动规则
- 逆光类（`backlight / rim`）必须配 `haze / mist in the air`，否则光边生硬无空气感。
- 低调（low-key）靠 `black flag negative fill` 造，不是靠"少写光"。
- 冷白雾凇与暖金逆光互斥，二选一。

---

## 06 动作运动（Motion & Camera · 视频核心，最详尽）

### 6.1 静态级运动（写真的主战场）
- `breath-level subtle motion, chest rising slowly` — 呼吸级起伏（静态人像保命项）
- `natural blink at irregular intervals` — 不规则自然眨眼（等间隔眨眼会显机械）
- `hair strands drifting in a light draught` — 发丝轻拂
- `eyelashes fluttering slightly` — 睫毛微颤
- `catchlight shifting as the head micro-turns` — 眼神光随微转移动
- `fabric settling, veil breathing` — 衣料 / 头纱轻微起伏
- `dust motes floating through the light shaft` — 光柱浮尘

### 6.2 动态级运动（人物动作）
- `slowly turning the head toward the light` — 缓慢转头向光（写真第一动作）
- `looking down then lifting the gaze to lens` — 垂眸后抬眼（情绪三段式）
- `hair flick with a head tilt` — 甩发侧头（Y2K / 时尚）
- `tucking hair behind the ear` — 别发（自然生活感）
- `stepping forward and settling into a pose` — 上前定势（时尚）
- `laughing then settling back to a soft smile` — 笑后回落（儿童 / 生活）
- `a child running toward camera, unposed` — 儿童奔跑（抓拍感）
- `the pet blinks slowly and its ears twitch` — 宠物慢眨 + 耳动

### 6.3 镜头运动（Camera Move）
- `very slow push-in` — 极缓推（写真最稳的运镜）
- `locked-off static with subject motion only` — 锁死机位，只有人在动
- `slight parallax drift` — 轻微视差漂移（增加立体）
- `lateral slider revealing the profile` — 横移揭示侧脸
- `rack focus from foreground bokeh to the eyes` — 前景虚化移焦到眼睛
- `handheld micro-sway` — 手持微晃（街头 / Y2K）
- `orbit quarter-arc around the subject` — 四分之一环绕（时尚）

### 6.4 招牌运动（Signature Moves）
- `slow push-in + head turn to the light` — 写真万能开场
- `downcast gaze → lift to lens → soft smile` — 情绪三拍，最能出片
- `hair flick on the beat with handheld sway` — Y2K / MV 感
- `veil drifting while the camera holds still` — 婚纱：人不动、纱在动
- `rack focus from petals to the eyes` — 前景转焦，文艺感
- `flash-frame cut between two poses` — 直闪硬切（时尚 / Y2K）

### 6.5 情绪三段式表演节奏
| 阶段 | 时间占比 | 动作 | 关键 tag |
|---|---|---|---|
| 起 | 0–25% | 静止 / 垂眸 | `still, gaze downcast, breath-level motion` |
| 承 | 25–65% | 抬眼 / 转头 | `lifts the gaze slowly, head turns toward light` |
| 转 | 65–100% | 情绪落点 | `a soft smile settles` / `eyes hold the lens` |

### 6.6 运动强度 → 稳定 / 模糊 速查表
| 场景 | 运动 tag | 模糊 | 常见翻车 |
|---|---|---|---|
| 静态写真 | `breath-level subtle motion` | `no motion blur` | 完全静止像照片；或脸抖变形 |
| 缓慢转头 | `slow head turn` | `minimal blur` | 转头中途脸变成另一个人 |
| 甩发 | `hair flick` | `slight blur on hair only` | 头发糊成一团 / 穿透肩膀 |
| 儿童奔跑 | `running toward camera` | `slight blur on limbs` | 腿部畸变、滑步 |
| 宠物动作 | `ears twitch, slow blink` | `no blur` | 毛发抖动闪烁 |

### 联动规则
- **人像视频宁静勿动**：动作越大，脸越容易崩。默认 `slow` + `subtle`。
- 转头类动作必须同时写 `same face throughout, facial structure locked`，这是人像视频最大风险点。
- 手持晃动只用于 Y2K / 街头；其余流派一律排除。

---

## 07 表情表演（Expression & Gaze · 选读）

### 表情词库
- `soft closed-lip smile` 抿嘴微笑 · `confident direct gaze` 自信平视
- `introspective downcast gaze` 内省垂眸 · `slight chin lift, cool detachment` 抬颌疏离（时尚）
- `unguarded laugh, eyes crinkling` 真笑（眼角有纹才真）
- `lips parted, breath held` 微启唇（私房 / 情绪）
- `natural unposed expression` 非摆拍（儿童 / 纪实）
- `serene closed eyes` 闭眼安然（婚纱 / 美妆）

### 视线方向
- `eyes to lens` 看镜头（连接感） · `gaze off-camera left` 视线出画（叙事感）
- `looking through the window` 望向窗外 · `eyes lowered to the hands` 垂视手部

### 联动规则
- 真笑必须写 `eyes crinkling`，只写 smile 会得到僵硬假笑。
- 儿童忌 `posed expression`，必须 `natural unposed`；成人时尚则相反。
- 眼神特写必配 05 的 `clear catchlight`，否则眼睛无神。

---

## 08 风格滤镜（Art Direction & Photographic Look）

### 美学方向词库
- `impasto oil painting portrait` — 厚涂油画（插画路线）
- `high-end editorial retouch` — 高端时尚精修
- `early 2000s digital compact aesthetic` — Y2K 数码劣质感
- `Japanese natural-light lifestyle` — 日系自然光
- `Korean clean beauty aesthetic` — 韩系清透
- `cinematic character portrait` — 电影感人物
- `documentary black and white` — 纪实黑白
- `soft romantic dreamcore` — 浪漫柔梦（婚纱）

### 胶片 / 镜头质感词库
- `Kodak Portra 400 colour response` 柔和肤色胶片 · `Cinestill 800T halation` 夜色红晕
- `fine film grain` 细颗粒 · `low-fi digital noise` 数码噪点（Y2K，与胶片颗粒互斥）
- `anamorphic lens flare` 横向炫光 · `soft focus filter, slight glow bloom` 柔焦
- `chromatic fringing` 色边（Y2K）· `creamy highlight rolloff` 高光柔和过渡
- `2.39:1 letterbox` 宽银幕 · `slight vignette` 暗角

### 参考锚点
| 锚点 tag | 视觉签名 | 适用流派 |
|---|---|---|
| `Peter Lindbergh black and white` | 纪实时尚、素颜、粗颗粒 | 高端黑白 |
| `Paolo Roversi painterly light` | 柔雾、油画感、暗调 | 厚涂、婚纱 |
| `Nick Knight bold editorial` | 高饱和、硬光、强造型 | 黑红时尚 |
| `Terry Richardson direct flash` | 白背景直闪、生猛 | Y2K、街头 |
| `Rinko Kawauchi soft daylight` | 日系过曝柔光、生活切片 | 日系、儿童 |
| `Annie Leibovitz cinematic portrait` | 布景叙事、戏剧光 | 电影感人物 |
| `Sargent oil portrait brushwork` | 萨金特笔触、皮肤高光 | 厚涂 |
| `Wong Kar-wai neon melancholy` | 霓虹暖红、慢门拖影 | 夜景人像 |

### 联动规则
- **一条 prompt 只锚一个摄影 / 画家签名**，两个同写会互相抵消。
- `film grain` 与 `low-fi digital noise` 互斥：胶片走前者，Y2K 走后者。
- 厚涂路线的锚点必须选画家（Sargent / Roversi），选摄影师会拉回写实。

---

## 09 材质细节（Skin, Hair & Fabric · 选读）

### 肤质 / 发质词库
- `natural skin texture with visible pores` 真实毛孔 · `subtle skin imperfections, no airbrushing` 保留瑕疵
- `matte skin with defined structure` 哑光有骨相（时尚） · `dewy glowing skin` 水光肌（韩系）
- `painterly skin with brushstroke shading` 笔触皮肤（厚涂专用）
- `individual hair strands with soft sheen` 发丝分离带光泽 · `fine baby hairs along the hairline` 碎发
- `downy hair backlit into a halo` 绒毛光晕（儿童） · `individual fur strand separation` 毛丝分离（宠物）

### 织物词库
- `satin with sharp specular highlights` 缎面硬高光 · `translucent tulle layering` 薄纱透叠
- `wool knit with visible rib texture` 罗纹针织 · `cotton with soft matte diffusion` 棉质漫射
- `metallic puffer with crinkled specular` 金属羽绒褶皱高光
- `lace with fine open-work detail` 蕾丝镂空

### 「防蜡像脸」检查表
| 症状 | 原因 | 修法 |
|---|---|---|
| 皮肤像塑料 | 过度磨皮 | 加 `visible pores, subtle imperfections, no airbrushing` |
| 脸像面具 | 缺发际线细节 | 加 `fine baby hairs along the hairline` |
| 眼睛无神 | 无眼神光 | 加 `clear catchlight in the eyes` |
| 头发像头盔 | 无发丝分离 | 加 `individual hair strands, flyaway hairs` |
| 厚涂被洗写实 | 正向缺笔触物理 | 加 `palette-knife texture, visible canvas weave` |
| 宠物毛像毡 | 无背光分离 | 加 `individual fur strands, backlit rim on fur` |

### 联动规则
- 写实流派：肤质词**必选**，是与"AI 假脸"划清界限的唯一手段。
- 厚涂流派：肤质词**必删**，改用笔触词，否则两套语义打架。

---

## 10 后期特效（Post & Grading · 选读）

- `soft bloom on highlights` 高光柔光晕 · `halation around light sources` 光源红晕
- `subtle skin retouch, texture preserved` 保留质感的精修
- `pastel colour grade` 粉调 · `teal-orange cinematic grade` 电影冷暖对撞
- `black and white with deep contrast` 高反差黑白
- `light leak on the frame edge` 边缘漏光（复古）
- `date stamp in the corner` 日期戳（Y2K 专属）
- `paper / canvas texture overlay` 纸纹 / 画布叠加（厚涂）

### 联动规则
- `subtle skin retouch, texture preserved` 是安全的美化写法；只写 `retouched` 会直接变塑料。
- 调色与流派必须一致：Y2K 忌 `teal-orange cinematic grade`，日系忌高反差。

---

## 11 道具场景（Props & Backdrop · 选读）

- `seamless studio backdrop in deep red / pastel blue` 无缝背景（时尚 / 宠物）
- `tall window with sheer curtain` 高窗薄纱（万能柔光源）
- `foreground petals or leaves out of focus` 前景虚化花叶（移焦用）
- `vintage flip phone and butterfly clips` 翻盖手机 + 蝴蝶夹（Y2K）
- `wooden floor with a single chair` 木地板与椅子（极简）
- `bouquet and lace veil` 捧花与头纱（婚纱）
- `knitted blanket and soft toy` 针织毯与玩偶（儿童）
- `pet bowtie or collar prop` 宠物领结

### 联动规则
- 前景虚化物（`foreground bokeh`）是提升"摄影味"最廉价的手段，配 `rack focus` 效果最好。
- 道具不超过 3 件；背景永远优先干净，人像的信息量应集中在脸上。

---

## 12 负向规则（Negative Prompt & Forbidden Combos）

### 通用 negative 词库
- `plastic skin, waxy face, over-airbrushed` — 蜡像脸（人像头号翻车）
- `face morphing, inconsistent face, changing identity` — 转头 / 跨帧变脸
- `extra fingers, malformed hands, fused fingers` — 手部畸变
- `dead eyes, no catchlight, misaligned pupils` — 无神眼 / 斜视
- `asymmetric distorted features, warped ear` — 五官畸变
- `helmet hair, no strand separation` — 头盔发
- `blown-out highlights, crushed blacks` — 曝光失控
- `cluttered distracting background` — 背景杂乱
- `text watermark, garbled text` — 水印 / 乱码
- `stiff frozen pose, no motion` — 完全静止

### 子流派专用 negative（**最关键一表**）
| 子流派 | 必须排除 | 不写会怎样 |
|---|---|---|
| **厚涂脸** | `photorealistic, photograph, real skin pores, 3D render, CGI, smooth airbrushed skin` | **90% 概率被洗成写实人像，笔触全失** |
| 黑红高端 | `soft flat lighting, pastel colours, snapshot look, busy background` | 变成普通棚拍，失去高级感 |
| Y2K 千禧 | `cinematic grading, film grain, clean high-end retouch, moody teal-orange` | 变成现代电影感，Y2K 味归零 |
| 儿童写真 | `heavy makeup, adult styling, dramatic shadow, sexualized posing` | 违和且不合规 |
| 婚纱 | `harsh direct sunlight, dark moody grading, plastic skin, warped hands` | 纱失透、脸失柔 |
| 萌宠 | `human hands, distorted anatomy, matted plastic fur, harsh shadows` | 毛发成毡、结构崩 |
| 日系生活 | `heavy contrast, saturated neon, dramatic rim light` | 变成时尚硬照 |
| 电影感人物 | `flat lighting, snapshot look, oversaturated` | 失去戏剧性 |

### 禁止组合表（Forbidden Combos）
| 冲突组合 | 后果 | 正确做法 |
|---|---|---|
| `impasto painterly` + `photorealistic / real skin pores` | 厚涂被洗成写实（本类第一翻车） | 厚涂必须 negative 掉全部写实词 |
| `impasto painterly` + `ray tracing / 3D render` | 出现塑料油画怪 | 厚涂只配 `canvas weave, brushstroke` |
| `film grain` + `low-fi digital noise` | 颗粒打架，画面脏 | 胶片与 Y2K 二选一 |
| `high-key soft` + `dramatic low-key falloff` | 灰平无调性 | 明确取一种 |
| `close-up` + `35mm 或更广` | 鼻大脸变形 | 特写一律 85mm 起 |
| `f/1.8 bokeh` + 无 `focus on the near eye` | 焦点落鼻尖，眼睛虚 | 显式指定对焦眼 |
| 大幅头部动作 + 无 `facial structure locked` | 转头中途换脸 | 动作类必带锁脸锚点 |
| `handheld sway` + 婚纱 / 高端时尚 | 廉价抖动感 | 手持只留给 Y2K / 街头 |
| 儿童 / 宠物 + `high angle` | 居高临下、比例失真 | 降到对象眼高 |
| `retouched` 不加 `texture preserved` | 直接塑料脸 | 写 `subtle retouch, texture preserved` |
| `backlight` 无 `haze / mist` | 光边生硬无空气感 | 逆光必配介质 |

### 冲突避免总则
- 人像负向的两条主线：**防假脸**（塑料 / 蜡像 / 无神）与**防跑风格**（厚涂被洗、Y2K 被电影化）。
- 每条 prompt 的 negative 至少覆盖：肤质假 + 手部 + 脸漂移 + 流派专用 四组。

---

## 13 推荐模型（Model Mapping · 见 models.md）

| 需求 | 主推 | 备选 | 为何契合 |
|---|---|---|---|
| **写真主力 / 风格化人像** | **MiniMax H3** | PixVerse v5.6 | 风格化与手绘 / 插画感最强，成本最低之一，自带 6–10s 原生音频；写真多为短镜正合适 |
| **社媒竖屏 / Y2K / 潮流** | **PixVerse v5.6** | MiniMax H3 | 风格化与夸张审美强，竖屏友好、快且便宜，适合批量出社媒物料 |
| **厚涂 / 插画人像** | **MiniMax H3** | Vidu Q3 / Wan 2.7 | 非写实基底最不容易被洗成写实；Vidu Q3 非写实一致性强，Wan 2.7 风格化与艺术表现好 |
| **写实高端时尚 / 婚纱** | **Veo 3.1** | Kling 3.0 / Seedance 2.0 | Veo 光影景深与肤质最接近实拍；Kling 人体运动与头发布料垂坠正确 |
| **人体运动 / 甩发 / 走位** | **Kling 3.0** | Seedance 2.0 | 头发飘动与布料物理真实，是动作类人像最稳的 |
| **批量出片 / 多方案** | **Seedance 2.0** | PixVerse v5.6 | Fast 档 $0.022/s，跨帧一致性好，先探方向再提级 |
| **萌宠写真** | **MiniMax H3** | PixVerse v5.6 / Kling 3.0 | 毛发与风格化表现好；需要极致毛发保真时上 Kling O03 |
| **长时长 / 一致性要求高** | **Vidu Q3** | Wan 2.7 | 12–16s + 首尾帧精确控制起止姿态，跨镜同脸更稳 |
| **人像口播 / 数字人** | **HeyGen / Hedra** | HappyHorse 1.1 | 口播与多语数字人专线；HappyHorse 7 语口型可做角色向 |

### 选型口诀
- **越非写实 → 越往 MiniMax H3 / PixVerse / Vidu 走**（它们不会把风格拉回写实）。
- **越写实、越要肤质与光影 → 越往 Veo 3.1 / Kling 3.0 走**。
- **要锁姿态或跨镜同脸 → Wan 2.7 / Vidu Q3 首尾帧 + 参考图 I2V**。
- 人像永远优先 **I2V**：给一张定妆参考图，比任何文字描述都更能锁住脸。

---

## 14 组装公式（Assembly Formula）

### 槽位顺序
```
[01 子流派（对照替换词表整行取值）]
+ [02 景别 + 焦段 + 光圈 + 面向角度]
+ [03 面部特征 + 肤质 / 发丝细节 + 一致性锚点]
+ [05 招牌布光 + 色温 + catchlight]
+ [06 单一主动作 + 缓慢镜头运动 + 呼吸级微动]
+ [08 美学方向 + 摄影/画家锚点 + 胶片或数码质感]
+ (选读 3–5: 04 造型妆容 / 07 表情视线 / 09 材质 / 10 调色 / 11 道具背景)
+ [12 negative 段（肤质假 + 手部 + 脸漂移 + 流派专用 四组）]
→ 模型选择见 [13]
```

### 必选 / 选读
- **必选**：01 / 02 / 03 / 05 / 06 / 08 / 12 / 13 / 14
- **选读（每条取 3–5）**：04 造型 / 07 表情 / 09 材质 / 10 后期 / 11 道具
- **人像额外强制**：`clear catchlight in the eyes` 与 `facial structure locked` 视为必选，不可省。

### 最小可用示例（写实流派）
```
Natural-light lifestyle portrait of a young woman by a tall window,
close-up head and shoulders, 85mm, f/1.8, three-quarter face angle, focus on the near eye,
natural skin texture with visible pores, fine baby hairs along the hairline, clear catchlight in the eyes,
facial structure locked, same face throughout,
soft window light through a sheer curtain, warm 4000K key with cool ambient fill,
Japanese natural-light lifestyle, Kodak Portra 400 colour response, fine film grain,
very slow push-in, she looks down then lifts her gaze, breath-level subtle motion, hair strands drifting
--no plastic skin, waxy face, over-airbrushed, dead eyes, face morphing, extra fingers, cluttered background
```

### 最小可用示例（厚涂流派 · 注意负向差异）
```
Impasto painterly portrait of a young woman turning toward the light,
medium close-up, three-quarter face angle, shallow depth of field,
painterly skin with brushstroke shading, palette-knife texture on the cheekbone, visible canvas weave,
facial structure locked, brushstroke texture stays consistent,
soft directional window light, muted ochre key with cool shadow,
impasto oil painting, Sargent oil portrait brushwork, canvas texture overlay,
very slow push-in, subtle breathing motion, painterly edges dissolving into the background
--no photorealistic, photograph, real skin pores, 3D render, CGI, smooth airbrushed skin, plastic sheen
```

### 交付前检查清单
1. 流派替换词表是否**整行**替换（光/色/造型/质感/负向五列）？
2. 厚涂类是否 negative 掉 `photorealistic` 与 `real skin pores`？
3. 写实类是否写了 `visible pores` + `baby hairs`？
4. 是否有 `clear catchlight in the eyes`？
5. 特写焦段是否 ≥85mm 且指定了对焦眼？
6. 有头部动作时是否带 `facial structure locked`？
7. 儿童 / 宠物机位是否降到对象眼高？
8. negative 是否覆盖肤质 / 手部 / 脸漂移 / 流派四组？
