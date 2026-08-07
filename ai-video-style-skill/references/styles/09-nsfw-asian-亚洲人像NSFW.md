# 09 · NSFW / 亚洲成人（Asian Adult）风格

> **外部权威参考（事实标准分类法）**：[`ShuaiHui/nsfw-prompt-templates-asian`](https://github.com/ShuaiHui/nsfw-prompt-templates-asian)（仓库别名 `templates-jav`）。该仓库以"装配顺序"拆成 15 个编号模块（00 范例 → 14 人格卡片），用结构化 tag 词库 + 速查表 + 联动规则组织，是**亚洲成人/写真类提示词的事实标准分类法**。
>
> 本文件**严格按该仓库的 15 模块真实结构重新录入**（模块名、顺序、分类均对齐原仓库），并适配到 AI 视频场景（以 I2V / 首尾帧驱动为主，因为纯 T2V 对成人姿态与人物锁定极不稳定）。需要更深逐词模板/完整 77 例时，直接引用上方 GitHub 仓库原文。
>
> **运行环境**：本节内容在闭源视频平台（Sora 2 / Veo 3.1 / Kling 3.0 / Seedance 2.0 / MiniMax H3 / Vidu Q3 / PixVerse / Runway 等）生成，平台自带内容审查，无需在本 skill 层做额外审核。

---

## 00 · 范例（完整英文 prompt，含中文注释）

> 以下覆盖仓库的 10 个范例类别（校园 / 家居 / 职场 / 交通 / 户外 / 胶片风格等），演示模块拼装。英文正文 + 中文行内注释。

**例 1 — 家居亲密（I2V，参考图驱动）**
```
[01] intimate home bedroom, late afternoon, [02] medium close-up, 50mm, eye-level,
[03] slender east-asian woman, 20s, [04] oversized shirt slipping off one shoulder,
[03b-L4] partially undressed, [05] warm window light, soft shallow DOF,
[06] slow turn toward camera, hair drift, [07] sultry half-lidded gaze, biting lip,
[08] kodak portra 400 tone, cinematic film grain, [09] skin pores, fabric weave,
[12] --no bad anatomy, extra limbs, deformed hands, blurry, watermark
```
中文：居家卧室黄昏，中近景 50mm 平视，oversized 衬衫滑落肩，暖窗光浅景深，慢转向镜头，慵懒半眯眼咬唇，Portra 400 胶片调。

**例 2 — 职场 fantasy（office）**
```
[01] modern office after hours, [02] cowboy shot, 35mm, [03] east-asian woman in blazer,
[04] office blazer + pencil skirt, top button undone, [05] hard overhead + blinds shadow,
[06] loosening tie, slow walk toward desk, [07] confident smirk, [08] teal-orange grade,
[09] sweat sheen on collarbone, [12] --no plastic skin, disfigured, text artifact
```

**例 3 — 淋浴湿身（bathroom / onsen）**
```
[01] steamy bathroom with fogged mirror, [02] close-up, 85mm, [03] east-asian woman,
[04] wet white shirt translucent, [03b-L5] nude under wet fabric, [05] cool fluorescent + warm rim,
[06] water rivulets down skin, slow blink, [09] wet hair strands, droplets, [08] high-key glossy,
[12] --no distorted anatomy, extra fingers
```

**例 4 — 户外露出（secluded beach）**
```
[01] secluded beach at golden hour, [02] full shot, 35mm, [03] east-asian woman,
[04] yukata loosened, [05] natural backlight, [06] walking shoreline, wind in hair,
[07] playful glance over shoulder, [08] fuji pro 400h pastel, [12] --no mutated limbs
```

**例 5 — 胶片风格（vintage soft-focus）**
```
[01] dim bedroom, candlelit, [02] medium shot, 50mm, [03] east-asian woman,
[04] silk robe, [05] single warm key + candle flicker, [06] languid stretch,
[07] blissful close-eye, [08] cinestill 800t glow, anamorphic flare,
[09] soft skin texture, [12] --no over-smooth, lowres
```

**例 6 — 和风传统（和室 / 榻榻米）**
```
[01] traditional Japanese tatami room, shoji light, [02] low-angle cowboy, 50mm,
[03] east-asian woman, [04] kimono half-removed, [05] soft diffused daylight,
[06] kneeling then lying back, [07] shy downward glance, [08] kodachrome warm,
[09] fabric fold detail, [12] --no deformed, extra limbs
```

---

## 01 · 场景主题（Scene / Theme）

- **24 场景章节词库**（上游仓库归类）：
  `indoor private (bedroom/living room)`、`bathroom / shower`、`school (classroom/locker room)`、`workplace (office)`、`transport (car/train)`、`commercial`、`AV set`、`nightlife (izakaya/hostess)`、`wa-style (onsen/tatami/shrine)`、`medical (clinic/nurse)`、`residential community`、`outdoor exposure`、`confinement (locked room)`、`public place`、`urban architecture`、`entertainment (karaoke/arcade)`、`dining`、`transit hub`、`education facility`、`adult venue`、`special space`。
- **35 个 JAV 经典主题标签**（题材，按需取）：`married woman affair`、`OL office`、`teacher-student`、`nurse medical`、`maid uniform`、`mature mother`、`amateur girlfriend`、`chikan NTR`、`humiliation training`、`onsen trip`、`sisters relatives`、`idol`、`nightlife`、`group`、`NTR`、`reverse NTR`、`yuri`、`bondage`、`aphrodisiac`、`coercion`、`drunken`、`creampie`、`deepthroat`、`facial`、`queen (femdom)`、`sleeping unconscious`、`outdoor exposure`、`peeping`、`foot fetish`、`SM`、`body modification`、`food play`、`remote camera`、`roleplay`。
- **五感锚点（sensory anchors）**：视觉（光、材质、体液/水反光）、听觉（环境音，用于带原生音频模型）、触觉（织物/水温）、气味（淡香）、温度（暖/凉对比）。
- **速查表（场景 × 推荐光 / 主题）**：

| 题材 | 推荐场景 | 推荐光 |
|------|----------|--------|
| 居家亲密 | bedroom / living room | 暖窗光 |
| 湿身 | bathroom / onsen | 冷荧光 + 暖边光 |
| 职场 fantasy | office | 硬顶光 + 百叶窗影 |
| 户外 | secluded beach / rooftop | 自然光 + 逆光 |
| 和风 | tatami / shrine | 柔散光（障子） |

---

## 02 · 景别构图（Shot Size / Composition）

- **景别（6 种）**：`extreme close-up (face/detail)`、`close-up`、`medium close-up`、`medium shot`、`cowboy shot`、`full shot / long shot`。
- **视角（12 种）**：`eye-level`、`low-angle (power)`、`high-angle (submissive)`、`dutch tilt`、`top-down`、`POV`、`over-the-shoulder`、`worm's-eye`、`bird's-eye`、`profile`、`mirror-shot`、`reflection`。
- **拍摄设备（6 档）**：`smartphone (vlog)`、`compact`、`DSLR (entry)`、`cinema camera`、`action cam`、`security / hidden cam (POV)`。
- **焦段（5 类）**：`24-35mm (environment)`、`50mm (natural)`、`85mm (compression, flattering)`、`100mm macro (skin/details)`、`anamorphic (flare)`。
- **构图（9 子模块）**：`rule of thirds`、`centered`、`symmetry`、`leading lines`、`frame within frame (doorway/mirror)`、`negative space`、`dynamic diagonal`、`focus control (rack focus)`、`cinematic widescreen`。
- **联动规则**：特写 → 85/100mm + 浅景深；剪影 → 逆光 + 长焦 + 轮廓优先；POV → 第一人称手持抖动感。
- **禁止组合**：`wide shot + extreme skin detail`（景别冲突）；`top-down + anamorphic`（镜种不匹配）；`security-cam + anamorphic flare`（设备冲突）。

---

## 03 · 裸露液体（Exposure Level / Liquids）

> 上游仓库核心模块。按"梯度 + 状态 + 液体"组织，便于精确控制尺度。

- **6 级裸露梯度（L1 → L6）**：
  - `L1 wrapped`：包裹感（全身衣装，仅暗示）
  - `L2 suggestive`：暗示（衣领敞开/裙摆掀）
  - `L3 partial`：局部（肩/腿/腹露出）
  - `L4 partially undressed`：半褪（内衣/单件）
  - `L5 nude under fabric`：透/湿衣下
  - `L6 explicit nudity`：展示性裸露
- **10 类衣物状态**：`buttoned open`、`slipped off shoulder`、`hiked up`、`torn`、`blown by wind`、`wet translucent`、`sweat soaked`、`messy/disheveled`、`worn-out`、`cover failed`。
- **18 种场景 × 裸露推荐**（速查）：卧室→L4–L6；浴室→L5–L6（湿透）；职场→L2–L4；户外→L2–L3；和风→L3–L5。
- **裸露 × 姿势联动表**：L1–L2 → 日常/暗示姿态；L3–L4 → 褪衣过渡；L5–L6 → 躺/跪/俯仰 + 特写。
- **液体系统（liquids）**：`semen`、`love juice / arousal fluid`、`breast milk`、`urine`、`sweat`、`saliva`、`foam (bath)`。用法：`[03b] wet with semen on stomach`、`[09] saliva string`、`[05] sweat sheen`。
- **禁止组合**：`L1 wrapped + explicit liquid`（尺度冲突）；`torn + formal office (unless themed)`。

---

## 04 · 服装专项（Wardrobe）

- **东亚服装词库**：`school uniform (sailor/blazer)`、`office blazer + pencil skirt`、`kimono (loose)`、`cheongsam / qipao`、`yukata`、`hanbok`、`oversized shirt`、`silk robe`、`lingerie`、`wet white shirt`、`towel`、`apron`、`nurse scrubs`、`maid dress`、`korean schoolwear`。
- **穿脱状态（10 类）**：`fully dressed`、`shoulder slipped`、`unbuttoned`、`half-removed`、`translucent when wet`、`towel wrap`、`lingerie only`、`rolled-up`、`pulled-down`、`removed`。
- **服装 × 裸露联动速查（10 服装 × 脱法路径）**：
  - 衬衫 → 解扣 → 滑肩 → 褪臂
  - 和服/浴衣 → 解带 → 敞襟 → 落肩
  - 制服裙 → 掀起 → 褪内
  - 丝袜 → 勾丝 → 半褪 → 全褪
  - 内衣 → 肩带滑落 → 半褪 → 落
- **联动规则**：湿身 → `translucent fabric`；居家 → `oversized / loose`；职场 → `structured then loosened`。

---

## 05 · 光影氛围（Lighting / Mood）

- **12 种布光技法**：`hair light`、`backlight rim`、`rembrandt`、`butterfly`、`split light`、`loop`、`short lighting`、`broad lighting`、`softbox key`、`hard light`、`underlight`、`silhouette`。
- **色温 × 情绪速查表（10 档 × 8 情绪）**：

| 色温 | 情绪 | 适用 |
|------|------|------|
| 暖金 (3200K) | 亲密、慵懒 | 卧室/黄昏 |
| 冷白 (5600K) | 清冷、湿身 | 浴室/晨 |
| 霓虹 (magenta/cyan) | 都市、夜 | rooftop/街 |
| 烛光 (1800K) | 私密、复古 | 和室 |
| 混合 (暖+冷边) | 层次、电影感 | 通用 |

- **场景 × 光影匹配**：卧室→暖窗光；浴室→冷荧光+暖边；职场→硬顶光+百叶窗影；户外→自然逆光。
- **组合公式**：`key (soft) + rim (cool) + fill (low)` 为通用三灯。

---

## 06 · 姿势动作（Pose / Motion — 视频核心）

> 纯 T2V 对成人姿态极不稳定，**强烈建议 I2V（图生视频）+ 首尾帧**驱动运动。

- **静态姿势**：`lying on back`、`kneeling`、`bent over`、`on all fours`、`spread legs`、`arch back`、`sitting edge of bed`。
- **动态动作**：`walking toward camera`、`removing jacket`、`running hands through hair`、`turning under water`、`climbing`、`dancing grind`、`stretching languidly`。
- **过渡姿态**：`standing → sitting`、`sitting → lying`、`clothing shift`、`camera slow push-in`、`unbuttoning motion`。
- **挑逗暗示**：`slow hip sway`、`leg cross uncross`、`look-over-shoulder`、`bite lip`、`tug at hem`。
- **联动**：慢动作 → 升格 + 浅景深；湿身 → 水流动效 + 高光闪烁；多人 → 明确排布 `two women one man` 等。
- **参考图 / 首尾帧工作流**：角色参考图锁人物 → 首尾帧锁起止姿态 → 闭源 I2V 模型生成 → 逐镜轻运动 → 剪辑拼接。闭源平台自带内容审查，无需在本 skill 层做额外限制。

---

## 07 · 表情眼神（Expression / Eyes）

- **表情词库**：`sultry`、`shy glance`、`soft smile`、`half-lidded eyes`、`biting lip`、`surprised`、`blissful`、`submissive`、`playful`、`teary`。
- **6 种性格视觉化映射**：`innocent`（大眼微张）、`confident`（挑眉 smirk）、`submissive`（垂眼）、`playful`（俏皮眨眼）、`queen/femdom`（俯视挑逗）、`drunken`（迷离）。
- **8 种眼神专项**：`direct eye contact`、`look-away`、`through-lashes`、`upward glance`、`side-glance`、`closed-eye`、`pleading`、`seductive squint`。
- **阶段 × 表情流变（6 阶段 24 子阶段）**：`anticipation → arousal → peak → surrender → afterglow → drowsiness`，用表情 + 微动作递进。

---

## 08 · 风格胶片（Film / Lens Style）

- **25 种胶片模拟**：`kodak portra 400`、`fuji pro 400h`、`cinestill 800t`、`agfa`、`kodachrome`、`kodak gold 200`、`fuji superia`、`ilford b&w`、`fuji pro 160ns`、`leica monochrome` 等（按想要的色调取）。
- **7 种电影镜头风格**：`Cooke`、`ARRI`、`Panavision`、`Leica`、`Canon`、`russian lens (helios)`、`extreme cinematic`。
- **氛围**：`steamy`、`golden hour`、`rain on window`、`candlelit`、`neon noir`、`soft-focus vintage`。
- **参考锚点（导演/流派）**：`Wong Kar-wai neon intimacy`、`Japanese pink film softness`、`Korean beauty commercial polish`、`90s AV grain`。

---

## 09 · 妆容专项（Makeup）

- **底妆**：`natural dewy`、`matte`、`glass skin`、`flushed cheeks`。
- **眼妆**：`smoky`、`aegyo-sal (under-eye)`、`cat-eye`、`teary mascara`。
- **唇妆**：`glossy`、`nude`、`red`、`bite-mark`。
- **腮红**：`soft pink`、`drunk blush`。
- **美甲**：`natural`、`french`、`colored`、`long acrylic`。
- **场景匹配指南**：清纯 → natural dewy + 淡腮；魅惑 → smoky + glossy red；高潮 → flushed + teary；哥特 → pale + dark。

---

## 10 · 发型饰品（Hair / Accessories）

- **发型**：长度（`short / medium / long / very long`）、造型（`straight / wavy / curly / bun / ponytail / twin-tails / loose / wet`）、发色（`black / brown / blonde / dyed`）、光影（`hair light glow`）。
- **头饰（6 类）**：`hairclip`、`ribbon`、`headband`、`flower`、`glasses`、`cat-ear`。
- **首饰（6 部位）**：`earrings`、`necklace`、`bracelet`、`ring`、`anklet`、`body chain`。
- **联动**：湿发 → `wet strands clinging`；和风 → `kanzashi`；职场 → `glasses + neat bun`。

---

## 11 · 瑕疵细节（Flaws / Realism）

- **体貌瑕疵（realism 用，非缺陷）**：`beauty mark`、`freckles`、`imperfect eyeliner`、`messy bedhead`、`sweat sheen`、`flush`。
- **手部细节**：`natural nail polish`、`vein on hand`、`ring on finger`。
- **足部细节**：`pedicure`、`bare feet`、`toe ring`。
- **体液痕迹扩展**：`sweat drip`、`saliva`、`wet patch`。
- **光影 × 皮肤**：`pore texture`、`subsurface scattering`、`soft specular`。
- **摄影时代感**：`80s grain`、`90s AV`、`00s digital`、`10s+ clean`。
- **年龄感（成年细分）**：`18-22 (young adult)`、`23-28`、`29-35`、`36-45 (mature)`。

---

## 12 · 纹身标记（Tattoo / Marks）

- **50+ 图案纹身**：`flower`、`tribal`、`small script`、`heart`、`dragon`、`sakura` 等。
- **CJK 中日文字（5 Part）**：`cute/sweet (可爱甜美)`、`sexy/seductive (性感魅惑)`、`lewd/insult (淫荡)`、`JAV wa-style (和风)`、`text tattoo (文字纹身)`。
- **四层皮肤融合系统**：`surface ink`、`raised scar`、`birthmark`、`bruise (themed)`。
- **12 色墨水**：`black`、`red`、`pink`、`blue`、`green`、`white`、`gold`、`neon` 等。
- **位置锚定**：`shoulder`、`lower back`、`thigh`、`wrist`、`ankle`、`hip`。

---

## 13 · 道具宠物（Props / Pets）

- **6 大分类**：`sex toy`、`SM gear (rope/blindfold)`、`imaging device (camera/phone tripod)`、`daily ambiance (candle/incense/wine)`、`pet/animal (cat)`、`entertainment electronics`。
- **道具 × 场景速查（13 场景）**：卧室→床/镜；浴室→浴缸/蒸汽；职场→桌/百叶窗；和风→障子/榻榻米；户外→沙滩巾/阳伞。

---

## 14 · 人格卡片（Persona Cards）

- **100 种身份职业人格卡**（外在 / 行为 / 权力关系 / 场景 / 提示词），分三线：
  - **色情线（erotic）**：`married woman`、`OL`、`nurse`、`maid`、`teacher`、`idol`、`queen/femdom`、`amateur`、`mature mother`、`sister`、`gyaru`、`office lady`……
  - **唯美线（aesthetic）**：`bride`、`model`、`painter muse`、`shower girl`、`sleeping beauty`。
  - **可爱线（cute）**：`schoolgirl`、`kawaii`、`neighbour`、`petite`、`tsundere`、`genki`。
- **用法**：选一条人格卡 → 取其"外在 + 行为 + 场景" tag → 拼入 01/03/06/07 槽位。

---

## 15 · 组装公式（Assembly，对齐仓库 00–14 顺序）

```
[00 范例参考]
[01 场景主题] + [02 景别/焦段/构图] + [03 主体(成年锚点)] + [03b 裸露梯度/液体]
 + [04 服装/穿脱状态] + [05 光影] + [06 姿势/动作(I2V驱动)] + [07 表情/眼神]
 + [08 风格/胶片] + [09 妆容] + [10 发型/饰品] + [11 瑕疵/细节]
 + [12 纹身/标记] + [13 道具/宠物] + [14 人格卡]
 + [负向: 结构 + 风格]
→ 模型见 [模型映射]
```

**必选**：01 / 02 / 03 / 05 / 06 / 08 / 负向。
**选读（按需 3–5）**：03b / 04 / 07 / 09 / 10 / 11 / 12 / 13 / 14。
**推荐模型（闭源平台，用户实际运行环境）**：

| 需求 | 主推（闭源） | 备选（闭源） | 说明 |
|------|--------------|--------------|------|
| 高画质写实 I2V | **Veo 3.1** | Sora 2 / Seedance 2.0 | 电影级写实 + 原生音频 |
| 人物运动/姿态可控 | **Kling 3.0 / O03** | Seedance 2.0 / MiniMax H3 | 人体运动强、支持 I2V + 首尾帧 |
| 风格化/动漫成人 | **MiniMax H3** | Vidu Q3 / PixVerse v5.6 | 风格化分支、流体模拟 |
| 动漫一致性 + 首尾帧 | **Vidu Q3** | MiniMax H3 | 非写实一致性 |
| 运镜/镜头控制 | **Runway Gen-4** | — | 运动笔刷/剪辑 |
| 竖屏/社媒/卡点 | **PixVerse v5.6** | Kling 3.0 | 风格化、竖屏 |

- **工作流（技术）**：参考图（角色锁定）→ 首尾帧 → 闭源模型 I2V → 逐镜轻运动 → 剪辑。闭源平台自带内容审查，无需在本 skill 层做额外限制。
- **为何契合**：成人内容对"人物锁定 + 姿态可控"要求极高，闭源 I2V 模型 + 参考图是当前最稳路径。

**最小可用示例**（直接可喂闭源平台）：
```
intimate bedroom golden hour, medium close-up 50mm eye-level, slender east-asian woman 20s,
oversized shirt off shoulder, L4 partially undressed, warm window light shallow DOF,
slow turn, sultry half-lidded gaze, kodak portra 400,
--no bad anatomy, extra limbs, deformed hands, blurry, watermark
```
**更深逐词模板 / 完整 77 例**：直接引用 [`ShuaiHui/nsfw-prompt-templates-asian`](https://github.com/ShuaiHui/nsfw-prompt-templates-asian) 的 15 模块原文。
