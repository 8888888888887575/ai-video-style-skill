# 01 · PV — Promotion Video（番宣 / 音乐 PV / 虚拟偶像 MV）

> **一句话定位**：用画面打节拍。高能量、强节奏剪辑、角色魅力优先的动画向短片。与「AI 漫剧」区别在于 **PV 不讲完整剧情，只卖角色与情绪高潮**；与「手绘 2D」区别在于 PV 允许 2D/三渲二/特效层混用，追求「爽」而非「手作温度」。
>
> **装配顺序**：01 场景主题 → 02 景别构图 → 03 主体特征 →(04 服装)→ 05 光影氛围 → 06 动作运动 →(07 表情)→ 08 风格滤镜 →(09/10/11)→ 12 负向 → 13 模型 → 14 公式。

---

## 00 范例（Examples · 完整可直接投喂的英文 prompt）

> 结构 = 场景主语 + 动作 + 镜头 + 光影 + 风格 + 材质 + 后期 + 负向。中文为行内注释，投喂时删除。

### 例 1 · 番剧主视觉 hero entrance（角色登场型）
```
A silver-haired anime heroine in a long crimson coat stands atop a shattered rooftop,     // 主体+场景
coat and hair violently fluttering against the wind, she snaps her head toward camera,    // 动作
low-angle hero shot, 24mm wide lens, slow dolly-in then a hard snap zoom to face close-up,// 镜头
backlit by a magenta sunset with volumetric god rays, strong rim light on hair edge,      // 光影
anime PV key visual, cel shading, clean thin linework, vibrant teal-and-magenta palette,  // 风格
glossy hair specular, soft skin gradient, fabric with subtle sheen,                       // 材质
additive glow, chromatic aberration, drifting light particles, beat-synced impact frame,  // 后期
--no photorealistic, 3D render, CGI, ray tracing, blurry face, extra fingers, watermark   // 负向
```

### 例 2 · 虚拟偶像 MV 卡点段（舞蹈/节奏型）
```
A virtual idol in a holographic stage costume performs a sharp choreography hit,          // 主体+动作
freeze on the beat then explode into motion, hair whip and skirt flare on the downbeat,   // 节奏语法
orbiting camera 180 degrees around her at chest height, 35mm, slight handheld micro-shake,// 镜头
concert lighting with moving spotlights, cyan and hot pink wash, lens flare streaks,      // 光影
anime music video, virtual idol MV, high-gloss cel shading, saturated stage grading,      // 风格
sequin costume with anisotropic sparkle, translucent hologram panels,                     // 材质
speed lines, radial blur on impact, confetti particles, rhythmic cuts every 2 beats,      // 后期
--no photorealistic, live-action, dull colors, motion sickness wobble, deformed hands     // 负向
```

### 例 3 · 战斗特效作画段（ufotable 味）
```
A young swordsman dashes through a dark corridor and unleashes a horizontal slash,        // 主体+动作
anticipation crouch for 4 frames then explosive burst, afterimage trail behind the blade, // 运动语法
camera tracks laterally at high speed then whip-pans to the impact point,                 // 镜头
blade glow as the only key light, blue-white energy illuminating the walls, deep shadows, // 光影
ufotable-style effects animation, sakuga impact frame, cel shaded anime PV,               // 风格
metallic blade with sharp specular, sparks on stone floor,                                // 材质
energy shockwave ring, debris particles, screen shake on impact, one-frame white flash,   // 后期
--no 3D render, CGI, photorealistic, mushy motion blur, floating limbs, text artifacts    // 负向
```

### 例 4 · 日常系温柔向 PV（抒情段，反差用）
```
A schoolgirl leans on a train window watching the city slide past,                        // 主体+场景
gentle breathing motion, hair strands lifted by the AC vent, she slowly blinks and smiles,// 微动作
medium close-up, 50mm, locked-off tripod with a very slow push-in,                        // 镜头
warm late-afternoon sunlight through glass, soft bloom, dust motes floating,              // 光影
anime PV lyrical interlude, Makoto Shinkai sky aesthetic, delicate cel shading,           // 风格
soft skin gradient, glass reflection with light streaks,                                  // 材质
gentle film grain, slight chromatic fringe, cross-dissolve out,                           // 后期
--no photorealistic, harsh contrast, fast cuts, distorted face, extra limbs               // 负向
```

### 例 5 · 国风玄幻 PV 高潮（命名美学锚定）
```
A robed cultivator ascends on a whirlwind of talismans above a misty jade mountain,       // 主体+场景
ribbons and sleeves spiral upward, slow-motion rise then a sudden speed ramp,             // 动作+速度斜坡
extreme wide establishing shot craning up, then cut to low-angle hero close-up,           // 镜头
golden-hour god rays piercing cloud sea, warm gold key against cool cyan ambient,         // 光影
Chinese fantasy anime PV, King Hu wuxia aesthetic, ink-wash mountain backdrop, cel shaded,// 风格
silk with soft cloth simulation, gold-leaf embroidery specular,                           // 材质
glowing talisman particles, light bloom, radial speed lines, epic beat drop cut,          // 后期
--no photorealistic, western fantasy, plastic 3D look, melting geometry, watermark        // 负向
```

---

## 01 场景主题（Scene / Subgenre）· 必选

### 子类型词库
- `anime series PV` — 番剧宣传片，主打角色阵容与世界观
- `music video / anime MV` — 歌曲驱动，画面服务旋律与歌词
- `virtual idol MV` — 虚拟偶像演出，舞台 + 舞蹈 + 灯光
- `game launch trailer PV` — 游戏上线宣传，技能演出 + UI 感
- `character introduction reel` — 角色卡片式逐个登场
- `season teaser / 15s bumper` — 极短预告，只留钩子
- `concert / live stage PV` — 演唱会现场感，观众与灯阵
- `school / slice-of-life PV` — 日常系，抒情、光斑、季节感
- `battle sakuga PV` — 战斗作画向，特效与冲击帧为核心
- `Chinese fantasy / xianxia PV` — 国风玄幻，飘带、山水、法术
- `cyberpunk city PV` — 霓虹都市，雨夜、全息广告
- `mecha PV` — 机甲，重量感 + 机械展开 + 发射演出
- `idol group formation PV` — 多人队形变换，对称构图
- `product-tie-in anime PV` — 联名商单，角色 + 商品同框

### 题材氛围锚点
- `high-energy hype`（燃向）/ `melancholic lyrical`（抒情）/ `mysterious teaser`（悬念）
- `nostalgic summer`（夏日回忆）/ `neon nightlife`（霓虹夜）/ `epic finale`（终章）

### 速查表：子类型 → 推荐 tag 组合

| 子类型 | 镜头倾向 | 光影倾向 | 运动倾向 | 必配 tag |
|---|---|---|---|---|
| 番剧 PV | hero low-angle + 快切 | rim light + 逆光 | snap zoom / impact frame | `anime PV key visual, cel shading` |
| 音乐 MV | 环绕 + 特写交替 | 舞台色光 | beat-synced cuts | `anime music video, rhythmic cuts every 2 beats` |
| 虚拟偶像 | orbit + 全身中景 | moving spotlight | 舞蹈卡点 | `virtual idol MV, stage lighting, choreography hit` |
| 战斗作画 | whip pan + 跟拍 | 刀光为主光 | anticipation→burst | `sakuga, impact frame, afterimage` |
| 日常抒情 | 定机位缓推 | 自然柔光 | 微动作 | `lyrical interlude, soft bloom, gentle breathing` |
| 国风玄幻 | 大远景升镜 | 金色丁达尔 | 慢速上升 + 速度斜坡 | `xianxia, ink-wash backdrop, ribbon flow` |
| 赛博都市 | 手持 + 反射 | 霓虹双色 | 雨滴 + 灯牌闪 | `cyberpunk neon, rain reflection, holographic ads` |
| 机甲 | 仰角 + 局部特写 | 硬边高光 | 机械展开 + 后坐力 | `mecha transformation, weighty recoil` |

### 联动规则
- 选 `battle sakuga PV` → 06 必须启用 `anticipation / impact frame / afterimage`，05 建议改为「特效自发光为主光」。
- 选 `lyrical interlude` → 06 必须降到微动作级，禁止 `snap zoom / screen shake`，否则抒情感被打碎。
- 选 `virtual idol MV` → 强烈建议用带原生音频的模型（Kling 3.0 / Veo 3.1 / Vidu Q3），否则卡点靠后期。

---

## 02 景别构图（Shot Size / Angle / Lens）· 必选

### 景别词库
- `extreme wide shot (EWS)` — 极远景，交代世界观规模
- `wide establishing shot` — 全景交代，PV 开场常用
- `full body shot` — 全身，展示服装与 pose
- `cowboy shot / medium full` — 七分身，动作与表情兼顾
- `medium shot` — 中景，对话与情绪
- `medium close-up (bust)` — 胸上，PV 主力景别
- `close-up (face)` — 面部特写，卖角色魅力
- `extreme close-up (eye / lips / hand)` — 大特写，节奏重音
- `insert cut` — 插入镜头（手、刀刃、发梢），快切填充
- `two shot / group formation` — 双人或队形，偶像向

### 角度词库
- `low-angle hero shot` — 仰角英雄镜，登场标配
- `high-angle / bird's eye` — 俯角，表现渺小或全局
- `dutch angle` — 荷兰角，制造不安与冲击
- `over-the-shoulder` — 过肩
- `worm's eye extreme low` — 贴地极低角，压迫感
- `top-down flat lay` — 正俯拍，设计感构图
- `profile silhouette` — 侧脸剪影

### 设备 / 焦段词库
- `24mm wide lens` — 广角，夸张透视与空间感
- `35mm` — 通用叙事焦段
- `50mm` — 标准，接近人眼
- `85mm portrait lens` — 长焦人像，压缩背景、糊背景
- `135mm telephoto compression` — 强压缩，人群/都市层次
- `anamorphic 2.39:1` — 变形宽银幕，横向光斑
- `handheld micro-shake` — 手持微抖，真实感
- `gimbal smooth` — 稳定器顺滑
- `crane up / jib` — 摇臂升降
- `drone orbit` — 无人机环绕

### 构图词库
- `rule of thirds` / `center symmetry`（对称，偶像队形）
- `negative space` — 留白，抒情段
- `leading lines` — 引导线（铁轨、走廊）
- `foreground occlusion` — 前景遮挡（树叶、人群）增加层次
- `2.5D parallax layers` — 多层视差，PV 招牌
- `frame within frame` — 框中框（窗、门）
- `silhouette against light` — 逆光剪影

### 速查表：情绪 → 景别 + 角度 + 焦段

| 情绪目标 | 景别 | 角度 | 焦段 | 备注 |
|---|---|---|---|---|
| 登场压迫 | full body | low-angle | 24mm | 广角+仰角 = 最强气场 |
| 角色魅力 | close-up | eye-level | 85mm | 背景虚化，只看脸 |
| 世界观宏大 | EWS | high-angle / crane up | 24mm | 配 drone orbit |
| 战斗冲击 | medium + insert | dutch angle | 35mm | 快切 insert 提节奏 |
| 抒情孤独 | wide + negative space | eye-level | 50mm | 留白 + 慢推 |
| 队形整齐 | two shot / group | center symmetry | 35mm | 对称构图最稳 |

### 联动规则（重要）
- **运动快 → 快门优先**：主体高速运动时写 `high shutter speed, crisp motion, minimal motion blur`，否则模型会糊成一团；反之慢镜写 `180-degree shutter, natural motion blur`。
- **广角 + 特写 = 畸变**：24mm 不要配 `extreme close-up face`，会鱼眼变形；特写统一用 `85mm` 以上。
- **手持 + 快切 = 晕**：`handheld` 与 `rhythmic cuts every 2 beats` 同用时，把抖动降级为 `subtle handheld`。
- **2.5D parallax 只在背景层**：写成 `background in 2.5D parallax, character stays sharp`，否则角色会被一起推平。

---

## 03 主体特征（Subject / Character Design）· 必选

### 角色原型词库
- `anime heroine / protagonist` — 女主角，PV 出现频率最高
- `stoic swordsman` — 冷面剑客
- `energetic idol` — 元气偶像
- `cool antihero` — 反英雄，暗色调
- `mecha pilot` — 机甲驾驶员
- `cultivator in flowing robes` — 修仙者
- `cyber-runner with augments` — 义体跑者
- `ensemble cast lineup` — 群像阵容排列

### 面部 / 头身设计词库
- `large expressive anime eyes with highlight` — 大眼带高光
- `sharp jawline, delicate nose` — 锐利下颌 + 精致鼻
- `heterochromia`（异色瞳）/ `slit pupils`（竖瞳）
- `7-head-tall proportions` — 七头身，标准 anime 比例
- `8-head-tall heroic proportions` — 八头身，英雄化
- `chibi 3-head proportions` — 三头身 Q 版（搞笑插入镜）
- `flowing long hair with distinct strands` — 分股长发（利于飘动）
- `twin tails / hime cut / undercut` — 双马尾 / 姬发 / 剃鬓

### 体型 / 姿态词库
- `slender athletic build` — 修长运动型
- `broad-shouldered heavy build` — 宽肩壮硕
- `dynamic contrapposto pose` — 重心偏移动态站姿
- `crouched ready stance` — 蓄力半蹲
- `mid-air twisting pose` — 空中扭转
- `back-to-camera reveal` — 背对镜头回眸

### 特征强化词库（用于跨镜锁定）
- `character sheet locked` / `consistent face` / `same costume across shots`
- `signature accessory: red ribbon on left wrist`（写死唯一识别物）
- `unique hair color: platinum with pink inner layer`

### 联动规则
- 多镜头 PV **必须**把「唯一识别物 + 发色 + 瞳色」写成固定前缀，否则跨镜脸会漂。
- `chibi 3-head` 只用于单独插入镜，不能与同一镜的 `8-head heroic` 混写。
- `flowing long hair` 是 PV 的动感来源，若角色短发，改用 `scarf / coat tail / ribbon` 补足飘动元素。

---

## 04 服装造型（Costume）· 选读

### 服饰词库
- `school uniform with blazer` — 学院制服
- `long crimson trench coat` — 长风衣（飘动神器）
- `holographic stage costume` — 全息舞台装
- `battle armor with layered plates` — 分层战甲
- `hanfu with flowing ribbons` — 汉服飘带
- `cyberpunk techwear with straps` — 机能风绑带
- `idol frilly dress` — 偶像蓬蓬裙
- `casual hoodie and shorts` — 日常连帽衫

### 材质词库
- `matte cotton` / `glossy latex sheen` / `silk with soft drape`
- `metallic plate with sharp specular` / `translucent chiffon layer`
- `sequin with anisotropic sparkle` / `leather with subtle grain`

### 状态词库
- `wind-blown, coat tails flaring` — 被风掀起
- `torn and battle-worn` — 破损战损
- `rain-soaked, clinging fabric` — 湿身贴合
- `crisp and pristine` — 整洁如新

### 联动规则
- 选 `long coat / ribbons / skirt` → 06 必须配 `cloth simulation, secondary motion`，否则衣服会像纸板。
- `torn and battle-worn` 与 `crisp and pristine` 互斥，不可同镜。
- 湿身 / 雨戏 → 05 必须加 `wet specular highlights`，10 加 `rain streaks`。

---

## 05 光影氛围（Lighting & Mood）· 必选

### 布光技法词库
- `strong rim light on hair edge` — 发丝轮廓光（anime 招牌）
- `backlit silhouette with god rays` — 逆光剪影 + 丁达尔
- `key light from below (uplight)` — 底光，反派/压迫
- `three-point anime lighting` — 三点布光的动画简化版
- `moving concert spotlights` — 移动追光
- `neon practical lights` — 场景内霓虹实光源
- `bounce fill from wet ground` — 湿地反弹补光
- `single hard key, deep shadow` — 单硬光大阴影，戏剧化
- `soft bloom diffusion` — 柔光弥散
- `emissive VFX as key light` — 特效自发光当主光（战斗段核心）
- `dappled light through leaves` — 树影斑驳
- `window sheer curtain light` — 窗台薄纱光

### 色温 × 情绪速查表

| 色温 / 配色 | 英文 tag | 情绪 | 典型段落 |
|---|---|---|---|
| 暖金 3000K | `warm golden hour, amber key` | 怀旧、温柔、终章 | 抒情段 / 国风高潮 |
| 冷蓝 7000K | `cool blue moonlight, cyan ambient` | 孤独、冷峻、夜戏 | 独白 / 潜行 |
| 品红×青 | `magenta and teal duotone` | 潮、燃、都市 | 副歌 / 卡点段 |
| 橙×青对撞 | `orange and teal contrast` | 电影感、冲突 | 战斗前对峙 |
| 紫×粉 | `purple-pink neon wash` | 梦幻、偶像 | 虚拟偶像 MV |
| 高对比黑白 | `high-contrast monochrome` | 冲击、闪回 | impact frame / 回忆 |
| 全白过曝 | `blown-out white flash` | 转场、爆发 | 一帧白闪 |
| 血红 | `crimson red key, harsh shadow` | 危险、觉醒 | 黑化段 |

### 组合公式（可直接套）
```
[主光] + [轮廓光] + [环境色] + [氛围介质]
例：single hard key from left + strong cyan rim light + warm amber ambient bounce + volumetric haze
```
- **燃向副歌**：`emissive VFX key + magenta rim + teal ambient + light particles`
- **抒情间奏**：`soft window light + gentle bloom + warm ambient + floating dust motes`
- **黑化觉醒**：`uplight crimson key + hard shadow + desaturated ambient + smoke haze`

### 联动规则
- `emissive VFX as key light` 必须与 06 的特效动作同帧出现，否则光源无来源，画面会假。
- 逆光剪影 + 面部特写冲突 → 逆光时脸会全黑；要看脸就加 `subtle fill light on face`。
- 舞台移动追光需要模型有较强时序稳定性 → 优先 Kling 3.0 / Veo 3.1，弱模型会闪烁。

---

## 06 动作运动（Motion Grammar）· 必选 · **本风格核心模块**

> PV 与其他风格最大的差异就在这里：**PV 的运动是「被节拍驱动」的**，不是被物理驱动的。所有 timing 都应能对应到「拍」。

### 6.1 静态 / 微动作（用于抒情段与呼吸镜）
- `subtle breathing motion` — 呼吸起伏
- `hair strands drifting in a light breeze` — 发丝轻拂
- `slow blink, then a faint smile` — 缓眨眼后微笑
- `fabric settling gently` — 衣料自然垂落
- `dust motes floating in the light beam` — 光柱里的浮尘
- `ambient loop, almost still` — 近乎静止的氛围循环

### 6.2 动态 / 爆发动作（副歌与战斗）
- `anticipation crouch then explosive burst` — 预备下蹲后爆发（动画十二原则）
- `hair whip on the downbeat` — 重拍甩发
- `coat flare as she turns` — 转身衣摆炸开
- `mid-air spin with trailing ribbons` — 空中旋转 + 飘带拖尾
- `sharp choreography hit, freeze on beat` — 舞蹈定点，卡拍定格
- `sword slash with afterimage trail` — 挥剑残影
- `dash with speed lines converging` — 冲刺 + 速度线汇聚
- `landing impact with ground crack and dust` — 落地冲击起尘
- `mecha transformation with sequential panel unfold` — 机甲逐段展开
- `recoil kickback after firing` — 射击后坐力

### 6.3 摄影机运动（Camera Move）
- `slow dolly-in` — 缓推（建立情绪）
- `snap zoom / crash zoom` — 急推（重音）
- `whip pan` — 甩镜（转场兼冲击）
- `360-degree orbit around subject` — 环绕（副歌高潮）
- `lateral tracking follow at running speed` — 横向跟拍
- `crane up reveal` — 升镜揭示
- `handheld micro-shake` — 手持微抖
- `impact shake / screen shake` — 撞击震屏
- `dolly zoom (vertigo)` — 希区柯克变焦
- `roll / camera rotate 90°` — 镜头翻滚
- `locked-off tripod` — 定机位（反差用）

### 6.4 时间控制（Timing / Easing）· PV 的灵魂
- `beat-synced cuts, one shot per 2 beats` — 每两拍一切
- `speed ramp: slow-mo then sudden real-time burst` — 速度斜坡
- `bullet-time freeze then resume` — 子弹时间
- `ease-out on entry, sharp stop` — 入场缓出急停
- `overshoot then settle` — 过冲回弹（Q 弹感）
- `hold for 6 frames on the impact frame` — 冲击帧定格 6 帧
- `staggered timing across characters` — 群像错峰起动
- `stop-motion stutter on 2s` — 一拍二抽帧（节奏顿挫）
- `smear frames between key poses` — 拉伸中间帧（速度感）

### 6.5 过渡 / 转场（Transition）
- `hard cut on the beat` — 硬切卡拍
- `whip pan transition` — 甩镜转场
- `light flash wipe` — 白光擦除
- `match cut on shape` — 形状匹配剪辑
- `speed line wipe` — 速度线扫场
- `morph between two characters` — 角色形变过渡
- `cross-dissolve for lyrical section` — 抒情叠化
- `iris / shutter wipe` — 圈入圈出（复古）

### 6.6 循环（Loop）
- `seamless loop, first and last frame identical` — 无缝循环（社媒卡点素材）
- `breathing loop for idle shot` — 待机呼吸循环

### 运动速查表：段落 → 运动配方

| 音乐段落 | 摄影机 | 主体动作 | Timing | 转场 |
|---|---|---|---|---|
| Intro 前奏 | slow dolly-in | 微动作 | 慢 ease-in | cross-dissolve |
| Verse 主歌 | 定机位 / 缓跟 | 走位、回眸 | 平稳 | hard cut |
| Pre-chorus 递进 | 逐渐加速推近 | 蓄力 anticipation | 加速 | light flash |
| Chorus 副歌 | 360 orbit + snap zoom | 爆发 pose、甩发 | 每 2 拍一切 | whip pan |
| Bridge 间奏 | 手持 + 特写 | 情绪微表情 | 放慢 | match cut |
| Climax 高潮 | crane up + impact shake | 全力技 + 冲击帧 | speed ramp | white flash |
| Outro 尾声 | 缓拉远 | 静止定格 | hold | fade out |

### 联动规则（硬约束）
- **一条 clip 只放一个主运动**：AI 视频 5–10s 内塞两个爆发动作必崩。多动作请拆镜。
- **camera move 与 subject move 不要同时高速**：二者取一，另一个降为低速，否则空间关系崩坏。
- **speed ramp 需明写起止**：`starts in slow motion for the first half, then bursts into real-time`，只写 `speed ramp` 模型不理解。
- **卡点靠模型还是靠剪辑**：无原生音频的模型（Sora 2 / Seedance 2.0 / PixVerse）请生成「单动作 clip」后在 AE/PR 对轨；有原生音频的（Veo 3.1 / Kling 3.0 / MiniMax H3 / Vidu Q3）可尝试直出。
- **loop 素材必须写死首尾同帧**，并用首尾帧功能（Wan 2.7 / Vidu Q3）而非纯 T2V。

---

## 07 表情表演（Expression & Acting）· 选读

### 表情词库
- `determined glare` — 坚毅怒视
- `confident smirk` — 自信轻笑
- `melancholic downcast gaze` — 忧郁垂眸
- `wide-eyed shock` — 瞪目震惊
- `gentle closed-eye smile` — 闭眼微笑
- `tears welling but not falling` — 泪光将坠
- `battle grin, teeth bared` — 战斗狞笑
- `blank expressionless stare` — 空洞无表情（黑化）

### 眼神 / 眼部词库
- `catchlight sparkle in pupils` — 瞳孔星芒高光
- `pupil contracts on shock` — 惊吓瞳孔收缩
- `eyes shadowed by bangs` — 刘海阴影遮眼
- `slow deliberate blink` — 缓慢眨眼
- `gaze snaps to camera` — 视线突然对镜

### 表演阶段（三段式）
- `beat 1: stillness / breath` — 静
- `beat 2: micro-tell (eyebrow, lip)` — 微征兆
- `beat 3: full expression release` — 释放

### 联动规则
- 表情变化需要 ≥2s 的镜头长度，1s 内的快切镜请用「单一固定表情」。
- `tears welling` 与快速运动冲突 → 泪光只放慢镜。
- 口型对唱：需要唱词同步走 HappyHorse 1.1（7 语口型）或后期对嘴。

---

## 08 风格滤镜（Art Direction & Reference Anchors）· 必选

### 美术方向词库
- `cel shading with clean thin linework` — 赛璐璐 + 细描边
- `high-gloss anime finish` — 高光泽动画完成度
- `2.5D parallax composite` — 2.5D 视差合成
- `sakuga effects animation` — 特效作画
- `toon-shaded 3D (cel-look 3D)` — 三渲二（PV 常见混合）
- `ink-wash backdrop with anime foreground` — 水墨背景 + 动画前景
- `flat limited palette with accent color` — 有限色板 + 强调色
- `hard cel shadow, two-tone shading` — 硬边二值阴影

### 胶片 / 镜头质感词库
- `anamorphic lens flare streaks` — 变形镜头横向光斑
- `chromatic aberration on edges` — 边缘色散
- `subtle film grain` — 轻胶片颗粒
- `bloom and halation on highlights` — 高光溢出光晕
- `vignette` — 暗角
- `scanline / VHS artifact`（复古段落用）

### 参考锚点（导演 / 工作室 / 作品）
- `ufotable Fate-style effects animation` — 特效作画天花板
- `Kyoto Animation delicate acting` — 细腻表演与光
- `Makoto Shinkai sky and light` — 新海诚天空与逆光
- `Trigger / Imaishi kinetic energy` — Trigger 系爆发张力
- `Studio Orange toon-shaded 3D` — 三渲二基准
- `Arcane painted look` — 手绘感 3D（混合向）
- `King Hu wuxia aesthetic` — 胡金铨武侠（国风 PV）
- `Spider-Verse comic hybrid` — 漫画混合（实验向）
- `TOHO animation PV / Aniplex PV` — 日系番宣工业标准
- `virtual idol hologram concert` — 虚拟演唱会视觉

### 速查表：题材 → 锚点组合

| 题材 | 主锚点 | 副锚点 | 慎用 |
|---|---|---|---|
| 燃系战斗 | ufotable effects | Trigger kinetic | Ghibli（太柔） |
| 抒情日常 | Makoto Shinkai sky | Kyoto Animation | ufotable（太炸） |
| 国风玄幻 | King Hu wuxia | ink-wash backdrop | cyberpunk neon |
| 虚拟偶像 | hologram concert | Trigger kinetic | film grain（脏） |
| 三渲二番宣 | Studio Orange | Arcane painted | hand-drawn boiling |

### 联动规则
- **锚点一次只用 1 主 + 1 副**，堆 3 个以上会互相抵消变成「平均脸」。
- 用了 `toon-shaded 3D` 就**不能**同时写 `hand-drawn frame-by-frame`，二者是对立管线。
- `film grain` 与 `high-gloss anime finish` 弱冲突：偶像/舞台段建议关掉颗粒。

---

## 09 材质细节（Material & Surface）· 选读

- `glossy hair specular with sharp highlight band` — 头发高光带
- `soft skin gradient, minimal texture` — 通透肤色渐变（anime 关键）
- `matte fabric with hard cel shadow` — 布料硬边阴影
- `metallic blade with anisotropic streak` — 刀身各向异性高光
- `wet ground with mirror reflection` — 湿地镜面反射
- `translucent hologram with scanline` — 半透全息带扫描线
- `glass window with light streak` — 玻璃光条
- `sequin sparkle, tiny specular dots` — 亮片碎光
- `smooth painted background, no photo texture` — 绘制背景（防止贴图污染）

### 联动规则
- anime 肤质要写 `soft skin gradient, minimal pore detail`，否则模型会加真实毛孔 → 变半写实。
- `wet ground reflection` 需模型反射能力好 → Kling O03 / Veo 3.1 优先。

---

## 10 后期特效（VFX / Grading / Compositing）· 选读

### VFX 词库
- `additive glow layer` — 加色辉光层
- `light particles drifting upward` — 上升光粒子
- `energy shockwave ring` — 能量冲击环
- `speed lines radiating from center` — 中心放射速度线
- `radial blur on impact` — 冲击径向模糊
- `one-frame white flash` — 一帧白闪
- `debris and spark particles` — 碎屑火花
- `lens flare streak across frame` — 横向光斑扫过
- `afterimage / echo trail` — 残影拖尾
- `glitch datamosh burst`（赛博段）

### 调色词库
- `vibrant anime color grading, lifted blacks` — 鲜艳动画调色 + 提黑
- `teal-and-magenta duotone grade` — 青品双色
- `high-contrast crushed blacks` — 高对比压黑
- `warm nostalgic grade with faded highlights` — 暖怀旧褪色

### 合成词库
- `multiply shadow layer` / `screen highlight layer`
- `background bokeh with hexagonal shape`
- `depth-based atmospheric haze`

### 联动规则
- 后期特效 tag 一条 prompt 最多 3 个，超过模型会互相打架糊成雾。
- `glitch datamosh` 与 `subtle film grain` 不要同用（噪声叠加过脏）。
- 粒子必须给方向与速度：`slow upward drifting particles` 优于裸写 `particles`。

---

## 11 道具场景（Props & Set）· 选读

- `shattered rooftop with rebar` — 破碎天台
- `cherry blossom petals in the wind` — 樱花飘落
- `neon signs in a rain-soaked alley` — 雨巷霓虹招牌
- `floating talismans and glowing runes` — 悬浮符箓
- `concert stage with LED wall and truss` — 演唱会舞台
- `train interior with sunset windows` — 夕阳电车车厢
- `school rooftop fence` — 学校天台铁网
- `broken glass suspended mid-air` — 悬停碎玻璃（子弹时间）
- `floating debris rising` — 上升浮空碎块
- `sword planted in stone` — 插地长剑
- `holographic UI panels` — 全息 UI 面板
- `paper lanterns / ink clouds`（国风）

### 联动规则
- 道具是「运动的借口」：选道具时必须能配一个 06 的动作（樱花→飘落、碎玻璃→悬停、符箓→旋转）。
- 道具数量 ≤3 类，否则画面信息过载、模型细节崩。

---

## 12 负向规则（Negative Prompt & Forbidden Combos）· 必选

### 12.1 通用负向词库（PV 基础版，建议全量带上）
```
photorealistic, realistic photo, live-action, 3D render, CGI, ray tracing,
plastic skin, uncanny valley, deformed face, distorted anatomy, extra fingers,
extra limbs, fused hands, mutated hands, asymmetrical eyes, cross-eyed,
blurry, low resolution, jpeg artifacts, oversaturated mush, muddy colors,
flickering, temporal jitter, morphing background, melting geometry,
watermark, signature, text artifacts, subtitles, logo, UI overlay,
static boring shot, no motion, slideshow effect
```

### 12.2 分场景追加负向

| 场景 | 追加负向 | 原因 |
|---|---|---|
| 抒情段 | `fast cuts, screen shake, speed lines, harsh contrast` | 防止节奏被打碎 |
| 战斗段 | `mushy motion blur, floating limbs, weightless motion` | 防止动作失重 |
| 虚拟偶像 | `film grain, dust, dirty texture` | 舞台要干净 |
| 国风玄幻 | `western fantasy, medieval armor, gothic architecture` | 防止文化串味 |
| 纯 2D PV | `toon shading 3D, subsurface scattering, PBR material` | 防止被洗成 3D |
| 循环素材 | `scene change, camera cut, new character` | 保证可循环 |

### 12.3 禁止组合表（Forbidden Combos）

| 禁止组合 | 后果 | 替代写法 |
|---|---|---|
| `cel shading` + `ray tracing / global illumination` | 塑料味三渲二，赛璐璐感全失 | 只保留 `cel shading, hard two-tone shadow` |
| `photorealistic` + `anime PV` | 恐怖谷真人脸 | 用 `stylized anime, not photorealistic` |
| `24mm wide` + `extreme close-up face` | 鱼眼畸变、五官拉伸 | 特写改 `85mm` |
| `handheld shake` + `screen shake` + `snap zoom` 同镜 | 画面完全无法阅读 | 三选一 |
| 两个爆发动作同镜 | 动作互相吞噬、肢体错乱 | 拆成两个 clip |
| `slow motion` + `beat-synced cuts every 2 beats` | 慢镜被切碎，节奏矛盾 | 慢镜单独成镜，切点放在慢镜结束处 |
| `film grain` + `glitch` + `chromatic aberration` 全开 | 画面脏、细节糊 | 最多留 2 个 |
| `hand-drawn boiling line` + `high-gloss anime finish` | 风格打架，线条脏 | 手绘感请走 04-handdrawn.md |
| 多角色 + `orbit camera` + 快切 | 角色脸全漂 | 群像镜用定机位或缓推 |
| `emissive VFX key light` + `natural daylight` | 光源逻辑矛盾，画面发灰 | 战斗段压暗环境光 |

### 12.4 冲突避免清单
- **文字类**：PV 里的 logo/歌词一律后期加，prompt 里写 `no on-screen text`。
- **一致性**：跨镜必须用参考图 / 首尾帧；纯 T2V 多镜头必漂。
- **音画**：无原生音频模型别期待卡点，按「生成单动作 → 剪辑对轨」流程。
- **时长**：PV 单镜 ≤3s 最稳；>5s 的运动镜建议拆。

---

## 13 推荐模型（Model Mapping）· 必选

> 模型能力口径见 `../models.md`。

### 主推

| 模型 | 定位 | 为何契合 PV |
|---|---|---|
| **MiniMax H3** | 动漫感首选 | 输出自带手绘动画质感，风格化专精；原生音频；流体/雨/水强，适合特效段；单 clip 成本最低 |
| **Vidu Q3** | anime 一致性 + 首尾帧 | 非写实一致性最强之一，多输入（文+图+首尾帧）可精确控镜头起止，12–16s 够放一个完整乐句 |
| **Kling 3.0 / O03** | 运动与保真 | 人体运动真实（头发飘、布料垂坠正确），舞蹈/战斗最稳；3.0 有原生音频，可尝试直出卡点 |
| **PixVerse v5.6** | 竖屏社媒批量 | 风格化强、快、便宜，适合一次出 10 个方向抽卡，竖屏 Shorts/Reels 友好 |

### 备选 / 专项

| 场景 | 模型 | 理由 |
|---|---|---|
| 需要角色唱歌口型 | **HappyHorse 1.1** | 7 语口型含演唱，15s 多镜头 |
| 电影级写实基底的真人向 PV | **Veo 3.1** / **Sora 2** | Veo 音画同步业界最佳；Sora 叙事长镜与构图有导演意图 |
| 大批量抽卡探方向 | **Seedance 2.0 (Fast)** | $0.022/s，先探 10 个构图再用主推模型出终稿 |
| 首尾帧锁循环素材 | **Wan 2.7** | 首尾帧 + 思考模式，可做无缝 loop；开源可自部署 |
| 精确控制某区域运动 | **Runway Gen-4** | 运动笔刷 + 运镜控制，导演向精修 |
| 高分辨率 / 竖屏 4K 投放 | **LTX 2.3** | 开源 4K@50fps、20s、原生竖屏 |
| 实验性特效试错 | **Pika** | 特效有趣、上手快 |
| 产品联名 PV 的产品镜 | **Luma** | 物体干净无伪影 |

### 工作流建议
1. **Seedance 2.0 Fast 抽卡** 定构图与配色 →
2. **MiniMax H3 / Vidu Q3** 出动画质感终稿（关键镜用首尾帧锁角色）→
3. 战斗/舞蹈镜换 **Kling 3.0** 提运动质量 →
4. 后期在 AE/PR 对轨卡点、加 logo 与歌词。

---

## 14 组装公式（Assembly Formula）· 必选

### 14.1 槽位顺序
```
[01 场景主题/子类型]
  + [02 景别 + 角度 + 焦段 + 摄影机运动]
  + [03 主体特征（含跨镜锁定前缀）]
  + (选读 04 服装造型)
  + [05 主光 + 轮廓光 + 环境色 + 氛围介质]
  + [06 主体动作 + timing/easing + 转场]
  + (选读 07 表情)
  + [08 美术方向 + 1主1副参考锚点 + 镜头质感]
  + (选读 09 材质 / 10 后期 / 11 道具，随机 3–5 个)
  + [12 负向（通用 + 分场景追加）]
→ 模型选择见 [13]
```

### 14.2 必选 / 选读
- **必选**：01 / 02 / 03 / 05 / 06 / 08 / 12 / 13 / 14
- **选读（每次取 3–5）**：04 / 07 / 09 / 10 / 11
- **PV 特别强制**：06 必须包含「一个主动作 + 一个 timing 描述」；08 必须至少一个参考锚点。

### 14.3 最小可用示例（Minimum Viable Prompt）
```
Anime PV hero shot of a silver-haired heroine on a rooftop,                 // 01+03
low-angle full body, 24mm, slow dolly-in,                                   // 02
strong magenta rim light against a teal dusk sky,                           // 05
her coat flares as she turns to camera, anticipation then sharp stop,       // 06
cel shading, clean linework, ufotable-style effects animation,              // 08
--no photorealistic, 3D render, ray tracing, extra fingers, watermark, text // 12
```
→ 模型：MiniMax H3（首选）/ Vidu Q3（要首尾帧锁脸时）

### 14.4 多镜头 PV 的固定前缀模板
```
[CHARACTER LOCK] Rin, silver hair with pink inner layer, gold heterochromia (left gold / right blue),
red ribbon on left wrist, crimson long coat. Same face and costume in every shot.
[SHOT n] <本镜的 01/02/05/06/08 槽位>
```
- 每一镜复用同一 `[CHARACTER LOCK]` 段，配合参考图 / 首尾帧，跨镜漂移可下降一个数量级。





