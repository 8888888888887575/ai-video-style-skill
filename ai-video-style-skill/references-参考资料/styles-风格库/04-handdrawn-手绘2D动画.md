# 04 · 手绘 2D 动画 — Hand-drawn 2D Animation（传统二维 / 赛璐珞 / 绘画质感）

> **一句话定位**：强调「人手绘制」的不规则与温度。核心识别特征是 **boiling line（线条沸腾）+ 有机笔触 + 有限帧率（on 2s / on 3s）+ 材料质感（纸纹、颜料、铅笔）**。
>
> **与相邻风格的边界（关键）**：
> - 与 **PV** 区别：PV 允许三渲二与特效层堆叠，追求「爽」；手绘追求「手作痕迹」，帧率反而更低。
> - 与 **CG** 是**对立管线**：本风格 12 节必须硬排除 `3D render / CGI / ray tracing / subsurface scattering`，这是最高频翻车点。
> - 与 **MG** 区别：MG 是矢量精确，手绘是刻意不精确。
>
> **四条子路线**（先选路线，再配模块）：赛璐珞 anime / 铅笔粗动画 / 水彩·水粉绘本 / 油画·厚涂动画。
>
> **装配顺序**：01 → 02 → 03 →(04)→ 05 → 06 →(07)→ 08 →(09/10/11)→ 12 → 13 → 14。

---

## 00 范例（Examples · 完整英文 prompt）

> 结构 = 场景主语 + 动作 + 镜头 + 光影 + 风格 + 材质 + 后期 + 负向。中文为注释，投喂前删除。

### 例 1 · 吉卜力风水彩田野（治愈系）
```
A young girl in a straw hat runs through a windswept summer meadow,                      // 主体+动作
grass bending in waves around her, her dress and hair trailing with a slight delay,       // 次级运动
wide side-scrolling tracking shot following her at a constant pace, eye-level,            // 镜头
warm afternoon sunlight, soft ambient bounce from the grass, gentle bloom on highlights,  // 光影
hand-drawn 2D animation, Studio Ghibli watercolor aesthetic, hand-painted background,     // 风格
watercolor paper grain, soft pigment bleed at edges, visible brush texture in the sky,    // 材质
animated on 2s, subtle line boiling, warm faded film scan look,                           // 后期
--no 3D render, CGI, ray tracing, cel-look 3D, photorealistic, digital gloss, vector clean// 负向
```

### 例 2 · 铅笔粗动画 pencil test（作画质感）
```
A boxer throws a heavy right hook in a rough pencil test animation,                       // 主体+动作
strong anticipation wind-up, smear frames through the swing, overshoot then settle,       // 运动语法
medium shot, static framing with a small impact shake, slight low angle,                  // 镜头
no rendered lighting, only hatching and cross-hatch shadow strokes,                       // 光影
rough pencil animation, graphite sketch aesthetic, unfinished animator's test,           // 风格
graphite texture on off-white paper, visible eraser smudges, construction lines left in,  // 材质
animated on 3s, heavy line boiling, occasional stray guide lines,                         // 后期
--no color fill, 3D render, CGI, clean digital lineart, photorealistic, smooth gradient   // 负向
```

### 例 3 · 赛璐珞 90s anime（复古平涂）
```
A schoolgirl turns her head toward camera as a train passes behind her,                   // 主体+动作
hair swings with a delayed follow-through, uniform ribbon fluttering,                     // 次级运动
medium close-up, locked-off camera on a hand-painted background, slight pan,              // 镜头
hard two-tone cel shadow, warm key from the left, no gradient shading,                    // 光影
1990s cel animation, retro anime, hand-inked outline with slight thickness variation,     // 风格
flat gouache color fills, painted background with visible brushwork, cel plastic sheen,   // 材质
animated on 2s, subtle registration jitter, film scan grain and dust specks,              // 后期
--no 3D render, CGI, ray tracing, subsurface scattering, digital gradient, modern gloss   // 负向
```

### 例 4 · 油画 / 厚涂动画（Loving Vincent 味）
```
A fisherman rows a small boat across a churning night sea, painted in thick oil strokes,  // 主体+动作
every brushstroke shifting and swirling between frames, the water alive with impasto,     // 招牌运动
wide shot, slowly drifting camera, painterly perspective,                                 // 镜头
moonlight rendered as pale yellow impasto ridges against deep blue, no realistic falloff, // 光影
oil painting animation, Loving Vincent style, post-impressionist brushwork,               // 风格
thick impasto texture with visible palette-knife ridges, canvas weave showing through,    // 材质
animated on 2s, constant paint shimmer between frames,                                    // 后期
--no 3D render, CGI, photorealistic, smooth digital shading, vector art, clean lines      // 负向
```

### 例 5 · 现代 rough sakuga 特效作画（燃向）
```
A cloaked figure slams a fist into the ground unleashing a shockwave,                     // 主体+动作
crouch anticipation, then explosive impact with hand-drawn debris and smoke shapes,       // 运动语法
low-angle wide, camera snaps back on impact, one-frame hold on the impact drawing,        // 镜头
high contrast, blown-out white flash at the moment of impact, dark rim-lit silhouette,    // 光影
rough sakuga animation, hand-drawn effects animation, expressive irregular linework,      // 风格
limited palette of three flat colors, hand-drawn smoke and debris shapes,                 // 材质
animated on 2s with 1s on the impact, smear frames, heavy line boiling,                   // 后期
--no 3D render, CGI, particle simulation, ray tracing, photorealistic, clean vector       // 负向
```

---

## 01 场景主题（Scene / Subgenre）· 必选

### 子路线词库（先选一条）
- `cel animation (traditional anime)` — 赛璐珞传统动画
- `rough pencil test animation` — 铅笔粗动画/作画测试
- `watercolor storybook animation` — 水彩绘本动画
- `gouache flat painted animation` — 水粉平涂动画
- `oil painting / impasto animation` — 油画厚涂动画
- `ink and brush (sumi-e) animation` — 水墨毛笔动画
- `crayon / colored pencil animation` — 蜡笔/彩铅动画
- `marker sketch animation` — 马克笔速涂动画
- `charcoal smudge animation` — 炭笔涂抹动画
- `limited animation (retro TV anime)` — 有限动画（复古电视动画）
- `rough sakuga effects animation` — 特效作画
- `rotoscope hand-traced animation` — 转描动画
- `paper cut-out animation` — 剪纸动画（混合向）
- `chalk on blackboard animation` — 黑板粉笔动画

### 题材 / 情绪锚点
- `nostalgic pastoral summer` — 怀旧田园夏日
- `melancholic rainy city` — 忧郁雨城
- `whimsical children's fable` — 童话寓言
- `gritty expressive action` — 粗粝动作
- `quiet domestic slice-of-life` — 安静日常
- `surreal dream sequence` — 超现实梦境
- `folk tale / mythological` — 民俗神话

### 速查表：子路线 → 推荐 tag 组合

| 子路线 | 线条 | 上色 | 帧率 | 必配 tag |
|---|---|---|---|---|
| 赛璐珞 anime | 墨线粗细变化 | 平涂二值 | on 2s | `cel animation, hand-inked outline, flat color` |
| 铅笔粗动画 | 石墨草线 | 无/单色 | on 3s | `rough pencil test, graphite texture, construction lines` |
| 水彩绘本 | 淡线或无线 | 透明叠色 | on 2s | `watercolor, pigment bleed, paper grain` |
| 水粉平涂 | 硬边 | 不透明平涂 | on 2s | `gouache, opaque flat paint, matte finish` |
| 油画厚涂 | 无线，笔触即形 | 厚涂 | on 2s | `impasto, palette knife ridges, canvas weave` |
| 水墨 | 飞白毛笔 | 墨色浓淡 | on 3s | `sumi-e, ink wash, dry brush flying white` |
| 蜡笔/彩铅 | 蜡质粗线 | 排线填色 | on 3s | `crayon texture, waxy stroke, paper tooth` |
| 特效作画 | 极不规则 | 三色有限 | on 2s / 1s | `rough sakuga, smear frames, limited palette` |
| 炭笔 | 涂抹柔边 | 灰阶 | on 3s | `charcoal smudge, grayscale, fingerprint smear` |

### 联动规则
- **子路线决定 09 材质与 12 负向**：选 `watercolor` 就必须配 `paper grain`，并排除 `digital gloss`；选 `oil impasto` 必须排除 `flat vector`。
- 选 `rough pencil test` → 05 光影不写「布光」，改写 `hatching shadow strokes`（铅笔动画没有渲染光）。
- 选 `limited animation` → 06 必须写 `only the foreground moves, background held still`（省帧法本身就是风格）。

---

## 02 景别构图（Shot Size / Angle / "Camera"）· 必选

> 手绘动画没有真实摄影机——所谓运镜其实是**背景平移、多层视差、画面缩放**。写 prompt 时要用「动画摄影台」的语言，而不是电影摄影机的语言。

### 景别词库
- `extreme wide painted establishing shot` — 手绘全景建立镜
- `wide shot with a hand-painted background` — 全景带绘制背景
- `full body shot showing the pose silhouette` — 全身看剪影
- `medium shot` / `medium close-up (bust)`
- `close-up on the face` / `extreme close-up on the eye` — 情绪特写
- `insert cut of hands / an object` — 局部插入
- `two shot for dialogue` — 双人对话镜
- `pillow shot / empty landscape` — 空镜（日式「枕镜」，抒情标配）

### 角度词库
- `eye-level neutral` — 平视（手绘默认，稳）
- `low-angle looking up` — 仰视
- `high-angle looking down` — 俯视
- `flat side-on profile view` — 纯侧面平视（绘本感）
- `over-the-shoulder` — 过肩
- `bird's-eye layout view` — 俯视布局（构图化）

### 「摄影台」运动词库（关键：不用摄影机术语）
- `horizontal background pan (side-scroll)` — 背景横移（跟跑标配）
- `multiplane parallax: foreground fast, background slow` — 多层平面视差
- `slow zoom in on the artwork (camera push on cel)` — 对画面缓推
- `truck out revealing the wider painting` — 拉出揭示
- `held frame, no camera movement` — 定格无运动
- `whip pan smear between two setups` — 甩场（带拖影）
- `follow pan tracking the running character` — 跟随横摇
- `tilt up along a tall painted background` — 沿竖长背景上摇
- `shake / vibration on impact` — 冲击震动

### 构图词库
- `strong silhouette read, pose readable in black` — 剪影可读（手绘动画第一构图法则）
- `flat layered composition, foreground / midground / background` — 分层平面构图
- `generous sky negative space` — 大片天空留白
- `off-center subject with leading room` — 偏心留视线空间
- `frame within frame using painted architecture`
- `low horizon line for open sky` — 低地平线

### 速查表：目的 → 构图配方

| 目的 | 景别 | 角度 | 摄影台运动 | 备注 |
|---|---|---|---|---|
| 角色奔跑 | 全身/中景 | 平视侧面 | 背景横移 + 多层视差 | 手绘最经典的运动镜 |
| 情绪爆发 | 面部特写 | 微仰 | 定格 + 微推 | 让表演说话 |
| 世界观 | 手绘全景 | 高角 | 缓拉出 | 展示背景绘画本身 |
| 抒情间隙 | 空镜 | 平视 | 定格或极缓推 | 日式枕镜 |
| 打击感 | 中景 | 低角 | 冲击震动 + 一帧定格 | 配 06 的 impact hold |
| 竖长场景 | 全景 | 平视 | 沿背景上摇 | 瀑布/高塔 |

### 联动规则（重要）
- **禁止写摄影焦段与光圈**：`85mm / f/1.8 / bokeh / shallow depth of field` 会把画面拉向实拍或 3D 渲染，直接破坏手绘属性。要虚化就写 `painted soft background, out-of-focus watercolor wash`。
- **多层视差要指定层速差**：`foreground moves fast, midground medium, background nearly static`，否则模型会整体平移，失去多平面感。
- **剪影优先**：任何动作镜先写 `strong readable silhouette`，这是手绘动画区别于 AI 糊团的关键。
- **定机位是朋友**：手绘风格下机位越静，模型越不容易把线条洗掉。

---

## 03 主体特征（Character Design）· 必选

### 造型风格词库
- `simplified shapes, appealing cartoon construction` — 简化形状、讨喜构成
- `Ghibli-style rounded soft features` — 吉卜力圆润造型
- `90s anime sharp chin and large eyes` — 90 年代尖下巴大眼
- `modern anime clean design` — 现代动画简洁设计
- `rubber-hose noodle limbs`（复古 30s 橡胶管风格）
- `angular expressive design (Tartakovsky style)` — 棱角表现主义
- `chunky storybook proportions` — 绘本敦实比例
- `minimal line character, few details` — 极简线角色
- `rough construction visible under the lines` — 结构线外露

### 头身 / 解剖词库
- `5-head-tall stylized proportions` — 五头身
- `7-head-tall anime proportions` — 七头身
- `3-head-tall chibi` — 三头身
- `exaggerated hands and feet for expression` — 夸张手脚
- `simplified anatomy, no muscle detail` — 简化解剖
- `consistent volume across frames` — 跨帧体积一致（防形变）
- `line of action drives the pose` — 动势线主导姿态

### 线条特征词库（手绘的身份证）
- `hand-inked outline with thick-to-thin variation` — 粗细变化墨线
- `uneven line weight, visibly human` — 不匀线宽
- `open线 gaps where lines don't close` — 断线留缝
- `construction and guide lines left visible` — 保留辅助线
- `single-weight marker outline` — 等粗马克笔线
- `no outline, shape defined by paint` — 无线，靠色块造型
- `sketchy multi-pass contour` — 多遍草线轮廓

### 特征锁定词库（跨镜一致）
- `character sheet locked, same design in every shot`
- `signature silhouette: round hat, oversized scarf`
- `consistent palette: ochre coat, teal scarf, black hair`

### 联动规则
- **线条一致性 > 细节丰富度**：手绘 AI 视频最常见的失败是「每帧线条风格漂移」，所以角色设计要**简化**：细节越少，跨帧越稳。
- `no outline` 路线（水彩/油画）不要再写 `hand-inked outline`，二者冲突。
- 三头身与七头身不可同镜混写。

---

## 04 服装造型（Costume）· 选读

### 服饰词库
- `simple cotton dress with few folds` — 少褶简裙（好画好动）
- `oversized coat with heavy hem` — 大衣重下摆
- `school uniform with a fluttering ribbon` — 制服飘带
- `flowing scarf trailing behind` — 长围巾拖曳
- `layered kimono with wide sleeves` — 和服宽袖
- `worn overalls with patches` — 补丁工装
- `cloak that reads as a silhouette shape` — 剪影化斗篷

### 材质（绘画语言，非 PBR）
- `flat matte fabric, no rendered sheen` — 平涂无光泽
- `watercolor-washed fabric with bleeding edges` — 水彩渗色布
- `gouache opaque color blocks` — 水粉不透明色块
- `hatched shading on the folds` — 排线阴影褶皱
- `paint texture visible in the fill` — 填色见笔触

### 状态词库
- `wind-blown, hem lifting` — 风掀下摆
- `rain-soaked, darker paint wash` — 雨湿加深色块
- `dusty and worn with sketchy grime lines` — 草线脏痕
- `crisp and simple` — 干净简单

### 联动规则
- **褶皱越少越好**：复杂褶皱在逐帧 AI 生成里必然抖动混乱 → 写 `simple folds, few wrinkles`。
- 飘动元素（围巾/下摆/发）是手绘动感来源 → 至少保留一个，并在 06 配 `follow-through delayed by a few frames`。
- 禁止写 `latex sheen / PBR / specular highlight` 等渲染词。

---

## 05 光影氛围（Light & Color · 绘画语言）· 必选

> 手绘动画的「光」不是计算出来的，是**画上去的**。要用「阴影形状 / 排线 / 色块」描述，而不是「主光 / 补光 / GI」。

### 「布光」技法词库（手绘化）
- `hard two-tone cel shadow, shadow as a flat shape` — 二值硬阴影（赛璐珞核心）
- `three-tone shading: base, shadow, highlight` — 三阶上色
- `hatching and cross-hatching for shadow` — 排线/交叉排线（铅笔）
- `watercolor wash shadow, soft bleeding edge` — 水彩晕染阴影
- `painted rim light as a bright stroke` — 一笔画出的轮廓光
- `blown-out white sky, no gradient` — 纯白天空
- `hand-painted god rays as translucent shapes` — 手绘光柱（半透明色块）
- `dappled leaf shadow painted as scattered dots` — 树影斑点
- `silhouette against a bright painted sky` — 亮天剪影
- `no rendered lighting at all, flat illustration` — 完全无渲染光
- `single-color night wash over everything` — 夜色统一罩色
- `impasto highlight ridges catching light`（油画）

### 色彩 × 情绪速查表

| 色调 | 英文 tag | 情绪 | 典型子路线 |
|---|---|---|---|
| 明亮饱和田园 | `bright saturated summer palette, vivid greens` | 治愈、怀旧 | 水彩/吉卜力 |
| 褪色暖黄 | `faded warm ochre, aged paper tone` | 回忆、旧片 | 赛璐珞复古 |
| 冷灰蓝雨天 | `muted cool gray-blue wash` | 忧郁、静 | 水彩/炭笔 |
| 三色有限板 | `limited palette of three flat colors` | 冲击、设计感 | 特效作画 |
| 单色石墨 | `monochrome graphite grayscale` | 草稿、原始 | 铅笔粗动画 |
| 墨黑与留白 | `black ink and raw paper white` | 东方、写意 | 水墨 |
| 高饱和撞色 | `bold complementary color clash` | 活泼、实验 | 蜡笔/马克笔 |
| 深蓝夜 + 暖点光 | `deep blue night with warm lamp accents` | 孤独、温暖 | 油画/水彩 |

### 组合公式
```
[整体罩色/色调] + [阴影处理方式] + [高光处理方式] + [背景绘制方式]
例：warm afternoon ochre tone + hard two-tone cel shadow + a single painted rim stroke
    + hand-painted watercolor background
```
- **吉卜力治愈**：`bright summer palette + soft watercolor shadow + gentle bloom + hand-painted background`
- **90s 赛璐珞**：`faded ochre tone + hard two-tone shadow + no gradient + painted background with brushwork`
- **特效作画**：`three-color limited palette + no shading + white flash + black void background`
- **铅笔测试**：`monochrome graphite + hatching shadow + no highlight + blank off-white paper`

### 联动规则
- **绝不写 `global illumination / ray tracing / volumetric lighting / subsurface scattering`** —— 这四个词是手绘风格的头号杀手，会立刻把画面渲染成 3D。
- 需要体积光就写 `hand-painted light shafts as translucent flat shapes`。
- `hard two-tone cel shadow` 与 `soft gradient shading` 互斥；赛璐珞选前者，水彩选后者。
- 背景必须显式声明 `hand-painted background`，否则模型倾向生成照片背景。

---

## 06 动作运动（Motion Grammar）· 必选 · **本风格核心模块**

> 手绘动画的运动由**动画十二原则 + 有限帧率 + 线条沸腾**共同定义。这里的每一个 tag 都直接决定「像不像手绘」，比任何美术 tag 都关键。

### 6.1 帧率与节拍（Frame Rate · 手绘最强识别特征）
- `animated on 2s (12 drawings per second)` — 一拍二（日式动画标准）
- `animated on 3s (8 drawings per second)` — 一拍三（更省、更顿挫）
- `on 1s for the fast action beats only` — 关键动作转一拍一
- `mixed timing: on 3s for holds, on 1s for impacts` — 混合帧率（专业做法）
- `choppy limited-animation cadence` — 有限动画的顿挫感
- `stepped playback, not smooth interpolation` — 阶梯播放非平滑插值

### 6.2 手绘专属运动特征
- `subtle line boiling, outlines shimmer between frames` — 轻微线条沸腾
- `heavy line boiling for a raw sketch feel` — 重线条沸腾
- `registration jitter, slight frame-to-frame misalignment` — 定位抖动
- `smear frames between key poses` — 拉伸残像中间帧
- `multiple-image blur (drawn afterimages)` — 手绘多重残影
- `impact hold: freeze on one drawing for 4 frames` — 冲击帧定格
- `pose-to-pose keyframing, distinct held poses` — 原画到原画（清晰停顿）
- `straight-ahead loose animation for effects` — 一气呵成（特效用）
- `drawn effects: smoke, fire and debris as hand-drawn shapes` — 手绘特效形状

### 6.3 动画十二原则词库
- `squash and stretch on impact and landing` — 挤压拉伸
- `anticipation: wind up in the opposite direction first` — 预备动作
- `follow-through and overlapping action, hair lags 3 frames` — 跟随与重叠
- `arcs: limbs move along curved paths` — 弧线运动
- `slow in and slow out on the extremes` — 缓入缓出
- `exaggeration beyond realistic range` — 夸张
- `secondary action: scarf swings while she walks` — 次要动作
- `weight and timing consistent with mass` — 重量与节奏

### 6.4 典型动作词库
- `run cycle with a strong contact and passing pose` — 跑步循环
- `walk cycle with a bounce` — 走路循环
- `hair swings with a delayed follow-through` — 甩发延迟
- `cloth ripples in a wave from the shoulder down` — 布料波状传导
- `character turns and holds a strong pose` — 转身定 pose
- `explosive action out of a deep crouch` — 深蹲爆发
- `gentle breathing on a held drawing` — 定格图上的呼吸
- `blink: 3-frame close, 2-frame open` — 眨眼帧数
- `wind gust bends grass and hair in waves` — 风场波浪

### 6.5 「摄影台」运动与过渡
- `background pan, character animated in place` — 背景移动角色原地跑
- `multiplane parallax with layered speeds` — 多层速差
- `whip pan with a drawn smear transition` — 手绘拖影甩场
- `cross-dissolve between painted setups` — 绘制画面叠化
- `white flash on the impact frame` — 白闪
- `iris in / iris out` — 圈入圈出（复古）
- `hold on the final drawing, fade to black` — 末帧定格淡出
- `match cut between two similar shapes` — 形状匹配剪辑

### 6.6 有限动画技巧（Limited Animation · 省帧即风格）
- `only the foreground character animates, background held still` — 只动前景
- `only the mouth and eyes move on a held body` — 只动嘴眼
- `cycling a 6-drawing loop` — 六张循环
- `sliding a static drawing across the frame` — 静图平移
- `held drawing with only the camera pushing in` — 定格 + 推镜

### 运动速查表：目的 → 运动配方

| 目的 | 帧率 | 手绘特征 | 十二原则 | 摄影台 |
|---|---|---|---|---|
| 治愈奔跑 | on 2s | subtle boiling | arcs + follow-through | 背景横移 + 多层视差 |
| 打击爆发 | on 1s（冲击）| smear + impact hold | anticipation + exaggeration | 震动 + 白闪 |
| 情绪特写 | on 3s | 轻 boiling | slow in/out | 定格 + 微推 |
| 粗草稿感 | on 3s | heavy boiling + jitter | 保留结构线 | 定机位 |
| 复古电视动画 | on 3s | registration jitter | 只动嘴眼 | 静图平移 |
| 风景空镜 | on 2s | 云与草的循环 | 波浪传导 | 极缓推 |
| 特效作画 | on 1s/2s | 手绘烟火形状 | straight-ahead | 冲击震动 |

### 联动规则（硬约束）
- **必须显式写帧率**：`animated on 2s` 是把 AI 从「平滑插值」拉回「手绘顿挫」最有效的单条 tag。不写则模型默认输出丝滑 24/30fps，手绘感立刻消失。
- **line boiling 要控量**：`subtle line boiling` 是风格，`heavy line boiling` 容易显脏且加剧一致性崩坏。默认用 subtle，只有铅笔草稿路线用 heavy。
- **smear / impact hold 是成对使用的**：快速动作 → smear frames；命中瞬间 → impact hold + white flash。
- **一镜一主动作**：手绘 AI 一致性弱于 3D，5s 内两个大动作必崩，请拆镜。
- **背景与角色分工**：优先 `background held still / slow pan` + `character animates`，这既是有限动画的正统做法，也大幅降低 AI 崩坏率。
- **禁止物理模拟词**：`particle simulation / cloth simulation / rigid body physics` 会触发 3D 管线 → 改写 `hand-drawn smoke shapes / drawn cloth ripples`。
- **循环素材**：走 `cycling a 6-drawing loop` + 首尾帧模型，纯 T2V 很难闭环。

---

## 07 表情表演（Expression & Acting）· 选读

### 表情词库
- `exaggerated open-mouth shout` — 夸张张嘴喊
- `quiet downcast melancholy` — 安静垂眸忧郁
- `wide-eyed wonder with sparkling pupils` — 惊奇星瞳
- `flat deadpan stare (comedic)` — 面瘫吐槽脸
- `soft closed-eye smile` — 闭眼柔笑
- `trembling lip before crying` — 哭前唇颤
- `angry with simplified brow and gritted teeth` — 简化怒眉咬牙
- `chibi super-deformed reaction`（插入用）

### 眼神 / 眼部
- `single white catchlight dot in the pupil` — 单点高光
- `eyes hidden by shadow under the bangs` — 刘海阴影遮眼
- `pupils shrink to dots on shock` — 惊吓瞳孔缩点
- `tears drawn as simple teardrop shapes` — 简化泪滴形
- `slow 3-frame blink` — 三帧慢眨

### 表演阶段（手绘三段式）
- `hold on a neutral drawing` — 静态原画停顿
- `2-frame transition drawing` — 两帧过渡张
- `hold on the expressive extreme` — 极限表情定格

### 联动规则
- 手绘表演靠**「停顿 + 突变」**，不靠平滑过渡：写 `hold, then snap to the new expression`。
- 口型同步在手绘风格下极难 → 需要唱/说走 HappyHorse 1.1，或用 `only the mouth moves on a held body` 的有限动画法。
- `chibi super-deformed` 只做单独插入镜。

---

## 08 风格滤镜（Art Direction & Reference Anchors）· 必选

### 美术方向词库
- `hand-drawn 2D animation, frame-by-frame` — 逐帧手绘（核心声明）
- `traditional cel animation` — 传统赛璐珞
- `hand-painted background art` — 手绘背景美术
- `rough animation / genga pencil stage` — 原画铅笔阶段
- `limited animation TV cadence` — 电视有限动画
- `storybook illustration in motion` — 动起来的绘本
- `sumi-e ink wash aesthetic` — 水墨写意
- `post-impressionist brushwork` — 后印象派笔触
- `mid-century UPA flat graphic` — 中世纪 UPA 平面
- `underground zine sketch look` — 地下杂志草稿感

### 材料 / 扫描质感词库
- `film scan grain with dust and hairs` — 胶片扫描颗粒带灰尘毛发
- `slight registration jitter from the animation camera` — 摄影台定位抖
- `aged paper yellowing at the edges` — 纸边泛黄
- `visible cel plastic sheen and layer separation` — 赛璐珞片反光与层分离
- `photocopied line texture` — 复印线质感
- `VHS softness for retro TV feel` — VHS 柔化
- `clean modern digital 2D, no grain`（现代路线，反向）

### 参考锚点（工作室 / 作者 / 作品）
- `Studio Ghibli watercolor warmth` — 吉卜力水彩温度
- `Makoto Shinkai painted skies`（背景锚点）
- `Kyoto Animation delicate acting` — 京阿尼细腻表演
- `1990s retro anime cel look` — 90 年代赛璐珞
- `Genndy Tartakovsky angular action` — 棱角化动作
- `Cartoon Saloon (Wolfwalkers) linework` — 爱尔兰线条美学
- `Loving Vincent oil painting animation` — 油画动画
- `Ghost in the Shell 1995 painted grit`（写实向手绘）
- `Spider-Verse hand-drawn hybrid`（混合向，慎用）
- `Bill Plympton rough pencil` — 粗铅笔作者动画
- `Yuasa Masaaki loose expressive` — 汤浅政明放飞线条
- `sumi-e Chinese ink animation (Shanghai Animation)` — 上美影水墨

### 速查表：目标 → 锚点组合

| 目标 | 主锚点 | 副锚点 | 材料质感 | 慎用 |
|---|---|---|---|---|
| 治愈田园 | Studio Ghibli watercolor | Makoto Shinkai skies | 纸纹 + 轻颗粒 | Tartakovsky（太硬） |
| 复古电视 | 1990s retro anime | UPA flat graphic | 胶片颗粒 + 定位抖 | 现代 clean digital |
| 粗粝动作 | Tartakovsky angular | Yuasa loose | 复印线质感 | Ghibli（太柔） |
| 绘本童话 | Cartoon Saloon | storybook illustration | 纸纤维 | film grain（太脏） |
| 油画艺术 | Loving Vincent | post-impressionist | 画布纹 | 清晰线条 |
| 东方写意 | Shanghai ink animation | sumi-e | 宣纸渗墨 | 硬边赛璐珞 |
| 现代番剧 | Kyoto Animation | modern clean 2D | 无颗粒 | VHS / 复印质感 |

### 联动规则
- 锚点 1 主 + 1 副为上限；`Ghibli` + `Tartakovsky` 会互相抵消成平庸中间态。
- **`Spider-Verse` 是陷阱**：它本质是 3D 混合，写了容易把画面拉向 CG → 除非确实要混合风，否则不写。
- 选 `clean modern digital 2D` 时，必须把 09/12 里的颗粒、纸纹、定位抖全部去掉，保持一致。

---

## 09 材质细节（Material & Texture）· 选读

### 纸 / 载体质感
- `watercolor paper grain with visible tooth` — 水彩纸粗纹
- `smooth bristol board surface` — 光滑绘图板
- `off-white animation paper with punch holes` — 带定位孔动画纸
- `canvas weave showing through the paint` — 画布纹
- `rice paper with ink bleeding` — 宣纸渗墨
- `newsprint / recycled paper tone` — 报纸底色

### 颜料 / 笔触质感
- `soft pigment bleed at the edges of washes` — 水彩边缘渗色
- `granulating watercolor sediment` — 水彩颗粒沉淀
- `opaque gouache with matte chalky finish` — 水粉哑光粉质
- `thick impasto ridges from a palette knife` — 厚涂刀痕
- `visible individual brush hairs in the stroke` — 见笔毛
- `dry brush scratchy texture` — 干笔飞白
- `graphite sheen on heavy pencil areas` — 石墨反光
- `waxy crayon buildup with paper tooth showing` — 蜡笔堆积

### 瑕疵 / 人味词库（**手绘真实感的核心**）
- `eraser smudges and ghost lines` — 橡皮擦痕与残影
- `construction lines left visible` — 保留结构线
- `slightly uneven color fill, paint going over the line` — 涂色出界
- `small paper wrinkles and fold marks` — 纸的褶皱
- `dust specks and stray hairs from the scan` — 扫描灰尘
- `pencil under-drawing showing through the paint` — 铅笔底稿透出
- `inconsistent line weight across the drawing` — 线宽不匀

### 联动规则
- **瑕疵是手绘的身份证**：至少带 2 个瑕疵 tag，否则输出会是「干净的数码 anime」而非手绘。
- 瑕疵 tag 与 `clean modern digital 2D` 路线互斥。
- 纸/画布纹理必须与 01 的子路线匹配（水彩配水彩纸、油画配画布、水墨配宣纸）。

---

## 10 后期特效（Post & Compositing）· 选读

- `hand-drawn smoke and dust shapes` — 手绘烟尘形状（**不要写 particle**）
- `drawn speed lines radiating outward` — 手绘速度线
- `white flash on the impact frame` — 冲击白闪
- `light bloom painted as a soft halo` — 手绘柔光晕
- `film scan grain overlay` — 胶片扫描颗粒
- `dust and scratch overlay (old print)` — 老片划痕
- `warm faded color grade, lifted blacks` — 暖褪色提黑
- `slight gate weave / frame wobble` — 片门抖动
- `vignette from the animation camera` — 摄影台暗角
- `paper texture multiplied over the whole frame` — 纸纹叠加全画面
- `clean composite, no overlays`（现代路线）

### 联动规则
- 后期 tag ≤3 个；颗粒 + 划痕 + 暗角全开会盖住线条。
- **所有特效都要用「手绘」限定词**：`hand-drawn smoke` 而非 `smoke VFX`，`drawn speed lines` 而非 `radial blur`。数字后期词会把画面拉回 CG/PV。
- `radial blur / chromatic aberration / lens flare` 在手绘风格下都属污染词（PV 可用，手绘慎用）。

---

## 11 道具场景（Props & Set）· 选读

- `hand-painted summer meadow with wind waves` — 手绘夏日草原
- `wooden countryside house with weathered planks` — 乡村木屋
- `train interior with painted seat fabric` — 手绘电车车厢
- `rainy street with painted puddle reflections` — 雨街水洼
- `cluttered artist's room with drawn details` — 杂物房间
- `open sky with hand-painted cumulus clouds` — 手绘积云天
- `cherry blossoms drawn as simple petal shapes` — 简化花瓣
- `laundry hanging and swaying` — 晾晒衣物摆动
- `paper lanterns with painted glow` — 纸灯笼
- `tall grass in the foreground as a silhouette layer` — 前景草剪影层
- `ink-wash mountains fading into paper white` — 水墨远山
- `simple prop shapes, few details` — 简化道具

### 联动规则
- **前景剪影层是廉价好用的层次法**：加 `foreground silhouette layer` 可立刻提升多平面感。
- 道具越少越好；手绘背景细节多 = 逐帧抖动源。
- 所有道具都要带绘制限定：`hand-painted / drawn`，否则模型可能给照片素材。

---

## 12 负向规则（Negative Prompt & Forbidden Combos）· 必选 · **本风格生死线**

> 手绘是所有风格里**最容易被模型「洗掉」**的一种：扩散模型的先验强烈偏向干净、平滑、3D 化。因此本节的负向词不是可选项，而是必须全量携带。

### 12.1 核心排除词（**必须全部带上，一个都不能少**）
```
3D render, CGI, computer generated, ray tracing, path tracing,
global illumination, ambient occlusion, subsurface scattering,
PBR materials, physically based rendering, toon shading 3D, cel-look 3D,
Unreal Engine, Blender render, octane render, realistic reflections,
photorealistic, photograph, live-action, real footage,
smooth digital gradient, airbrushed shading, plastic surface, glossy digital sheen,
vector art, perfectly clean lines, uniform line weight, anti-aliased perfection
```
> 记忆口诀：**「三维四光两材质，写实平滑加矢量」**。

### 12.2 通用画质负向
```
blurry, low resolution, jpeg artifacts, oversharpened,
deformed anatomy, extra limbs, extra fingers, fused hands, melting face,
inconsistent character design, face changing between frames, model drift,
excessive line boiling, chaotic flickering lines, unstable outlines,
smooth 60fps interpolation, motion smoothing, soap opera effect,
watermark, signature, text artifacts, subtitles, timecode
```

### 12.3 分子路线追加负向

| 子路线 | 追加负向 | 原因 |
|---|---|---|
| 水彩绘本 | `hard cel shadow, digital gloss, saturated neon` | 水彩要柔要淡 |
| 赛璐珞 anime | `soft gradient shading, painterly brushwork, watercolor bleed` | 赛璐珞要硬边平涂 |
| 铅笔粗动画 | `color fill, clean inking, finished artwork` | 要保持未完成感 |
| 油画厚涂 | `clean lines, flat fill, vector shapes` | 油画无线条 |
| 水墨 | `saturated color, hard outline, western painting` | 水墨靠墨色浓淡 |
| 有限动画复古 | `smooth animation, high frame rate, modern gloss` | 顿挫即风格 |
| 特效作画 | `particle simulation, volumetric smoke, 3D debris` | 特效必须手绘 |
| 现代 clean 2D | `film grain, paper texture, dust, registration jitter` | 现代路线要干净 |

### 12.4 禁止组合表（Forbidden Combos）

| 禁止组合 | 后果 | 替代写法 |
|---|---|---|
| `hand-drawn` + `3D render / CGI / ray tracing` | **直接翻车**：输出变成干净三渲二，手绘感全无 | 全量带 12.1 排除词 |
| `hand-drawn` + `subsurface scattering / PBR` | 皮肤变写实塑料 | 皮肤写 `flat painted skin tone` |
| `watercolor` + `hard two-tone cel shadow` | 两种上色逻辑打架，出现脏边 | 水彩用 `soft wash shadow` |
| `oil impasto` + `clean hand-inked outline` | 油画不该有线，出现描边油画的怪物 | 油画写 `no outline, shape from paint` |
| `animated on 3s` + `smooth 60fps` | 帧率语义矛盾，输出变平滑 | 只写一种帧率，并在负向排除 smoothing |
| `heavy line boiling` + 面部大特写 | 五官抖成鬼脸 | 特写用 `subtle line boiling` |
| `heavy line boiling` + 跨镜角色一致 | 一致性彻底崩 | 多镜叙事一律用 subtle |
| `85mm / shallow depth of field / bokeh` | 引入摄影虚化 → 拉向实拍 | 用 `painted soft background wash` |
| `particle simulation / cloth simulation` | 触发 3D 物理管线 | `hand-drawn smoke shapes / drawn cloth ripples` |
| `radial blur / chromatic aberration / lens flare` | 数字后期味，PV 化 | `drawn speed lines / painted halo` |
| 两个大动作同镜 | 逐帧一致性崩坏、肢体错乱 | 拆镜 |
| `film grain + dust + scratches + vignette` 全开 | 线条被噪声吃掉 | 最多留 2 个 |
| `clean modern digital 2D` + `paper grain / eraser smudges` | 路线自相矛盾 | 先定「有材质」还是「无材质」 |

### 12.5 冲突避免清单（工程层面）
- **一致性策略（最重要）**：手绘风格跨镜漂移最严重 →
  1. 必用参考图 / 首尾帧（Vidu Q3、Wan 2.7）；
  2. 角色设计尽量简化（细节少 = 稳）；
  3. 低变异 seed，同一 seed 出同一角色；
  4. 固定角色前缀（见 14.4）。
- **帧率策略**：显式写 `animated on 2s` + 负向写 `smooth 60fps interpolation, motion smoothing`，双向夹逼。
- **背景策略**：`hand-painted background` 必写；有限动画法（背景静止）能大幅降低崩坏。
- **时长策略**：手绘单镜 ≤3s 最稳；长镜必然出现线条漂移。
- **后期补救**：可在 AE 里叠纸纹 + 抽帧（posterize time）人工制造 on 2s，比让模型硬做更可控。

---

## 13 推荐模型（Model Mapping）· 必选

> 模型能力口径见 `../models-模型能力矩阵.md`。手绘的选型逻辑是：**风格化能力 > 写实保真度**，一致性机制优先。

### 主推

| 模型 | 定位 | 为何契合手绘 |
|---|---|---|
| **MiniMax H3** | **手绘感第一选择** | 动漫/风格化专精，输出本身自带「手绘动画感」；对水、雨、风等有机运动表现好（适合草浪、水彩流动）；原生音频；单 clip 成本最低之一 |
| **Vidu Q3** | 一致性 + 首尾帧 | **非写实/anime 一致性最强之一**，这正是手绘最缺的能力；多输入（文+图+首尾帧）可锁角色与镜头起止；12–16s 可容纳完整动作 |
| **PixVerse v5.6** | 风格化批量 / 竖屏 | 风格化非写实强（动漫、插画、夸张比例），快且便宜，适合一次抽 10 个方向找线条手感；竖屏社媒友好 |
| **Kling 3.0** | 运动质量 | 人体运动真实（头发飘、布料垂坠正确），适合需要扎实运动基底的手绘动作镜；原生音频 |

### 备选 / 专项

| 需求 | 模型 | 理由 |
|---|---|---|
| 角色说话 / 唱歌口型 | **HappyHorse** | 动漫卡通审美强，多语口型（含演唱），15s 多镜头 |
| 首尾帧锁循环 / 屏内文字 | **Wan 2.7** | 首尾帧 + 思考模式，可做 6 张循环；开源自部署便于批量；风格化艺术表现好 |
| 手绘 + 写实混搭基底 | **Wan 2.7** / **Seedance 2.0** | 需要半写实底子再手绘化时使用 |
| 精修某区域运动 | **Runway Gen-4** | 运动笔刷可只让围巾/头发动，配合有限动画法 |
| 长叙事分镜 | **Seedance 2.0 (Fast)** | $0.022/s 批量抽卡拆镜，再用主推模型出终稿 |
| 高分辨率输出 | **LTX** | 开源 4K，适合放大后叠纸纹后期 |
| 实验性笔触探索 | **Pika** / **Hunyuan** | 快速试错非常规质感 |

### ⚠️ 不推荐（反向指引）

| 模型 | 为何不适合 |
|---|---|
| **Veo 3.1** | 强项是电影级写实与实拍质感，会主动把手绘「修正」成干净高完成度画面 |
| **Sora 2** | 时序物理强但审美偏写实电影，手绘笔触易被平滑 |
| **Kling O03** | 极致保真面向真实材质，与「刻意不精确」的手绘目标相反 |
| **Luma** | 输出过于干净无伪影，手绘要的正是伪影 |
| **Animora MotionVid** | MG 专精，矢量精确，与手绘不规则冲突 |

### 选型速查表

| 子路线 | 首选 | 次选 |
|---|---|---|
| 吉卜力水彩 | MiniMax H3 | Vidu Q3 |
| 90s 赛璐珞 | Vidu Q3 | PixVerse v5.6 |
| 铅笔粗动画 | PixVerse v5.6 | MiniMax H3 |
| 油画厚涂 | MiniMax H3 | Wan 2.7 |
| 水墨写意 | MiniMax H3 | Wan 2.7 |
| 特效作画 | Kling 3.0 | MiniMax H3 |
| 跨镜叙事 | Vidu Q3（首尾帧） | Wan 2.7（首尾帧） |
| 角色口播 | HappyHorse | Vidu Q3 |

### 工作流建议
1. **PixVerse v5.6 / Seedance Fast** 低成本抽卡，锁定线条与配色手感；
2. 用选中帧作为参考图，交 **Vidu Q3 / Wan 2.7** 走 I2V + 首尾帧，保证跨镜一致；
3. 动作复杂镜交 **MiniMax H3**（有机运动）或 **Kling 3.0**（人体运动）；
4. 后期在 AE 里：抽帧成 on 2s + 叠纸纹 + 加胶片颗粒 + 手绘特效层 —— **这一步比在 prompt 里硬求更可控**。

---

## 14 组装公式（Assembly Formula）· 必选

### 14.1 槽位顺序
```
[01 子路线 + 题材情绪]
  + [02 景别 + 角度 + 摄影台运动 + 剪影可读性]
  + [03 造型风格 + 头身比 + 线条特征]
  + (选读 04 服装：少褶 + 一个飘动元素)
  + [05 整体色调 + 阴影处理方式 + 背景绘制声明]
  + [06 帧率(on 2s/3s) + 线条沸腾程度 + 十二原则 + 主动作]
  + (选读 07 表情：停顿+突变)
  + [08 美术方向 + 1主1副锚点 + 材料/扫描质感]
  + (选读 09 纸/颜料/瑕疵 ×2 / 10 后期 ≤3 / 11 道具，取 3–5 个)
  + [12 负向（12.1 核心排除词全量 + 12.2 + 子路线追加）]
→ 模型选择见 [13]
```

### 14.2 必选 / 选读
- **必选**：01 / 02 / 03 / 05 / 06 / 08 / 12 / 13 / 14
- **选读（每次取 3–5）**：04 / 07 / 09 / 10 / 11
- **手绘特别强制（缺一即翻车）**：
  1. 06 必须显式写帧率 `animated on 2s`（或 3s）；
  2. 06 必须写 `subtle line boiling`；
  3. 05 必须写 `hand-painted background`；
  4. 08 必须写 `hand-drawn 2D animation, frame-by-frame`；
  5. 09 至少 2 个瑕疵 tag；
  6. 12 必须全量携带 12.1 核心排除词。

### 14.3 最小可用示例（Minimum Viable Prompt）
```
Hand-drawn 2D animation of a girl running through a summer meadow,               // 01+03
wide side tracking shot, background pan with multiplane parallax, eye-level,     // 02
warm afternoon palette, soft watercolor shadow, hand-painted background,         // 05
animated on 2s, subtle line boiling, hair follow-through delayed 3 frames,       // 06
frame-by-frame cel animation, Studio Ghibli watercolor aesthetic,                // 08
watercolor paper grain, slightly uneven color fill going over the line,          // 09
--no 3D render, CGI, ray tracing, global illumination, subsurface scattering,
   PBR, photorealistic, smooth digital gradient, vector art, uniform line weight,
   smooth 60fps interpolation, watermark                                         // 12
```
→ 模型：MiniMax H3（首选）/ Vidu Q3（需锁角色时走 I2V + 首尾帧）

### 14.4 多镜头手绘叙事的固定前缀模板
```
[STYLE LOCK] Hand-drawn 2D frame-by-frame animation, animated on 2s, subtle line boiling,
hand-painted watercolor backgrounds, Studio Ghibli aesthetic, watercolor paper grain.
NOT 3D, NOT CGI, no ray tracing, no smooth digital gradient.

[CHARACTER LOCK] Hana: 6-head-tall, round soft features, short black bob, ochre coat,
teal scarf, single white catchlight in each eye. Same simplified design in every shot.

[SHOT n] <本镜的 02 景别 / 05 色调 / 06 动作与帧率 / 选读槽位>
```
- 每镜复用同一 `[STYLE LOCK]` + `[CHARACTER LOCK]`，配合参考图与首尾帧，是手绘跨镜一致的唯一可靠解法。





