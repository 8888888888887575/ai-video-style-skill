# 05 · AI 漫剧 / AI 短剧（AI Anime Drama / Cinematic Donghua Series）

> 定位：叙事驱动的连续 AI 视频，中文创作社区（NeoWoW neo-tv、抖音 AI 漫剧、AIX Studio）最主流品类。
> 与 PV（单曲节奏向）、CG（单条渲染展示）的根本区别：**有角色、有剧情、跨多镜头甚至多集**，头号约束是**跨镜头角色/世界观一致**。
> 结构严格对齐 `_TEMPLATE.md` 15 模块。提示词正文英文，中文仅作注释。

---

## 00 范例（Examples）

### 例 1 · 国风玄幻 · 剑修登场 hero shot
```
A young xianxia sword cultivator stands on a floating jade cliff above a sea of clouds,
white silk robe with crimson inner lining fluttering, signature red hair ribbon streaming,
low-angle hero shot, 35mm, slow dolly-in toward the face, shallow depth of field,
golden-hour rim light through cloud gaps, volumetric god rays, teal-and-gold palette,
cel shaded 3D anime, King Hu wuxia aesthetic, ink-wash distant mountains, drifting spirit particles,
character sheet locked, same face, consistent costume
--no photorealistic, live action, plastic skin, extra fingers, western cartoon, text watermark
```
> `low-angle + slow dolly-in` 是主角登场标准装配；`King Hu wuxia aesthetic` 用导演签名锚定美术，比 "Chinese style" 命中率高一个量级；一致性锚点必须常驻。

### 例 2 · 科幻末日 · 废土定场
```
Extreme wide establishing shot of a ruined megacity under permanent ash sky,
collapsed highways and a half-buried mecha carcass, a lone survivor in patched exosuit crossing frame,
24mm wide, slow crane-down, atmospheric haze layering, drifting ash particles,
cold blue ambient with orange ember accents, high-contrast dystopian grading,
cinematic 3D anime, toon shaded 3D, UE5 cinematic lighting,
world bible locked, scale reference kept consistent
--no clean streets, bright cheerful daylight, pristine surfaces, melting geometry, warped horizon
```
> 末日靠「尺度 + 大气层次」立住，`atmospheric haze layering` 比堆废墟名词有效；`scale reference kept consistent` 防同一城市下一镜变小。

### 例 3 · 都市言情 · 教室对视（正反打 A 镜）
```
Over-the-shoulder shot of a high-school girl turning her head toward a boy across the classroom,
85mm portrait lens, eye level, shallow depth of field, dust bokeh in background,
late afternoon sun through window blinds, warm key from camera left plus cool window fill,
soft pastel slice-of-life palette, subtle film grain,
2D anime, hand-drawn donghua, Makoto Shinkai sky and light bloom,
eyes widen then lashes lower, breath-level subtle motion, same face as character sheet
--no 3D render, CGI, photorealistic, exaggerated anime distortion, extra limbs
```
> 言情靠**微表情 + 光的温度**，不靠大动作；OTS 是正反打 A 镜，B 镜换轴不换光位。

### 例 4 · 音乐 MV · 摇滚舞台高潮
```
A rock vocalist screams into the mic on a neon stage as the chorus hits,
28mm handheld energy, camera orbits 180 degrees around the performer, beat-synced cuts every two beats,
magenta and cyan stage wash, hard backlight haze, strobe accents, additive glow,
stylized 2D anime PV, speed lines on impact frames, chromatic aberration on beats,
hair flutter, sweat highlight, crowd silhouette foreground,
slow motion burst on the final downbeat then speed ramp back
--no static camera, muddy lighting, mismatched instrument fingering, blurry face, text artifacts
```
> MV 的镜头本身就是节拍器；`orbit → snap-zoom → slow-mo burst` 是最稳的高潮三段式。

### 例 5 · 萌系搞笑 · Q 版反差
```
A tiny chubby cat spirit puffs up and throws a comically oversized punch at a shadow ghost,
low-angle comedic close-up cutting to a wide reaction shot,
squash and stretch exaggeration, snap anticipation then explosive overshoot, bouncing tail secondary motion,
bright flat lighting, high-saturation candy palette, thick clean outlines,
chibi 2D anime, limited animation, impact star burst, cartoon dust puff
--no realistic anatomy, photorealistic fur, dark horror grading, gore, complex shading
```
> 萌系靠**动画原理**（预备/过冲/挤压拉伸）而非细节，混入写实词立刻失去喜感。

---

## 01 场景主题（Scene & Theme）

### 子类型词库
- `xianxia cultivation world` — 仙侠修真：洞天福地、飞剑、法宝
- `wuxia jianghu` — 武侠江湖：客栈、竹林、雨夜追杀
- `Chinese mythic fantasy` — 国风玄幻：神魔、上古遗迹、天宫
- `historical epic donghua` — 历史史诗：边塞、行军、封狼居胥
- `post-apocalyptic wasteland` — 末日废土：灰烬天、断桥、幸存者营地
- `cyberpunk neon city` — 赛博都市：霓虹雨街、义体、全息广告
- `urban campus romance` — 都市校园言情：教室、天台、便利店
- `concert music video` / `idol choreography stage` — 演唱会 MV / 偶像编舞
- `chibi comedy short` — 萌系搞笑：夸张日常、宠物拟人
- `interactive branching episode` — 互动剧：选择分支、多结局

### 子类型 → 场景 / 调色 / 世界观 速查表
| 子类型 | 核心场景 tag | 主色调 tag | 世界观锚点 |
|---|---|---|---|
| 国风玄幻/仙侠 | `floating jade cliff, sea of clouds, ancient sect hall` | `teal-and-gold, ink grey, crimson accent` | `xianxia, immortal sect, spirit energy` |
| 历史史诗 | `desert frontier, marching army, war banners` | `dust ochre, steel grey, blood red` | `Han dynasty campaign, historical epic` |
| 科幻末日 | `ruined megacity, ash sky, buried mecha` | `cold blue, ember orange, desaturated` | `post-apocalyptic, survival` |
| 赛博都市 | `neon rain alley, holographic billboards` | `magenta-cyan, wet black asphalt` | `cyberpunk, augmented body` |
| 都市言情 | `classroom, rooftop, convenience store night` | `warm amber, soft pastel, cool window blue` | `slice of life, campus romance` |
| 音乐 MV | `neon stage, crowd silhouette, practice room` | `magenta-cyan wash, strobe white` | `music video, concert, choreography` |
| 萌系搞笑 | `cozy room, cartoon street, spirit world` | `candy saturation, flat bright` | `chibi, comedy, mascot creature` |

### 联动规则
- 选定子类型后，**05 光影 / 08 风格 / 12 负向**三节必须同步换档，否则风格互相污染（仙侠配赛博霓虹光会失去水墨感）。
- 世界观 tag 一旦确定，须作为**固定前缀**出现在同一集的每条 prompt（world bible）。

---

## 02 景别构图（Shot Size & Composition）

### 景别词库
- `extreme wide shot (EWS)` — 大远景：立世界观、展示场景尺度
- `wide / establishing shot` — 远景 / 定场
- `full shot` — 全身：交代动作与服装
- `medium shot` / `medium close-up` — 中景 / 中近景：对话与情绪起步
- `close-up` / `extreme close-up (ECU)` — 特写 / 大特写：眼睛、剑锋、指尖
- `over-the-shoulder (OTS)` — 过肩：正反打骨架
- `two-shot` — 双人同框：关系镜头
- `insert shot` — 插入镜头：道具、信物、屏幕

### 角度 / 设备 / 焦段词库
- `low angle` 仰拍（强势/登场）· `high angle` 俯拍（弱势/孤立）· `eye level` 平视（中性）
- `dutch angle` 斜角（失衡/战斗）· `bird's eye` 顶视（调度/阵型）
- `handheld` / `steadicam` / `dolly` / `crane` / `drone` — 设备语汇
- `24mm wide` 压迫透视 · `35mm` 通用叙事 · `50mm` 自然视角
- `85mm portrait lens` 人像压缩虚化 · `135mm telephoto compression` 长焦压缩（人潮/追逐）

### 景别 × 焦段 × 用途 速查表
| 叙事目的 | 景别 | 焦段 | 角度 | 附加 |
|---|---|---|---|---|
| 世界观开场 | EWS / establishing | 24mm | drone / high angle | `atmospheric layering` |
| 主角登场 | full → medium | 35mm | low angle | `slow dolly-in` |
| 对话正反打 | OTS + medium CU | 50–85mm | eye level | `180-degree rule kept` |
| 情绪爆点 | close-up → ECU | 85mm | eye level | `shallow depth of field` |
| 战斗爆发 | medium → wide | 24–35mm | dutch angle | `motion blur, impact shake` |
| 结尾留钩 | wide 或 ECU | 35mm | eye level | `hold then slow fade` |

### 联动规则
- **景别越近 → 焦段越长 → 景深越浅**：`close-up` 必配 `85mm + shallow DoF`，配广角会脸变形。
- **仰拍+广角 = 英雄化；俯拍+长焦 = 孤立感**，反配会读错情绪。
- 正反打两镜须守 `180-degree rule kept` 并复用同一光位描述，否则剪起来跳轴。

---

## 03 主体特征（Character & Subject）

### 角色设计词库
- `sword cultivator in white silk robe` — 剑修（仙侠主角标配）
- `demonic cultivator, black robe, red eyes` — 魔修反派
- `armored general, lamellar armor, war cape` — 史诗将军
- `survivor in patched exosuit` / `netrunner with chrome implants` — 废土幸存者 / 赛博义体者
- `high-school student in seifuku or gakuran` — 校园制服
- `rock vocalist with dyed streak hair` — MV 主唱
- `chibi mascot creature` — 萌系吉祥物

### 解剖与体型词库
- `slender athletic build` 修长有力 · `broad-shouldered heroic build` 宽肩英雄 · `petite frame` 娇小
- `realistic anime proportion, 7-head-tall` 正常动画比例 · `chibi proportion, 2-head-tall` Q 版二头身
- `defined jawline, sharp brow` 硬朗五官 · `soft rounded features` 柔和五官

### 一致性锚点词库（跨镜必带）
- `character sheet locked` 角色表锁定 · `same face across shots` 跨镜同脸
- `consistent costume and hairstyle` 服装发型一致 · `reference image guided` 参考图引导（I2V）
- 唯一识别特征举例：`signature red hair ribbon` / `scar on left brow` / `heterochromia eyes` / `silver ear cuff`

### 联动规则
- 每角色必须有 **1–2 个唯一识别特征**并写进每条 prompt，比描述脸型更能锁住模型。
- `chibi proportion` 与 `realistic anime proportion` 不可混写，会出现头身比抖动。
- 03 的服装描述必须与 04 完全一致；两处冲突时模型按后写的执行。

---

## 04 服装造型（Costume · 选读）

- `flowing hanfu with wide sleeves` — 汉服广袖（飘带是仙侠核心运动源）
- `layered xianxia robe, crimson inner lining` — 多层仙侠袍，露里衬做色彩点缀
- `lamellar armor with battle scuffs` — 札甲带战损
- `tattered wasteland cloak, dust-stained` — 废土斗篷
- `tech-wear jacket with LED piping` — 赛博机能夹克
- `Japanese school uniform, sailor collar` — 水手服
- `stage costume with metallic studs` — 舞台演出服
- 状态修饰：`wind-blown` 飘动 · `rain-soaked` 湿透 · `battle-torn` 破损 · `crisply pressed` 挺括

### 联动规则
- 有 `wide sleeves / long ribbon / cape` → 06 必须补 `cloth simulation, secondary motion`，否则布料僵死。
- `rain-soaked` → 09 补 `wet fabric specular`、05 补 `hard rim light`，否则湿感不成立。

---

## 05 光影氛围（Lighting & Mood）

### 布光词库
- `golden-hour rim light` — 黄金时刻轮廓光：登场 / 离别
- `volumetric god rays` — 体积光柱：神性 / 圣殿
- `hard key with deep shadow (chiaroscuro)` — 明暗对照：反派 / 审讯
- `soft window light through blinds` — 百叶窗光：校园 / 告白
- `neon wash, magenta-cyan` — 霓虹对撞：赛博 / MV
- `firelight flicker` / `moonlit cool ambient` — 火光跳动 / 冷月夜戏
- `overcast flat light` — 阴天平光：压抑日常
- `strobe accents` / `horror uplight` — 舞台频闪 / 底光诡异

### 色温 × 情绪 速查表
| 色温 tag | 观感 | 情绪 | 典型子类型 |
|---|---|---|---|
| `warm 2700K tungsten` | 暖橘 | 温情、回忆、家 | 都市言情、萌系 |
| `golden hour 3200K` | 金黄 | 史诗、离别、登场 | 仙侠、历史 |
| `neutral 5000K daylight` | 中性 | 客观、日常 | 校园、日常 |
| `cool 6500K overcast` | 冷白 | 疏离、压抑 | 都市、悬疑 |
| `cold blue 8000K moonlight` | 冷蓝 | 孤独、死亡、末日 | 末日、夜战 |
| `magenta-cyan neon mix` | 撞色 | 亢奋、迷幻 | 赛博、MV |

### 联动规则
- 逆光（`backlit / rim light`）必须配 `atmospheric haze` 或 `volumetric`，否则光边生硬无空气感。
- 同场景跨镜头的 key light 方向须写死（如 `key light from camera left`），否则剪辑时人脸忽明忽暗。
- 冷蓝主调 + 暖点缀（`cold blue with ember accents`）是末日 / 夜战最稳的双色方案。

---

## 06 动作运动（Motion & Camera · 视频核心，最详尽）

### 6.1 静态级运动（Micro / Idle）
- `breath-level subtle motion` 呼吸级起伏（静态镜保命项）· `eye blink at natural interval` 自然眨眼
- `hair strands drifting in light breeze` 发丝轻拂 · `fabric ripple, secondary motion` 布料次级运动
- `dust motes floating in light shaft` 光柱浮尘 · `ambient candle flicker` 环境烛光晃动

### 6.2 动态级运动（Action）
- `sword slash with trailing energy arc` — 剑光拖尾
- `wire-fu leap, weightless ascent` — 吊威亚式跃起
- `explosive burst outward, debris scatter` — 爆炸冲击与碎片
- `sprint with camera tracking alongside` — 侧向跟跑
- `impact recoil, body knocked back` — 受击后仰
- `cloak billowing on turn` — 转身斗篷张开
- `choreographed dance combo` — 编舞连段（MV）
- `squash and stretch exaggeration` — 挤压拉伸（萌系）

### 6.3 镜头运动（Camera Move）
- `slow dolly-in` 缓推聚焦 · `dolly-out reveal` 拉出揭示环境
- `orbit / arc around subject` 环绕 · `crane-up / crane-down` 升降
- `tracking / following shot` 跟随 · `whip pan` 甩镜转场
- `handheld shake` 手持晃动（紧张） · `snap zoom` 急推（爆点）
- `push-in with rack focus` 推进 + 移焦

### 6.4 招牌运动（Signature Moves）
- `Hitchcock dolly zoom (vertigo effect)` — 希区柯克变焦：真相揭露、天旋地转
- `slow motion impact then speed ramp back` — 慢动作爆发 + 速度斜坡
- `bullet-time freeze orbit` — 子弹时间环绕
- `hero entrance: low-angle dolly-in with wind gust` — 主角登场组合拳
- `one-shot corridor traversal` — 一镜穿廊

### 6.5 分镜剪辑语法（Editing Grammar · 漫剧专项）
| 语法 | 英文 tag | 用途 | 装配注意 |
|---|---|---|---|
| 正反打 | `shot reverse shot, over-the-shoulder A/B` | 对话 | 两镜同光位，守 180° 轴线 |
| 希区柯克变焦 | `dolly zoom, vertigo effect` | 震惊 / 顿悟 | 单镜内完成，勿叠 snap zoom |
| 慢动作爆发 | `slow motion impact, speed ramp` | 战斗高潮 | 前一镜必须常速，形成对比 |
| 跳切 | `jump cut on the same axis` | 焦躁 / 时间压缩 | 同景别同角度才成立 |
| 匹配剪辑 | `match cut, graphic match` | 场景转换 | 两镜需同形状或同运动 |
| 交叉剪辑 | `cross-cutting between two locations` | 双线并进 | 两地色温需明确区分 |
| 定格留钩 | `freeze frame then slow fade to black` | 集尾 | 配 `hold one second` 更稳 |
| 卡点剪辑 | `beat-synced cuts every two beats` | MV | 需音频驱动或后期对轨 |

### 6.6 运动强度 → 快门 / 模糊 速查表
| 运动强度 | 推荐 tag | 模糊处理 | 常见翻车 |
|---|---|---|---|
| 静止对话 | `breath-level subtle motion` | `natural motion blur` | 完全不动像静帧 |
| 中速走位 | `steady tracking shot` | `slight motion blur` | 脚步滑步（补 `feet planted`） |
| 高速战斗 | `fast slash, impact shake` | `heavy motion blur` | 肢体糊成一团 |
| 慢动作 | `slow motion 120fps look` | `crisp, minimal blur` | 慢动作却强模糊 = 矛盾 |

### 联动规则
- **一条 prompt 只写一个主镜头运动**；`orbit + dolly-in + whip pan` 同写必乱。
- 快运动 → 写 `motion blur` 并把 02 焦段回退到 24–35mm；85mm 拍快动作会糊到不可读。
- 跨镜衔接：上镜尾帧 = 下镜首帧（首尾帧工作流），运动方向须连贯（左出 → 右入）。

---

## 07 表情表演（Expression & Acting · 选读）

### 表情词库
- `stoic resolve, jaw tightened` 隐忍决绝 · `eyes widen then lashes lower` 惊后垂眸
- `tearful eyes, tears welling but not falling` 含泪未落 · `cold smirk, one brow raised` 冷笑挑眉
- `exhausted hollow stare` 空洞疲惫（末日） · `explosive scream, veins on neck` 嘶吼
- `bright open-mouth laugh` 大笑（萌系） · `subtle micro-expression shift` 微表情过渡

### 表演三段式
| 阶段 | 英文 tag | 说明 |
|---|---|---|
| 起 | `neutral resting expression` | 前 20% 时长保持中性 |
| 承 | `expression begins to shift, eyes first` | 眼睛先动，是可信度关键 |
| 转 | `full emotional beat lands` | 情绪落点通常在 60–70% |

### 联动规则
- 情绪镜必须 `close-up + 85mm + shallow DoF`，否则表演被环境稀释。
- `tearful` 需配 `catchlight in the eyes / rim light on tears`，否则泪不发光=看不见。
- 写 `explosive scream` 须同步 06 的 `impact shake`，否则声嘶力竭而画面平静。

---

## 08 风格滤镜（Art Direction & Reference Anchors）

### 美术方向词库
- `cel shaded 3D, toon shaded` — 三渲二（CG 漫剧主路线）
- `2D anime, hand-drawn donghua` — 纯 2D 漫剧
- `painted 3D, Arcane-like brushwork` — 绘画感 3D
- `ink-wash aesthetic, xieyi brush` / `gongbi fine-line color` — 水墨写意 / 工笔重彩
- `high-contrast dystopian grading` — 末日高反差
- `soft pastel slice-of-life` — 日系小清新
- `neon-drenched cyberpunk grade` — 赛博霓虹调色

### 胶片 / 镜头质感词库
- `subtle film grain` 轻颗粒（言情/文艺） · `anamorphic lens flare` 宽银幕横向炫光（史诗/MV）
- `chromatic aberration on edges` 边缘色散 · `2.39:1 cinematic letterbox` 宽银幕比例
- `slight vignette` 暗角 · `bloom on highlights` 高光溢出

### 参考锚点（导演 / 流派签名 · 高命中）
| 锚点 tag | 视觉签名 | 适用子类型 |
|---|---|---|
| `King Hu wuxia aesthetic` | 胡金铨：竹林、留白、腾挪写意 | 武侠、仙侠 |
| `Zhang Yimou red aesthetic` | 张艺谋：大面积红、对称仪式感 | 历史、玄幻 |
| `Makoto Shinkai sky and light bloom` | 新海诚：通透天空、光晕 | 都市言情、青春 |
| `Studio Ghibli warm palette` | 吉卜力：温润自然、手绘云 | 治愈、萌系 |
| `Arcane painted 3D` | 双城之战：厚涂笔触 3D | CG 漫剧、赛博 |
| `ufotable effect animation` | 特效作画：能量层次 | 战斗、仙侠 |
| `Blade Runner neon rain` | 银翼杀手：湿街霓虹 | 赛博、末日 |
| `Mad Max wasteland grade` | 疯狂麦克斯：橙青对撞土黄 | 废土 |

---

## 09 材质细节（Materials & Texture · 选读）

- `silk sheen with soft falloff` 丝绸柔光泽（汉服） · `worn leather with scuff marks` 磨损皮革
- `brushed metal armor, micro-scratches` 拉丝金属甲 · `rusted steel with flaking paint` 锈蚀掉漆
- `wet asphalt with reflected neon` 湿沥青反霓虹 · `paper texture overlay` 纸纹叠加（水墨）
- `soft skin with anime flat shading` 动画平涂肤质 · `glowing energy with inner core falloff` 能量体内核衰减

### 联动规则
- 走 2D 路线时**禁止** `PBR / subsurface scattering / ray tracing`，会把 2D 洗成 3D。
- 走 CG 三渲二时材质要「半写实」：`stylized PBR with toon ramp on top`，纯 PBR 会失去动画感。

---

## 10 后期特效（VFX & Post · 选读）

- `energy blast VFX with radial shockwave` 能量爆发冲击波 · `spirit particles drifting upward` 灵气粒子
- `ash and ember particles` 灰烬余烬 · `rain streaks with lens droplets` 雨丝与镜头水珠
- `speed lines on impact frames` 冲击帧速度线 · `impact frame flash (white/negative)` 冲击白帧
- `holographic UI overlay` 全息 UI · `light leak transition` 漏光转场 · `glitch datamosh transition` 故障转场

### 联动规则
- `impact frame flash` 每镜最多 1 次，滥用会变成频闪噪音。
- 粒子密度随景别变化：EWS 用 `sparse drifting particles`，CU 用 `dense foreground bokeh particles`。

---

## 11 道具场景（Props & Set Dressing · 选读）

- `jade pendant as keepsake` 玉佩信物（跨集回收） · `ancestral sword with inscribed runes` 铭文古剑
- `war banner torn at the edge` 破损战旗 · `rusted road sign half-buried` 半埋路牌（末日）
- `holographic vending machine` 全息贩卖机 · `paper crane on the desk` 桌上纸鹤（言情）
- `guitar pick and setlist taped to floor` 拨片与歌单（MV） · `floating lanterns over water` 水上河灯

### 联动规则
- 信物是**跨集一致性锚点**，出现即写死材质与颜色（`green jade, silver knot cord`）。
- 单镜道具控制在 3 件以内，超过会挤占角色一致性预算。

---

## 12 负向规则（Negative Prompt & Forbidden Combos）

### 通用 negative 词库
- `photorealistic, live action footage` 防写实污染（2D / 三渲二必带）
- `3D render, CGI, ray tracing` 纯 2D 路线必带
- `western cartoon, disney style` 防欧美卡通化
- `extra fingers, malformed hands, extra limbs` 肢体畸变
- `face morphing, inconsistent face` 跨帧脸漂移
- `melting geometry, warped architecture` 几何融化
- `text watermark, subtitle artifacts, garbled text` 文字伪影
- `low resolution, blurry, jpeg artifacts` 画质 · `static frozen frame, no motion` 完全不动

### 子类型专用 negative
| 子类型 | 必须排除 | 原因 |
|---|---|---|
| 国风玄幻（2D） | `photorealistic, plastic skin, ray tracing, western fantasy armor` | 防洗成写实 / 西幻 |
| CG 漫剧（三渲二） | `flat 2D drawing, rough sketch lines` | 防退化为平面 |
| 科幻末日 | `clean streets, bright cheerful daylight, pristine surfaces` | 防"干净废土" |
| 都市言情 | `exaggerated anime distortion, horror grading, gore` | 防情绪跑偏 |
| 音乐 MV | `static camera, muddy lighting, mismatched instrument fingering` | 防死板与穿帮 |
| 萌系搞笑 | `realistic anatomy, photorealistic fur, dark grading` | 防失去喜感 |

### 禁止组合表（Forbidden Combos）
| 冲突组合 | 后果 | 正确做法 |
|---|---|---|
| `ink-wash aesthetic` + `ray tracing / PBR` | 水墨被洗成塑料 3D | 水墨只配 `paper texture, flat wash` |
| `2D anime` + `subsurface scattering` | 平涂脸出现写实肤质 | 2D 用 `flat shading` |
| `chibi proportion` + `realistic anatomy` | 头身比抖动 | 二选一并写死 |
| `slow motion` + `heavy motion blur` | 语义矛盾，输出抖动 | 慢动作配 `crisp minimal blur` |
| `orbit` + `whip pan` + `dolly-in` 同写 | 镜头乱飞 | 一镜一主运动 |
| `close-up` + `24mm wide` | 脸部透视畸变 | 特写配 85mm |
| `handheld shake` + 高稳定要求 | 抖与稳互斥 | 明确取其一 |
| 多角色 + 无唯一识别特征 | 脸互串 | 每人写死 1–2 个特征 |
| `cyberpunk neon` + `xianxia ink` 混写 | 世界观崩塌 | 分镜隔离，勿同镜 |
| 两个导演签名同写 | 风格互相抵消 | 一条 prompt 只锚一个 |

### 冲突避免总则
- **风格排他优先**：越非写实的风格，negative 里排除写实词越重要（漫剧首要翻车点）。
- 同一集内 negative 段保持一致，避免某几镜风格突变。

---

## 13 推荐模型（Model Mapping · 见 models.md）

| 需求 | 主推 | 备选 | 为何契合 |
|---|---|---|---|
| **跨镜角色一致（核心）** | **Wan 2.7** | Vidu Q3 / Seedance 2.0 | 首尾帧 + 思考模式（先规划再生成），多约束提示遵循好；开源可自部署批量出分镜 |
| **2D 漫剧审美** | **Vidu Q3** | MiniMax H3 / PixVerse v5.6 | 非写实 / anime 一致性最强之一，12–16s 长时长 + 首尾帧精确控制镜头起止 |
| **CG 漫剧（三渲二）** | **Kling 3.0 / O03** | Seedance 2.0 / Veo 3.1 | O03 视觉保真 2026 顶级，复杂场景与反射连贯；Seedance 物理与跨帧一致好且便宜 |
| **战斗 / 人体运动** | **Kling 3.0** | Seedance 2.0 | 人体运动真实，头发飘动与布料垂坠正确 |
| **电影感提级 / 终稿** | **Veo 3.1** | Sora 2 | Veo 光影景深调色最接近实拍级；Sora 2 时序连贯且最长 20s，适合长叙事镜 |
| **音乐 MV / 口型演唱** | **HappyHorse 1.1** | Kling 3.0 / MiniMax H3 | 7 国语言口型（含演唱）+ 15s 多镜头；Kling 3.0 / Veo 3.1 有原生音频 |
| **萌系 / 竖屏社媒** | **PixVerse v5.6** | MiniMax H3 | 风格化与夸张比例强，竖屏友好、成本低 |
| **雨 / 水 / 流体场景** | **MiniMax H3** | Kling 3.0 | 流体模拟强，且自带手绘动画感 |
| **精确运镜控制** | **Runway Gen-4** | — | 运动笔刷与运镜指令响应行业最佳，适合导演向分镜 |

### 生产工作流（跨镜一致靠流程，不靠单模型）
1. **建角色表 + 场景表**：每角色 1 张正脸参考 + 固定文字设定（脸 / 发 / 服 / 配色 / 唯一特征）；每场景 1 张参考 + 调性词。
2. **拆 shot list**：镜号 / 景别 / 角度 / 画面描述 / 参考角色 / 台词 / 时长。
3. **逐镜生成**：优先 I2V + 首尾帧（上镜尾帧 = 下镜首帧）；纯 T2V 只用于无角色空镜。
4. **关键镜提级**：登场 / 高潮 / 结尾用 Veo 3.1 / Sora 2 / Kling O03 重出一版。
5. **剪辑拼接 + 配音**：屏内文字与字幕走 Wan 2.7（12 国语言）或后期 AE/PR。

---

## 技术专题 1 — CG 漫剧（3D 三渲二）vs 2D 漫剧

**选错路线 = 风格被洗，这是漫剧第一决策点；开工前必须先问用户「要 3D 感还是纯 2D 感」。**

| 维度 | CG 漫剧（3D 三渲二） | 2D 漫剧 |
|---|---|---|
| 管线 | 3D 渲染 + toon ramp + 轮廓线 | 纯 2D anime / 手绘审美 |
| 正向 tag | `cinematic 3D anime, toon shaded 3D, UE5 cinematic, stylized PBR` | `2D anime, hand-drawn donghua, cel animation, flat shading` |
| 必带 negative | `flat 2D drawing, rough sketch lines` | `3D render, CGI, ray tracing, PBR` |
| 推荐模型 | Veo 3.1 / Sora 2 / Seedance 2.0 / Kling O03 / Wan 2.7（首尾帧锁角色） | MiniMax H3 / Vidu Q3 / PixVerse v5.6 / HappyHorse 1.1 |
| 参考质感 | 《灵笼》《凡人修仙传》《吞噬星空》的 AI 版 | neo-tv 国风玄幻、都市言情 |
| 优势 / 风险 | 空间运镜自由、大场面稳 / 易滑向写实 | 情绪笔触好、成本低 / 大场面与复杂运镜易崩 |

---

## 技术专题 2 — 命名美学锚定（Director-Signature Anchoring）

**用一位导演 / 流派 / 画家的视觉签名锚定整体美术方向，比泛泛写「中国风」命中率高一个量级。**

- 标准写法：`[导演签名] + [2–3 个具体视觉名词] + [调色词]`
  - `King Hu (胡金铨) aesthetic, wuxia martial arts cinema, ink-wash mountains, long robe silhouette, misty swordsmanship, golden-hour wuxia tone`
  - `Zhang Yimou red aesthetic, symmetrical ceremonial composition, massive red drapery, lantern-lit courtyard`
  - `Makoto Shinkai sky, volumetric cloud bloom, lens flare over rooftops, hyper-blue summer sky`
- 可锚定清单：`King Hu wuxia` / `Zhang Yimou red` / `Wong Kar-wai neon melancholy` / `Studio Ghibli warm` / `Makoto Shinkai sky` / `Arcane painted 3D` / `spider-verse hand-drawn` / `ufotable effect animation` / `Blade Runner neon rain` / `Mad Max wasteland`。
- **禁忌**：一条 prompt 只锚一个签名，同写两个会互相抵消导致输出泛化。

---

## 14 组装公式（Assembly Formula）

### 槽位顺序
```
[01 世界观固定前缀]
+ [02 景别 + 角度 + 焦段 + 构图]
+ [03 主体特征 + 唯一识别特征 + 一致性锚点]
+ [05 布光 + 色温 + 情绪]
+ [06 主体动作 + 单一镜头运动 (+ 剪辑语法标注)]
+ [08 美术方向 + 导演签名锚点 + 胶片质感]
+ (选读 3–5: 04 服装 / 07 表情 / 09 材质 / 10 特效 / 11 道具)
+ [12 negative 段]
→ 模型选择见 [13]
```

### 必选 / 选读
- **必选**：01 / 02 / 03 / 05 / 06 / 08 / 12 / 13 / 14
- **选读（每镜取 3–5）**：04 服装 / 07 表情 / 09 材质 / 10 后期 / 11 道具
- **漫剧额外强制**：世界观前缀（01）与一致性锚点（03）必须出现在**每一条** prompt。

### 最小可用示例
```
Xianxia sword cultivator [world: immortal sect, sea of clouds],
medium close-up, 85mm, low angle, slow dolly-in,
white silk robe with crimson lining, signature red hair ribbon, character sheet locked, same face,
golden-hour rim light, volumetric haze, teal-and-gold palette,
cel shaded 3D anime, King Hu wuxia aesthetic, subtle film grain,
breath-level subtle motion, hair strands drifting
--no photorealistic, plastic skin, extra fingers, face morphing, text watermark
```

### 整集装配检查清单
1. 世界观前缀是否每镜一致？2. 唯一识别特征是否每镜出现？3. key light 方向是否跨镜统一？
4. 每镜是否只有一个主镜头运动？5. 正反打是否守 180° 轴线？6. 上镜尾帧是否作为下镜首帧？
7. negative 段是否全集统一？8. 2D / CG 路线是否全集未混？


---
