# 06 · 商业 / 电商 / 产品视频（Commercial / E-commerce / Product）

> 定位：面向品牌营销与电商转化的视频——产品 beauty shot、品牌 TVC、电商模特换装、珠宝 / 汽车 / 3C 精修、商业首尾帧。AIX Studio 工作流库中条目最多的商业化赛道。
> 与写实 CG 的区别：**目标不是"像真的"，而是"卖得动"**——材质必须可信、文字必须可读、姿态必须可控。
> 结构严格对齐 `_TEMPLATE.md` 15 模块。提示词正文英文，中文仅作注释。

---

## 00 范例（Examples）

### 例 1 · 珠宝微距 hero shot
```
A platinum diamond ring rotating slowly on a black velvet pedestal,
extreme macro close-up, 100mm macro lens, f/8 for edge-to-edge sharpness, slow turntable rotation,
three-point studio lighting: large softbox key, silver reflector fill, hard rim light for facet sparkle,
controlled specular highlights travelling across the brilliant-cut facets,
accurate metal: polished platinum with anisotropic reflection, no plastic look,
clean seamless dark gradient background, subtle dust-free surface, commercial beauty shot
--no plastic sheen, blurry facets, fake CGI glow, warped ring band, extra stones, text watermark
```
> 珠宝的全部说服力在**火彩**：`hard rim light + facet sparkle + slow turntable` 三件套；光斑必须"走"过刻面，静止即死。

### 例 2 · 汽车品牌大片
```
A matte-graphite electric sedan drives along a wet coastal highway at dusk,
low-angle tracking shot alongside the car, 35mm, stabilised dolly, consistent speed,
golden-hour backlight with cool blue ambient fill, wet asphalt reflecting the sky,
accurate car paint: metallic flake under clearcoat, crisp reflection of the horizon line sliding across the body,
cinematic commercial grading, anamorphic lens flare, 2.39:1 letterbox,
spray mist from tyres, shallow depth of field on the background
--no plastic car body, distorted wheels, floating car, mismatched reflections, garbled badge text
```
> 汽车靠**反射滑过车身**证明体积；`reflection sliding across the body` 比堆材质词更有效。

### 例 3 · 3C 数码 · 商业首尾帧
```
[First frame] A closed matte-black laptop resting on a light grey desk, centred, clean studio lighting.
[Last frame] The same laptop fully open, screen glowing with a crisp readable UI dashboard, same position and scale.
Locked-off camera with a very slow push-in between frames, 50mm, no perspective shift,
soft top softbox key plus two side strip lights, gentle gradient falloff on the background,
anodised aluminium with fine brushed grain, oleophobic screen with accurate reflection,
on-screen text readable and correctly spelled, product stays identical in both frames
--no morphing product, changing logo, warped keyboard keys, garbled UI text, plastic look
```
> 3C 的核心是**产品在首尾帧之间不能变形**：锁死机位 + 同尺寸 + 同光位，只让"状态"变化（开合/亮屏）。

### 例 4 · 电商模特换装（锁姿态）
```
A female e-commerce model standing in a neutral A-pose on a seamless light grey cyclorama,
full shot, 85mm, eye level, locked-off camera, model pose and body proportions unchanged,
the outfit changes from a beige trench coat to a navy wool blazer with a clean dissolve,
high-key studio lighting: large octabox key, twin fill panels, soft floor bounce, minimal shadow,
accurate fabric behaviour: wool drape with visible weave, coat hem settling naturally after the change,
same face, same hands position, same footwear, reference image guided
--no changing face, shifting pose, extra arms, melting fabric, warped hands, floating garment
```
> 换装的唯一目标是**只换衣、不换人**：`locked-off camera + pose unchanged + same face/hands` 必须同时出现。

### 例 5 · 品牌 TVC · 宫格拼贴节奏
```
A fast-cut brand montage of a skincare line: droplet impact, texture swirl, model applying cream, bottle hero,
rapid rhythmic cuts on a 4-beat grid, each shot 0.5 seconds, matched centre composition for graphic continuity,
bright airy high-key lighting, pastel brand palette of blush pink and cream white,
glossy glass bottle with clean refraction, silky cream texture with believable viscosity,
clean brand-colour wipe transitions between shots, minimal negative space for later typography
--no cluttered background, harsh shadows, muddy colour, garbled label text, plastic-looking bottle
```
> TVC 拼贴要**统一构图中心**，切换才不散；给后期文字预留 `minimal negative space`。

---

## 01 场景主题（Scene & Theme）

### 子类型词库
- `product hero shot` — 产品英雄镜：单品居中、极致打光
- `jewelry macro` — 珠宝微距：戒指、项链、腕表
- `automotive commercial` — 汽车商业片：路面、隧道、盐湖
- `consumer electronics showcase` — 3C 数码：手机、笔电、耳机
- `e-commerce model try-on` — 电商模特上身 / 换装
- `footwear on-foot shot` — 鞋类上脚
- `beauty and skincare texture shot` — 美妆膏体 / 质地镜
- `food and beverage commercial` — 食品饮料：倒液、拉丝、蒸汽
- `brand TVC montage` — 品牌 TVC 蒙太奇
- `packshot on seamless background` — 无缝背景包装镜
- `lifestyle in-context usage` — 场景化使用镜

### 品类 → 打光 / 背景 / 焦段 速查表
| 品类 | 打光 tag | 背景 tag | 焦段 | 招牌动作 |
|---|---|---|---|---|
| 珠宝 / 腕表 | `hard rim light for sparkle, softbox key` | `black velvet, dark gradient` | 100mm macro | `slow turntable` |
| 汽车 | `golden-hour backlight, large overhead strip` | `wet asphalt, salt flat, tunnel` | 24–35mm | `tracking alongside` |
| 3C 数码 | `top softbox, twin side strips` | `light grey seamless, gradient` | 50mm | `locked push-in` |
| 服装 / 模特 | `octabox key, twin fill, floor bounce` | `light grey cyclorama` | 85mm | `A-pose, pose unchanged` |
| 鞋类 | `low kicker light, rim on sole` | `concrete, seamless white` | 50mm | `step-in, foot pivot` |
| 美妆质地 | `bright high-key, backlit gel` | `pastel gradient, acrylic slab` | 100mm macro | `swirl, droplet impact` |
| 食品饮料 | `hard backlight for translucency, steam rim` | `dark wood, marble` | 50–100mm | `pour, splash crown` |

### 联动规则
- 品类一旦选定，**05 打光 / 09 材质 / 12 负向**必须成套切换：珠宝的硬光配到服装上会打出难看的死影。
- 商业片背景永远优先 `seamless / clean gradient`；杂乱背景会稀释产品且拉低转化。

---

## 02 景别构图（Shot Size & Composition）

### 景别与构图词库
- `packshot, product centred` — 正打包装镜，构图居中
- `extreme macro close-up` — 极微距：刻面、纹理、涂层
- `three-quarter product angle` — 四分之三角：最能交代体积
- `full shot of model` / `medium shot, waist up` — 模特全身 / 半身
- `detail insert (stitching, clasp, port)` — 细节插入镜
- `top-down flat lay` — 俯拍平铺（配件 / 套装）
- `negative space composition for typography` — 留白构图，给文字位
- `symmetrical centred composition` — 对称居中（高端感）

### 设备 / 焦段 / 光圈词库
- `locked-off tripod` 锁死机位（首尾帧必备） · `motorised slider` 电控滑轨 · `turntable rig` 转台
- `35mm` 环境+产品 · `50mm` 自然透视 · `85mm` 模特人像 · `100mm macro` 微距
- `f/2.8 shallow` 浅景深氛围 · `f/8 edge-to-edge sharp` 全清晰（产品主图）
- `focus stacking look` 景深合成感（微距全清）

### 构图 → 用途 速查表
| 用途 | 构图 | 焦段 / 光圈 | 备注 |
|---|---|---|---|
| 电商主图帧 | `packshot, centred, symmetrical` | 50mm / f/8 | 必须全清晰、无裁切 |
| 材质说服 | `extreme macro` | 100mm / f/8 + focus stacking | 只拍一个卖点 |
| 体积交代 | `three-quarter angle` | 50mm / f/5.6 | 配缓慢环绕 |
| 氛围种草 | `lifestyle in-context` | 35mm / f/2.8 | 产品仍需占画面 1/3 以上 |
| 上身展示 | `full shot of model` | 85mm / f/4 | 锁机位便于换装 |
| 广告版位 | `negative space composition` | 35mm / f/4 | 留白侧不放高频细节 |

### 联动规则
- 需要后期加字幕 / LOGO → 必须写 `negative space`，且该区域避免高频纹理与强反光。
- 微距 + 大光圈会让刻面失焦：微距一律 `f/8` 或 `focus stacking look`。
- 换装 / 首尾帧类必须 `locked-off tripod`，任何运镜都会破坏对齐。

---

## 03 主体特征（Product & Model）

### 产品形态词库
- `slim rectangular device with rounded corners` — 3C 常见形体
- `faceted brilliant-cut gemstone` — 明亮式切割宝石
- `cylindrical airless pump bottle` — 真空按压瓶（美妆）
- `frosted glass flacon with metal cap` — 磨砂玻璃香水瓶
- `sculpted sneaker silhouette with visible midsole` — 运动鞋轮廓
- `sedan silhouette with continuous shoulder line` — 轿车腰线
- `matte cardboard carton with spot-UV logo` — 哑光纸盒 + 局部 UV

### 模特特征词库（电商）
- `professional e-commerce model, natural proportions` — 自然比例
- `neutral A-pose` / `three-quarter stance` / `walking pose mid-stride` — 标准站姿 / 三七站 / 行走
- `hands relaxed at sides, fingers separated` — 手部放松分指（防并指畸变）
- `natural skin texture with visible pores` — 真实肤质（防塑料脸）
- `consistent body proportions across shots` — 跨镜身形一致

### 一致性锚点（商业专用）
- `product geometry locked` 产品几何锁定 · `same colourway` 同配色
- `logo placement unchanged` LOGO 位置不变 · `reference image guided` 参考图引导
- `pose unchanged, only garment changes` 只换衣不换姿态

### 联动规则
- 产品必须写 **1 个不可变的几何特征**（如 `continuous shoulder line` / `spot-UV logo on the front face`），否则跨帧会漂移。
- 模特手部是最高风险区：写 `fingers separated`，并在 12 补 `malformed hands` 负向。

---

## 04 服装造型（Wardrobe · 选读）

- `beige trench coat with belted waist` 米色风衣 · `navy wool blazer, structured shoulder` 海军蓝西装
- `silk slip dress with fluid drape` 真丝吊带（垂坠是卖点） · `knit sweater with visible rib texture` 罗纹针织
- `technical outerwear with matte ripstop` 机能外套 · `denim with authentic wash and selvedge edge` 丹宁水洗
- 状态：`crisply steamed` 熨挺 · `natural drape` 自然垂坠 · `hem settling after motion` 下摆回落

### 联动规则
- 面料必须与 09 材质呼应：`silk` → `soft specular sheen`；`wool` → `diffuse with visible weave`。
- 换装镜写 `hem settling after motion`，衣物才不会像贴图。

---

## 05 光影氛围（Lighting & Mood）

### 商业布光词库
- `large softbox key` — 大柔光箱主光：万能起手
- `octabox with grid` — 带蜂窝八角箱：可控溢光
- `strip light for edge definition` — 条形光勾边（3C / 瓶身）
- `hard rim light for sparkle` — 硬勾光出火彩（珠宝）
- `silver reflector fill` / `black flag negative fill` — 银反补光 / 黑旗吃光造立体
- `backlit gel for translucency` — 背透光（饮料 / 膏体）
- `low kicker from below` — 低位踢光（鞋 / 车轮）
- `high-key even lighting` / `low-key dramatic falloff` — 高调均匀 / 低调戏剧
- `Tyndall shaft through window` — 丁达尔窗光（生活场景）

### 情绪 × 打光 × 色温 速查表
| 品牌调性 | 打光 | 色温 / 色板 | 典型品类 |
|---|---|---|---|
| 高端奢华 | `low-key, hard rim, black negative fill` | `warm 3000K + deep black` | 珠宝、腕表、香水 |
| 科技冷感 | `strip lights, even top softbox` | `neutral 5000K + cool grey` | 3C、家电 |
| 清透干净 | `high-key, floor bounce` | `daylight 5600K + white` | 服装、母婴 |
| 温暖生活 | `Tyndall window light, warm bounce` | `warm 3200K + cream` | 家居、食品 |
| 潮流张扬 | `coloured gels, hard shadows` | `magenta-cyan contrast` | 潮鞋、饮料 |
| 自然户外 | `golden-hour backlight` | `3200K + cool ambient fill` | 汽车、户外装备 |

### 联动规则
- 反光材质（金属 / 玻璃 / 车漆）看的是**光源的形状**：必须写清 `large softbox` 或 `strip light`，写 "bright lighting" 等于没写。
- 想要立体感先加 `black flag negative fill`，加光不如减光。
- 高调（high-key）与 `dramatic shadow` 互斥，同写会得到脏灰片。

---

## 06 动作运动（Motion & Camera · 视频核心，最详尽）

### 6.1 静态级运动（产品自身）
- `slow turntable rotation, constant speed` — 匀速转台（最稳的产品运动）
- `subtle breathing highlight travel` — 高光缓慢游走（静物"活起来"的关键）
- `gentle fabric sway in still air` — 布料微摆
- `steam rising slowly` / `condensation droplet sliding` — 蒸汽上升 / 冷凝水珠下滑
- `liquid surface settling ripple` — 液面余波

### 6.2 动态级运动（产品与人）
- `pour with laminar liquid stream` — 层流倒液（饮料核心镜）
- `splash crown formation in slow motion` — 皇冠水花
- `cream swirl with peak formation` — 膏体旋涂拉尖
- `product unfolding / lid opening` — 开合展开（3C / 包装）
- `model turning to camera, hem following` — 模特转身带动下摆
- `step-in and foot pivot` — 上脚与转脚（鞋类）
- `car passing frame with reflection sweep` — 车过镜头带反射扫过

### 6.3 镜头运动（Camera Move）
- `locked-off static` 锁死机位（首尾帧 / 换装必用）
- `very slow push-in` 极缓推 · `slider dolly left to right` 滑轨横移
- `orbit around product at constant radius` 等半径环绕
- `macro rack focus from logo to texture` 微距移焦
- `crane-down to reveal product` 升降揭示
- `tracking alongside vehicle` 车侧跟拍
- `snap cut between matched compositions` 同构图硬切（TVC）

### 6.4 招牌运动（Signature Moves）
- `hero turntable + macro push-in combo` — 转台展示接微距，商业片万能结构
- `reflection sweep across the body` — 反射扫过（车 / 金属，证明体积）
- `first-last frame state change with locked camera` — 商业首尾帧：机位不动、只变状态
- `outfit dissolve with pose held` — 换装溶解、姿态保持
- `beat-grid montage, 0.5s per shot` — 宫格 TVC 节奏

### 6.5 商业首尾帧工作法（First–Last Frame Workflow）
| 步骤 | 要点 | 关键 tag |
|---|---|---|
| 1 定首帧 | 产品初始状态，构图/尺寸确定 | `product centred, locked-off tripod` |
| 2 定尾帧 | **只改一个变量**（开合 / 亮屏 / 换装 / 换季） | `same position and scale` |
| 3 写过渡 | 描述状态变化而非镜头变化 | `clean dissolve` / `smooth state change` |
| 4 锁一致 | 几何、配色、LOGO 全部锁死 | `product geometry locked, logo unchanged` |
| 5 校验 | 逐帧比对首尾，检查形变 | negative 补 `morphing product` |

### 6.6 运动速度 → 模糊 / 帧感 速查表
| 场景 | 速度 tag | 模糊 | 常见翻车 |
|---|---|---|---|
| 产品转台 | `constant slow rotation` | `minimal motion blur` | 忽快忽慢、反向抖动 |
| 液体倒入 | `laminar pour` | `slight blur on stream` | 液体变成果冻块 |
| 慢动作水花 | `slow motion 240fps look` | `crisp, no smear` | 慢动作却糊 = 矛盾 |
| 模特走位 | `natural walking cadence` | `slight blur on limbs` | 滑步（补 `feet planted`） |
| 汽车跟拍 | `steady constant speed` | `background motion blur only` | 车身也糊、车轮静止 |

### 联动规则
- **商业片默认"稳"**：除非明确要生活感，否则一律排除 `handheld shake`。
- 一条 prompt 只写一个主运动；`turntable + orbit` 同写会导致产品自旋加镜头旋，画面眩晕。
- 慢动作必须同时写 `crisp, no smear`，否则模型会用运动模糊冒充慢速。

---

## 07 表情表演（Model Performance · 选读）

- `confident neutral gaze to camera` 自信平视 · `soft closed-lip smile` 微笑不露齿
- `eyes closed, serene` 闭眼安然（美妆 / 香氛） · `subtle chin lift` 抬颌（时装）
- `natural blink, no staring` 自然眨眼（防死盯镜头）
- `hands presenting product at chest height` 手部呈现产品
- 表演三段式：`neutral hold` → `slight expression shift` → `settle back to neutral`

### 联动规则
- 电商模特忌 `exaggerated expression`，夸张表情会降低专业感与转化。
- 手持产品时必须写 `fingers separated, product not occluded`，否则手指糊成一团且挡住 LOGO。

---

## 08 风格滤镜（Art Direction & Grading）

### 商业美术方向词库
- `commercial beauty shot, advertising grade` — 广告级质感基调
- `clean minimal studio aesthetic` — 极简棚拍
- `luxury editorial, dark and glossy` — 奢侈品硬广
- `bright airy lifestyle` — 明亮生活感
- `techy futuristic product film` — 科技感产品片
- `Japanese muji-like restraint` — 无印良品式克制
- `bold pop colour blocking` — 撞色潮流

### 镜头 / 胶片质感
- `anamorphic lens flare` 宽银幕炫光（汽车/大片） · `2.39:1 letterbox` 电影比例
- `pristine digital clarity, no grain` 数字纯净（3C / 美妆主图）
- `fine film grain` 轻颗粒（时装 / 生活感） · `slight vignette` 暗角聚焦
- `crisp micro-contrast` 微反差锐利（质感说服力来源）

### 参考锚点
| 锚点 tag | 视觉签名 | 适用品类 |
|---|---|---|
| `Apple product film aesthetic` | 极简白 / 深空灰、精准打光、纯净无颗粒 | 3C、家电 |
| `Cartier jewellery film` | 低调红黑、硬勾光火彩 | 珠宝、腕表 |
| `Nike energy commercial` | 高对比、动感跟拍、汗感质地 | 运动、鞋服 |
| `Aesop muted editorial` | 低饱和大地色、柔窗光 | 护肤、香氛 |
| `Mercedes night drive film` | 夜路湿地反射、冷暖对撞 | 汽车 |
| `Zara lookbook studio` | 中性灰无缝背景、干净全身 | 服装电商 |

---

## 09 材质细节（Materials & Realism · 选读，商业核心）

### 材质词库（重点：排除塑料感）
- `polished platinum with anisotropic reflection` 抛光铂金 · `brushed aluminium with fine directional grain` 拉丝铝
- `metallic flake under clearcoat` 金属漆闪片 + 清漆 · `matte anodised finish` 阳极氧化哑光
- `clear glass with accurate refraction and caustics` 通透玻璃与焦散 · `frosted glass with soft light diffusion` 磨砂玻璃
- `full-grain leather with natural pore variation` 全粒面皮革 · `wool with visible weave and diffuse falloff` 羊毛织纹
- `silk with soft specular sheen` 真丝柔光泽 · `ceramic with subtle glaze unevenness` 陶瓷釉面
- `natural skin texture with visible pores` 真实肤质

### 「防塑料感」检查表
| 症状 | 原因 | 修法 |
|---|---|---|
| 金属像喷漆玩具 | 缺各向异性与环境反射 | 加 `anisotropic reflection, studio reflection card visible` |
| 玻璃像磨砂塑料 | 缺折射与焦散 | 加 `accurate refraction, caustics, clear glass` |
| 皮革像 PU | 纹理均匀无变化 | 加 `natural pore variation, uneven grain` |
| 肤质像蜡 | 过度磨皮 | 加 `visible pores, subtle skin imperfections` |
| 布料像贴图 | 无垂坠与厚度 | 加 `natural drape, fabric thickness, weave visible` |
| 整体发假 | 反射环境为空 | 加 `softbox reflection in the surface` |

### 联动规则
- 商业片必带 `no plastic look` 的正向对照：**写清"像什么材质"比写"不要塑料"更有效**。
- 反射材质必须交代**反射的内容**（`reflecting the softbox / horizon line / studio card`），否则模型会填涂灰色。

---

## 10 后期特效（VFX & Compositing · 选读）

- `clean brand-colour wipe transition` 品牌色块划擦转场 · `light leak transition` 漏光转场
- `particle sparkle accent on facets` 火彩粒子点缀（克制使用）
- `liquid morph between product states` 液态形变
- `subtle lens flare on rim highlight` 边缘炫光
- `on-screen readable UI overlay` 屏内可读 UI（走 Wan 2.7）
- `floating spec callout with negative space` 参数标注留白位

### 屏内文字 / LOGO 处理规则
- 需要**可读文字**（包装 LOGO、屏幕 UI、价格）→ 首选 **Wan 2.7**（12 国语言屏内文字）；否则一律**留白后期加**。
- prompt 内写文字时：只写**短词**且明确 `readable and correctly spelled`；长句必乱码。
- negative 必带 `garbled text, gibberish letters, distorted logo`。

---

## 11 道具场景（Props & Set · 选读）

- `black velvet pedestal` 黑丝绒展台（珠宝） · `acrylic riser block` 亚克力垫块
- `seamless cyclorama background` 无缝背景（模特） · `marble slab surface` 大理石台面
- `water droplets scattered on the surface` 表面水珠（清爽感） · `dry ice mist low to the ground` 低位干冰雾
- `reflection card just out of frame` 画外反光板（写出来能改善反射）
- `single plant shadow gobo on wall` 植物投影（生活感）

### 联动规则
- 道具**永远不能抢产品**：写 `props out of focus, product in sharp focus`。
- 珠宝忌浅色道具（吃火彩），一律深色绒面。

---

## 12 负向规则（Negative Prompt & Forbidden Combos）

### 通用 negative 词库
- `plastic look, fake CGI sheen, toy-like` — 商业片头号翻车
- `garbled text, gibberish letters, distorted logo, misspelled brand name` — 文字 / LOGO
- `morphing product, changing shape, inconsistent colourway` — 跨帧产品漂移
- `warped hands, malformed fingers, extra arms` — 模特手部
- `changing face, shifting pose, floating garment` — 换装类
- `cluttered background, distracting props, visible studio equipment` — 背景杂乱 / 穿帮
- `harsh blown-out highlights, crushed blacks` — 曝光失控
- `mismatched reflections, empty grey reflection` — 反射造假
- `handheld shake, unstable camera` — 商业片忌抖
- `oversharpened halo, heavy noise` — 后期过度

### 品类专用 negative
| 品类 | 必须排除 | 原因 |
|---|---|---|
| 珠宝 | `blurry facets, fake glow, extra stones, warped band` | 火彩与几何是全部说服力 |
| 汽车 | `distorted wheels, floating car, wrong badge, melted body line` | 车身线条与轮圈最易崩 |
| 3C | `warped keyboard keys, garbled UI text, wrong port count` | 规整几何禁不起变形 |
| 服装换装 | `changing face, shifting pose, extra arms, melting fabric` | 只换衣不换人 |
| 鞋类 | `warped sole, mismatched left-right shoe, floating foot` | 左右鞋必须一致 |
| 食品饮料 | `unappetising colour, jelly-like liquid, dirty splash` | 液体物理与食欲感 |

### 禁止组合表（Forbidden Combos）
| 冲突组合 | 后果 | 正确做法 |
|---|---|---|
| `high-key lighting` + `dramatic deep shadow` | 脏灰、无调性 | 二选一 |
| `macro close-up` + `f/2.8 shallow` | 刻面 / 纹理失焦 | 微距用 f/8 或 focus stacking |
| `locked-off tripod` + 任意运镜词 | 首尾帧错位、产品变形 | 换装 / 首尾帧只写 locked-off |
| `slow motion` + `heavy motion blur` | 语义矛盾 | 慢动作配 `crisp, no smear` |
| `turntable rotation` + `camera orbit` | 双重旋转、眩晕 | 只选一个旋转源 |
| 长句屏内文字 + 非 Wan 2.7 | 必乱码 | 留白后期加，或换 Wan 2.7 |
| `no plastic` 但无材质描述 | 模型无参照，仍然塑料 | 正向写清具体材质与反射内容 |
| `lifestyle handheld` + `packshot 主图` | 定位混乱 | 主图走棚拍锁机位 |
| 模特手持产品 + 无 `fingers separated` | 并指 / 六指 + 遮挡 LOGO | 显式写手部与遮挡规则 |

### 冲突避免总则
- 商业片的负向重点不是"防丑"，而是**防不可信**（塑料感）与**防不可用**（乱码 / 形变）。
- 任何要进电商详情页的帧，负向必带文字类与形变类两组。

---

## 13 推荐模型（Model Mapping · 见 models.md）

| 需求 | 主推 | 备选 | 为何契合 |
|---|---|---|---|
| **商业首尾帧 / 产品落帧** | **Wan 2.7** | Vidu Q3 | 首尾帧 + I2V 最强，且**屏内可读文字（12 国语言）**，是唯一能稳出包装 LOGO / 屏幕 UI 的选择 |
| **品牌 TVC / 汽车大片** | **Veo 3.1** | Sora 2 / Kling O03 | Veo 电影级写实 + 光影景深调色最佳，且**原生音频同步业界最佳**，广告音画一体 |
| **长镜头 / 叙事型广告** | **Sora 2** | Veo 3.1 | 时序连贯与物理强，最长 20s，适合一镜到底品牌片 |
| **极致保真 / 高端硬广** | **Kling 3.0 / O03** | Veo 3.1 | O03 视觉保真 2026 顶级，复杂反射与多主体连贯性好 |
| **批量出图 / 多方案比稿** | **Seedance 2.0** | PixVerse v5.6 | Fast 档 $0.022/s，物理与提示遵循好；先探 10 个方向再用 Veo 出终稿 |
| **产品干净 I2V** | **Luma Ray 3** | Seedance 2.0 | 输出干净无伪影、I2V 快，适合 5s 短产品镜 |
| **电商模特换装 / 多姿势** | **Wan 2.7** | Vidu Q3 / Kling 3.0 | 首尾帧锁姿态 + 参考图引导；Kling 布料垂坠正确 |
| **精确运镜（滑轨 / 环绕）** | **Runway Gen-4** | — | 运镜控制与运动笔刷行业最佳，可指定局部运动 |
| **数字人带货口播** | **HeyGen / Hedra** | — | 企业口播与多语数字人专线，非通用 T2V 赛道 |

### 组合工作流
- **比稿阶段**：Seedance 2.0 Fast 批量出 10 版构图 → 选定 → Veo 3.1 / Kling O03 出终稿。
- **详情页素材**：Wan 2.7 首尾帧锁产品 → 导出关键帧做主图 → 视频段单独剪。
- **文字**：能后期就后期；必须模型内出文字时锁定 Wan 2.7 并只写短词。

---

## 14 组装公式（Assembly Formula）

### 槽位顺序
```
[01 品类 + 场景定位]
+ [02 景别 + 焦段 + 光圈 + 构图（含留白位）]
+ [03 产品几何特征 / 模特姿态 + 一致性锚点]
+ [05 布光（写清光源形状）+ 色温 + 调性]
+ [06 单一主运动 + 镜头运动（首尾帧则写 locked-off）]
+ [08 美术方向 + 品牌参考锚点 + 镜头质感]
+ (选读 3–5: 04 服装 / 07 模特表演 / 09 材质 / 10 后期 / 11 道具)
+ [12 negative 段（必含材质假 + 文字乱 + 形变三组）]
→ 模型选择见 [13]
```

### 必选 / 选读
- **必选**：01 / 02 / 03 / 05 / 06 / 08 / 12 / 13 / 14
- **选读（每条取 3–5）**：04 服装 / 07 表演 / 09 材质 / 10 后期 / 11 道具
- **商业额外强制**：09 材质在**任何反光 / 透明 / 织物品类中视为必选**，不可省。

### 最小可用示例
```
Product hero shot of a frosted glass perfume flacon on a marble slab,
three-quarter angle, 100mm macro, f/8 edge-to-edge sharp, locked-off tripod with very slow push-in,
frosted glass with soft light diffusion and accurate refraction, brushed gold cap, no plastic look,
low-key luxury lighting: softbox key reflected in the glass, hard rim light, black flag negative fill,
warm 3000K palette, luxury editorial dark and glossy, crisp micro-contrast,
subtle highlight travelling across the bottle shoulder
--no plastic look, fake CGI sheen, garbled text, distorted logo, morphing product, cluttered background
```

### 交付前检查清单
1. 材质是否写了"像什么"而非只写"不要塑料"？2. 反射是否交代了反射内容？
3. 文字是否可读或已留白？4. 首尾帧机位是否锁死、只变一个变量？
5. 是否只有一个旋转 / 运动源？6. 手部与遮挡规则是否写清？
7. 留白区是否避开高频细节？8. negative 是否含材质 / 文字 / 形变三组？
