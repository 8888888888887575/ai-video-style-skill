# MiniMax H3 提示词完整指南（中英对照 / Complete Prompt Guide）

> **两份来源，一套指南：**
> - **海螺 App / 网页端写法**（`@图片1 人物参考` 自然语言标注）—— 蒸馏自 MiniMax 官方《H3 使用手册》。
> - **官方 API 结构化格式**（字段名即 API 真实 token）—— 蒸馏自 MiniMax 官方 HuggingFace 仓库 `MiniMaxAI/MiniMax-H3` 两份文档：
>   - `docs/VIDEO_PROMPT_WRITING_GUIDE_base_en.md`（Base 四模式）
>   - `docs/VIDEO_PROMPT_WRITING_GUIDE_ref_en.md`（Full-Reference Mode 全参考模式）
>
> **怎么用本文件**：
> - 用海螺 App / 网页交互界面 → 看 **Part A**（`@` 自然语言写法）。
> - 给 Codex / Claude / Cursor 等 agent **直接调 H3 API** → 看 **Part B**（结构化字段，字段名即真实 token）。
> - 两套范式语义对应，对照表见 **§0**；飞书 `@` 写法 → API 字段的速查映射见 **§3**。

---

## 0. 两套范式对照（App `@` vs API 结构化）

| 意图（中文） | 海螺 App 端（`@` 写法，见 Part A） | H3 API 结构化（见 Part B） |
|---|---|---|
| 人物参考 / 锁脸 | `@图片1 是人物参考` | `<Subject 1> is the person in <Picture 1>...` + `subject_definitions` 段 |
| 场景 / 风格参考 | `@图片2 是场景参考` | `<Subject 2> is the environment in <Picture 2>...` |
| 首帧图 | `@图片1 作为开头` | I2VA 指令：`at 0.00 seconds ... <Picture 1> (from [Shot 1]) is fully referenced.` |
| 尾帧图 | `@图片2 作为结尾` | L2VA 指令：`<Picture 1> (from [Shot N]) aligns with the S.SS-second mark` |
| 运镜参考视频 | `@视频1 是运镜参考` | `<Video 1> is the camera-movement reference`（task type = `reference generation`） |
| 音色参考 | `@音频1 是音色参考` | `<Audio 1> is the voice-timbre reference for <Subject X> (Sx)` |
| 台词 | `@人物 说："……"` | `(S1) says: <d>[Chinese] ……</d>` |

---

# Part A — 海螺 App / 网页端写法（`@` 自然语言标注）

> 何时看本部分：① 选了 H3 做多模态参考 / 精准编辑 / 带声音输出；② 给 H3 写提示词老翻车（脸漂移、口型对不上、想一镜到底却切镜、想卡点却没声）。

## A0. 完整公式（铁律）

```
完整提示词 = 参考素材说明 + 核心创意 + 画面过程说明
```

- 三段顺序写、用【】标出三段标题最稳。
- **没上传任何素材 → 整段「参考素材说明」跳过**，但「核心创意 + 画面过程说明」要写更细（见 A5 纯文字模式）。
- 所有素材引用用 `@图片N / @视频N / @音频N`，N = 你上传的顺序号。

---

## A1. 参考素材说明（`@` 标注完整分类）

写给 H3「每个上传文件是干什么用的」。写清 **编号 + 用途**。用途官方清单如下（按需取用）：

| 标注写法 | 含义 / 锁什么 |
|---|---|
| `@图片1 人物参考` | 锁定脸 / 形象（最常用，锁一致性必写） |
| `@图片N 物体参考` | 锁定某个物体（产品、道具、眼镜…） |
| `@图片N 场景参考` | 锁定场景 / 环境 |
| `@图片N 关键帧` | 锁定首帧 / 尾帧（有明确首尾帧需求时写明） |
| `@图片N 音色参考` | 锁定音色（配合音频复用） |
| `@图片N 故事版` | 按故事版分镜生成镜头内容 |
| `@图片N 风格参考` | 按图片风格生成类似风格内容 |
| `@图片N 构图参考` | 按图片中物体构图生成对应构图 |
| `@视频N 动作参考` | 锁定动作 / 表演节奏 |
| `@视频N 运镜参考` | 锁定运镜 |
| `@视频N 视频编辑` | 对视频某内容增删改（精准编辑入口） |
| `@音频N 音频复用` | 生成视频的音频**整体**直接复用参考音频 |
| `@音频N 音频部分复用` | 某声音轨 / 某时间段**部分**复用参考音频 |

规则：
- **想锁脸但没传图 = 必失败**。要脸一致一定上传人物参考图并标「人物参考」。
- 素材里有极想保住的特征，**明确写出来**比只标类型一致性更好（如「保持黑色半扎长发、银色镂空发冠一致」）。
- 音频复刻 / 部分复刻，若对**人声对白 / 唱歌歌词**保持要求高，**强烈建议补具体歌词原文**：`@音频1 作为音频复刻素材，具体歌词是："ABCDEFG"`。

示例：
> @图片1 提供了 xx 角色的形象（多角色时逐个指代清楚），@视频2 提供了动作参考。

---

## A2. 核心创意（一句话锁全片）

必须含 5 要素：**主体 + 地点 + 事件 + 题材/风格 + 特殊运镜**。

- 主体：谁/什么（人/物/动物）。
- 地点：在哪里。
- 事件：在做什么。
- 题材/风格：写实 / 动画 / 电影感 / 广告片 / 纪录片 / 赛博朋克 / 霓虹灯美学 / 涂鸦风…
- 特殊运镜：**默认会切镜**。要特殊镜头写明——航拍 / 一镜到底 / 慢动作。
  - 环绕运镜**别写「环绕」**，写 `truck left+pan right` 或 `truck right+pan left`。
  - 切镜风格写明其一：普通切镜(cut) / 叠化(fade) / 卡点切镜 / 快切。
- 任何元素直接关联引用素材，用 `@图片1 / @音频1` 强调。

示例：
> 一位穿汉服的年轻女子（@图片1）在樱花纷飞的庭院里舞剑，古典国风，电影质感，一镜到底。

---

## A3. 画面过程说明（按 shot 分段）

每个分镜 / 时间段写两部分：**想要**（画面里要出现什么）+ **不想要**（不要出现什么）。

「想要」每段含：**景别 + 内容 + 运镜 + 动作 + 台词 + 音效**。
- 以切镜 shot 作时间戳分段；shot 内写好景别、内容、内部运镜、台词、音效。
- **台词长短对齐镜头**（见 A4，口型问题的头号根源）。
- 想让视频出现**具体文字 / Logo / 标题 / 标语 / 按钮文案 → 必须写出原文**：
  > 手机屏幕上显示标题："AI Video Creation"，按钮文字为："Start Now"。

---

## A4. 镜头拆分铁律（翻车高发区）

1. **台词长度 ≈ 镜头长度**：避免 3s shot 说一大段话，口型必崩。
2. **跨 shot 台词（J-cut / L-cut）H3 能响应**：只要明确写出一句台词跨了哪些 shot 即可，例如「接着上个 shot 继续说…」。
   - 画外音转画内：写明「一个画外音响起说：Wake up。之后切镜到中年妇女近景，她是画外音主人，继续说道：It's time to go to school!」
3. **切镜一致性**：切镜时写清「切到什么景别 + 具体是之前的哪个角色」，跨镜头一致性更好。

---

## A5. 三类模式，提示词分别怎么写

### A. 多模态素材融合（多模态参考）
同时传 人物图 + 动作视频 + 场景图 + 音乐，**每个素材写清角色**：
> @图片1 是人物参考（锁这位女子的脸），@视频1 是动作参考（用里面的舞剑动作），@音频1 是情绪参考（古风配乐）。让这位女子在樱花庭院里按视频里的动作舞剑。

### B. 图生视频（首/尾帧）
- **只传 1 张**：说清是**首帧**（开头画面）还是**尾帧**（结尾画面）。
- **传 2 张（首+尾帧）**：H3 **不会自动加切镜**，只补两帧之间的动作、光影、声音。
> @图片1 是首帧参考图：女子持剑站在樱花树下。让她从持剑起势到舞剑完毕，自然衔接，不要切镜。

### C. 纯文字生成（无素材）
不依赖参考，直接建主体/场景/动作。**文字要更具体**，多用「大全景交代空间 + 中景承载动作 + 特写强调细节」分层：
> 写实自然纪录片风格，电影级真实光影。清晨薄雾中，广阔湿地芦苇荡里，一只优雅白鹤单腿站立浅水中，缓慢转头看向镜头。柔和逆光，雾气在光束里飘动。

---

## A6. 容易踩的坑（对照自查）

| 常见问题 | 怎么改 |
|---|---|
| 只写一段话没分段 | 按 3 段公式拆开写 |
| 素材上传了但没说用途 | 补一句「@图片1 是 XX 参考」 |
| 想用音乐但写「不要 BGM」 | 矛盾，删一个或分场景写 |
| 想一镜到底却写了很多分镜 | 全文保持一段情节描述，删掉【镜头 N】结构 |
| 想要主角脸一致但没传图 | 必传人物参考图并标「人物参考」 |
| 提示词太短（无素材时） | 至少写 主体外观 + 场景细节 + 动作 + 风格 |

---

## A7. 真实示例（来自官方手册，已清理平台特有引用）

### 示例 1 — 大字幕 Trap MV（多素材 + Shot 级分镜 + 文字原文 + 卡点）
```
【参考素材说明】@图片3：场景视觉风格（街道/夜间/地下空间、压迫感构图、环境层次、影像颗粒）
@图片2：文字包装样式（字体质感、图形设计、动态图形排版冲击力）
@图片1：人物形象（脸、发型、服装轮廓、比例、气质、氛围），只参考指定维度，不出现真实品牌/原 logo/可识别文字。
【核心创意】10秒，16:9 横版 trap MV。两位 fly detective 兄弟在多个近景地下空间轮流对镜头 rap，
全程跟随 trap 鼓点律动、卡点硬切，高反差印刷海报质感的英文块字随 bass hit 压屏出现。
地下音乐录像带 + 时尚杂志拼贴 + 高时装质感，兄弟搭档式冷峻 performance。
【画面过程描述】
Shot 1 — 面部极近特写 / 通道压迫感：Detective A 直视镜头开始 rap，眼神冷静锐利；
文字 "TWO FLY" 巨大粗体英文压入画面上下，不遮挡眼睛；律动：808 bass 砸下，"TWO FLY" 瞬间纵向压缩后回弹。
（硬切）
Shot 2 — 中近景半身 / 墙面文字背景：Detective B 对镜头 rap，肩膀头部跟 hi-hat 点拍；
文字 "CLUES" 在人物身后，被头发/肩膀自然遮挡；律动：每个 snare 时文字突然放大、抖动。
（硬切）… Final — 多场景近景 performance montage；主文字 "CASE CLOSED" 巨大压入；
律动随 808 bass hit 硬切重组。禁止全身、禁止多人全景，只用近景/中近景/面部特写/手部特写。
```
要点：文字原文写出 + 每个 shot 标景别/内容/运镜/台词/音效 + 卡点硬切 + 跨 shot 用「（硬切）」衔接。

### 示例 2 — 国风舞剑（多模态 3 段式，锁脸+锁动作+带声）
```
【参考素材说明】@图片1：人物参考（锁这位女子的脸与汉服）；@视频1：动作参考（用里面的舞剑动作）；@音频1：情绪参考（古风配乐，音频整体复用）
【核心创意】10秒，16:9，一位穿汉服的年轻女子在樱花纷飞的庭院里舞剑，古典国风，电影质感，一镜到底。
【画面过程说明】从持剑起势到舞剑完毕，自然衔接不切镜；樱花随风飘落，镜头轻微环绕（truck left+pan right）；
结尾女子收势，花瓣定格。音频整体复用 @音频1 的古风配乐。
```

### 示例 3 — 游戏 UI 角色装备（分秒级分镜，无素材参考结构）
```
角色参考图1，UI风格参考图2。
[0秒-2秒] 高角度俯拍。角色坐在亮紫色地面，参考图1，抬头看向摄像机。右侧显示游戏菜单 UI：开始新游戏 /
继续游戏(高亮) / 设置 / 退出游戏。左上角显示玩家资料 MINIMAX。光标点击"继续游戏"。
[2秒-4秒] 平滑变焦至右臂。UI 面板从右侧滑入，"右臂装备" 面板出现，选中高亮 "幻影之握"，滑动至 "时空之爪"；
右手机械重新配置，青色 LED 灯闪烁更亮。
[4秒-7秒] 摄像机平滑绕到左侧。新 UI 滑入 "武器定制" 网格；左臂逐段拆解更换，可见暴露线路和活塞。
[7秒-8.5秒] 拉回中景。确认配置按钮闪烁，点击，UI 向内收缩消失。
[8.5秒-10秒] 底部出现加载条 0%→100%。环境变暗，暖金光芒渗入。
[10秒-15秒] 她起身，完整赛博朋克贫民窟加载，第三人称视角位于她身后。
```
要点：用 `[起止秒数]` 分段 + 每段景别/内容/运镜/UI 文字原文 + 角色参考图锁身份。

### 示例 4 — 精准编辑（在已有视频上改局部，不动其余）
```
# 角色/物体替换
把视频中的猫换成狗。
# 场景背景替换（高精度指令遵循示范）
将原视频中的桌面替换为标准办公室工位办公桌，背景整体替换为带百叶窗与金属文件柜的办公环境。
新办公桌透视比例需与原镜头完全匹配，桌面材质自然承接原视频光影投射，边缘阴影与高光方向必须与原场景光源严格一致。
背景百叶窗与文件柜的景深虚化程度需与原视频焦点对齐，保持原有空间纵深感。
在此过程中，原视频的镜头运动轨迹、机械臂完整运动时序与速度、画面中其他物品相对位置与空间遮挡关系、
以及整体光照氛围必须保持 100% 不变，确保替换元素与原画面无缝融合。
# 台词/音色修改
将视频1女生说的话："我们之间不可能在一起的，不是不爱，是我们真的走不到最后的"，
改成音频1的台词："别走了，好吗？这一次，我们不要放开彼此"，并略微调整对应的表演。
```
要点：精准编辑 = 参考视频 + 明确「改什么 + 保持不变清单」。一次性可堆多条局部指令（换报纸→绿书、椅子→红沙发、去墨镜、去燃烧、照片→黑本子、左侧加树），H3 高精度指令遵循可一并执行。

### 示例 5 — 手绘发光动画融合（纯文字 + 实拍，无素材）
```
【参考素材说明】无参考素材（纯文字生成视频）。
【核心创意】15 秒，16:9 横版视频。将实拍的傍晚老式电车车厢与手绘发光动画融合：空荡末班电车车厢里，乘客用手机单手临时拍摄，遇到手绘杏橙色发光线在车厢里连续变形（车票→纸燕子→毛毛虫→箭头→小帆船→迷你电车→蜗牛→雨伞→小鱼→整车晚霞云海），最后回到车票碎成纸屑。整体生活感、怀旧、温柔而略带哀愁。
【画面过程描述】
0〜3 秒 — 正向：实拍镜头从拍摄者指尖在起雾车窗上随手画弧线开始。指尖离开，雾痕变成杏橙手绘发光线（蜡笔粉笔混合质感），先贴指尖→绕食指→落掌心卷成车票→被另一手按住→折成扁平纸燕子→沿右侧扶手环飞走。相机慢半拍追，先拍空掌和倒影，再匆忙右晃。│反向：不要平稳广告式构图。
3〜6 秒 — 正向：纸燕子绕吊环飞一圈，尾巴勾住扶手环轻晃发出塑料碰撞声。拍摄者伸手想稳扶手环，纸燕子掠手背散成一串手绘逗号→首尾相连聚成发光毛毛虫→沿座椅靠背爬行（留杏橙粉末）→拉直成涂鸦箭头→指完塌成小帆船沿座椅缝滑走。相机迟一步推进，运动模糊+短暂失焦。│反向：不要新角色出现，所有形态必须首尾相连。
6〜10 秒 — 正向：小帆船滑地板、借电车晃动漂移、拖粉笔灰杏橙线→拍摄者伸脚挡+手捞→船从指鞋间溜过撞半卷车票→卷轴滚动→变成 2 节迷你手绘电车→沿地板黑色缝线行驶→冲到路线图下车头一抬变扁平蜗牛→爬上金属立柱、回头抖触角催拍摄者追。│反向：不要立体 CG。
10〜13 秒 — 正向：蜗牛触角碰车门按钮→按钮周围亮起杏橙手绘光圈→变手绘小雨伞→贴车门玻璃下滑→翻面变带铃铛尾巴手绘鱼→游到下方用尾巴扫拍摄者手腕→拍摄者后退撞座椅、镜头一歪再追车厢中央。│反向：不要恐怖怪物化、不要扑咬。
13〜15 秒 — 正向：手绘鱼从车门玻璃散开→所有线迹沿窗玻璃/地板木纹/座椅缝/扶手环/路线图/天花板灯罩蔓延→整节车厢变巨大夕阳云海→拍摄者后退伸手→空中云带落掌心变回车票→满车厢晚霞线散成小纸屑→画面在温柔余韵中结束。│反向：不要切镜到别的场景、不要凭空的恐怖元素。
【整体要求补充】
▍手绘动画风格（贯穿全片）— 始终是平面逐帧手绘发光涂鸦，不是立体角色或 CG 生物；线条粗细/轮廓/填色每帧轻微变化，边缘有蜡笔/粉笔/彩色铅笔/粗糙笔刷/粉彩毛边；中心色：杏橙、暖橘、淡奶白、少量柔和金；每次变形保留前一形态痕迹（车票虚线边、纸燕子翅膀…），让观众感到是同一存在连续变形。
▍相机节奏 — 始终比手绘动画慢半拍；保留手持手机抖动、电车行驶摇晃、靠近玻璃的短暂失焦、窗外街灯曝光跳动、自然运动模糊。
▍禁止项 — 禁止精密 3DCG/毛绒玩具风/三维渲染/平滑霓虹管/均匀矢量线；禁止电影感过强布光、广告摄影式整洁构图；禁止字幕/标志/背景音乐；禁止巨大眼睛、裂嘴、牙齿、威吓、扑咬、突然黑屏、跳吓、恐怖怪物化。
▍环境音 — 只用老式电车车厢内真实声音（车轮轨道摩擦、车厢摇晃、扶手环碰撞、车门按钮机械声、纸质车票摩擦、布座椅碰触、拍摄者小声惊呼与急促脚步）；手绘动画声音：极轻粉笔摩擦、玻璃滑动刮擦、柔软电子颤音、短促滑稽鸣叫。
```
要点：**纯文字模式的「正向/反向」成对约束法**——每个时间段既写「正向要什么」又写「反向不要什么」，比单写「不想要」更稳、更能压住 H3 的自由发挥；形态连续变形靠「保留前一形态痕迹」锚定同一主体；相机故意慢半拍 + 手持抖动营造真实跟拍感。这套写法可直接套用到任何「实拍+手绘/特效融合」类需求。

---

## A8. 参数速查

- 时长 4–15s；**24 FPS**；原生双声道（所有结果默认带声）。
- 分辨率两档：
  - **768p 模式（已开放）**：输出宽高比在 **16:9 ~ 9:16** 之间时，输出为**短边 768 像素**；否则输出分辨率**总像素约 1M**（如 21:9 时为 1536×672）。生成结果可升档至 1440p。
  - **1440p 模式（官方推荐版）**：短边 1440 像素，画质更优。
- **画幅比例**：在 **21:9 / 16:9 / 4:3 / 1:1 / 3:4 / 9:16** 范围内指定，或选**自动模式**由 H3 自行判断输出宽高比。
- 输入：首/尾帧入口 图片 0/1/2 张([256,5760]，宽高比 5:2~2:5)；全能参考 图片≤9 / 视频≤3段(2–15s,总≤15s) / 音频≤3段(需配图或视频,2–15s,总≤15s)，**混合≤12 文件**。
- 格式：视频 H.264/HEVC(内音 AAC/MP3)；图片 JPG/JPEG/PNG/WEBP/HEIC/HEIF；音频 WAV/MP3。
- 大小：视频单 50MB / 图片单 30MB / 音频单 15MB；API 请求体 64MB（推荐用 URL 传素材）。
- 提示词 ≤ 7000 字符。TTS 精准覆盖 11 语（中/英/日/韩/法/德/西等），衍生 40+ 语。

---

## A9. 商用场景分类索引（按场景取用法）

H3 官方把「商用级全场景生成」分成以下方向。拿到需求先对号入座，再决定走 Part A 的哪段 / 参考哪个示例：

| 场景方向（中英） | 典型需求 | 本指南对应参考 |
|---|---|---|
| **品牌大片与影视内容** Brand film & video | 电影感品牌片、TVC、海报动态化、影视预告 | A2 核心创意5要素 / A7 示例1（大字幕 MV）/ 示例5（实拍+手绘） |
| **视觉创意与内容包装** Visual creative & packaging | 创意短片、特效包装、审美 MV、视觉实验、社媒素材 | A7 示例1 / A5 三类模式 / A1 @标注13类 |
| **AI 剧情内容创作** AI narrative | 竖屏短剧、漫剧、角色演绎、AI 配音 | A4 镜头铁律 / A7 示例4（精准编辑台词）/ A3 画面过程 |
| **产品与电商营销** Product & e-commerce | 产品展示、卖点视频、品牌/投流素材 | A1 物体参考 / A2 特殊运镜 / A3 文字原文（产品名/卖点） |
| **数字体验与游戏创意** Digital & game | 游戏 UI、网页 UI、交互演示、功能动效 | A7 示例3（游戏 UI 分秒分镜）/ A3 `[起止秒数]` 分段 |
| **硬件 / 实体工业 / 具身智能** Hardware & embodied AI | 机器臂演示、工业产品、具身智能动作展示 | A5 图生视频（首帧）/ A7 示例4（场景背景精准替换） |
| **动画与风格化影像** Animation & stylized | 游戏 CG、角色 PV、动漫 PV、二次元、IP 内容 | A1 风格参考 / A7 示例2（国风舞剑）/ 示例5（手绘） |

> 提示：文档里每个方向都给了**成片级完整 Prompt 范例**（含分镜、运镜、声音、禁止项）。需要某个方向的"官方成片模板"时，回原飞书手册 §三 对应小节取用即可——本指南聚焦**可复用的写法方法论**，不重复搬运成片。

---

# Part B — 官方 API 结构化格式（给 Codex / Claude / Cursor 直调）

> 本部分 = H3 **API 实际接受的结构化提示词格式**——字段名 / 标签（如 `integrated_multimodal_description`、`<Subject 1>`、`[Shot 1]`）就是 API 真实 token。

## B1. Base 四模式（T2VA / I2VA / FL2VA / L2VA）

四种模式区别只在"是否给参考图、图放在开头还是结尾"：

| 模式 | 英文全称 | 中文 | 首帧指令 |
|---|---|---|---|
| **T2VA** | Text-to-Video (Audio) | 纯文生视频 | 无（直接写三核心字段） |
| **I2VA** | Image-init T2VA | 图生视频（图=首帧） | 有，指定首帧 |
| **FL2VA** | First-Last T2VA | 首+尾帧生视频 | 有，指定首帧+尾帧 |
| **L2VA** | Last T2VA | 尾帧生视频（倒推开头） | 有，指定尾帧 |

### B1.1 终稿结构（Final Prompt Structure）

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

### B1.2 沿时间线展开 multimodal description

- `[Shot 1]` 开头**不写时间戳**；后续镜头用 `[Shot N] At MM:SS.mmm, ...`（切镜时间必须严格递增且在视频时长内）：
  ```text
  [Shot 1] Live-action, cinematic, a medium-wide shot frames...
  [Shot 2] At 00:03.500, the camera cuts to...
  ```
- `[Shot 1]` 开头先定**整体风格 + 初始构图**。常用风格词（保留英文）：
  `Cinematic` / `live-action` / `2D-animated` / `3D CG` / `claymation`(黏土) / `watercolor`(水彩) / `vintage film`(复古胶片)
- 图生任务从参考图推导风格；纯文生从用户文字选风格。

### B1.3 镜头与切镜（Shots and Cuts）

- 普通切镜动词：`the camera cuts to` / `the shot cuts to` / `the shot transitions to` / `the shot changes to` / `the shot switches to`。
- 用户明确要求时可用 cross-dissolve(叠化) / fade(淡入淡出) / wipe(擦除)。
- 切镜必须带来**新信息**（主体/空间/状态/视角/时间）。若只改距离或微角度，优先用**运镜**而非切镜。
- 跨 cut 的连续性写法：`continues seamlessly across the cut` / `continues uninterrupted into the next shot` / `carries over from the previous shot` / `remains audible across the transition`。

### B1.4 运镜三维度（Motion Type + Amplitude + Speed）

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

### B1.5 说话人 / 台词 / 歌唱（Speakers, Dialogue, Singing）

- 说话/歌唱/画外人声用**稳定 ID**：`(S1)` `(S2)`，多人同说用复合 ID `(S1,S2)`。同一说话人跨镜头 ID 不变；不发声的角色不给 ID。
- 台词格式：`<d>[语言标签] 原文</d>`——**原文逐字保留，不翻译不改写**：
  ```text
  The young woman with a quiet, breathy voice (S1) says: <d>[English] I get off at the next station.</d>
  The two children (S1,S2) shout together, <d>[English] Wait for us!</d>
  ```
- 首次出场要先用视觉+音频上下文建立稳定身份（角色类型/年龄/性别/是否在画内/音高/音色/语速/口音）。身份短语、`(Sx)`、动作、语气都在 `<d>` **外**；`<d>` 内只放语言标签 + 用户原文。
- **画外音（voiceover）**：用 `says in an off-screen voiceover`，并在其后注明 `while his lips remain completely closed`（嘴保持闭合）。
- **台词跨 cut**：在连接点两侧都用 `<scenetrans>`，并明确 `the audio continues across the cut`；视频结束截断用 `<cutoff>`。

### B1.6 屏幕文字（On-Screen Text）

- 画面里实际可见的标语/招牌/字幕/霓虹字，用**英文双引号**包裹，原文逐字保留（不翻译）：
  ```text
  A red neon sign reading "营业中" glows above the doorway.
  ```

### B1.7 overall_soundscape / non_diegetic_music 写法

- `overall_soundscape`：1–4 句英文连续段落，概括全程环境音/物理动作音/非语言人声（风、雨、交通、脚步、布料、撞击、呼吸、笑、喘）。台词/歌/画内乐已在 multimodal 里，这里不重复。用户要求全程静音才用 `N/A`。
  ```text
  overall_soundscape: Steady rain taps against the café windows while low room ambience continues underneath. The entrance bell rings once, followed by wet footsteps and the soft scrape of a chair.
  ```
- `non_diegetic_music`：1–3 句，描述角色听不到、仅观众可听的配乐，聚焦乐器/速度/节奏/动态变化，不用抽象情绪词、不解释情绪功能。无则用 `N/A`。
  ```text
  non_diegetic_music: Sparse piano notes at a slow tempo, joined by sustained low strings that gradually increase in volume before fading out.
  ```

### B1.8 四个官方 Case（原样保留英文，附中文要点）

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

## B2. Full-Reference Mode（全参考模式）— 图/视频/音频参考 + 精准编辑

用于：上传参考图/视频/音频，或做角色/物体/背景/光影替换、台词/音色修改等精准编辑。输出是**六段固定结构**（全英文写，仅 `<d>` 内台词/歌词和画面可见文字保留原文语言）。

### B2.1 六段结构（顺序固定）

| 段（英文原文） | 中文 | 作用 |
|---|---|---|
| `subject_definitions` | 参考定义 | 定义被引用的内容与标签 |
| `summary` | 摘要 | 概括任务类型 / 目标视频 / 主要参考关系 |
| `retention_analysis` | 保留分析 | 每个参考内容如何被保留/转移/复用 |
| `detailed_description` | 详细描述 | 按播放顺序描述视觉/动作/镜头/声音/台词 |
| `overall_soundscape` | 整体声景 | 环境音/物理音 |
| `non_diegetic_music` | 非剧情音乐 | 仅观众可听配乐 |

### B2.2 四类参考标签（Reference Labels）

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

### B2.3 任务类型前缀（summary 开头，方括号）

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

### B2.4 关系标记（Relationship Markers，固定英文值）

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

### B2.5 detailed_description 要点

- 生成任务通常 **350–500 英文词**；台词密集优先塞满台词时间线而非机械凑字数。视频编辑类随源视频复杂度伸缩。
- 风格在 `[Shot 1]` **之前**用 1–2 句英文开门：
  ```text
  The target video is in a cinematic, literary music-video style with soft lighting and a slightly desaturated color palette.
  [Shot 1] The scene opens in a crowded urban street...
  ```
- 标签在**首次清晰出现**处插入（描述其特征/画面位置/当前动作），后续镜头沿用同名标签不再重定义。
- 具体帧锚用自然短语：`the shot begins from <Picture 1>` / `the shot's keyframe corresponds to <Picture 2>` / `the shot ends on <Picture 3>`。
- 说话人/音频源：被引用主体实发声 → 同时写 `<Subject N> (Sx)`；同一主体画外音 → 同形式标 `off-screen`；说话人不对应已定义主体 → 稳定声音描述 + `(Sx)`。若人声只存在于直接复用的 BGM/完整音轨里、无具体人产生 → 用 `<Audio N>` 作可听源，**不要**另造 `(Sx)`。

### B2.6 完整官方示例（咖啡店 Samoyed 案例，原样保留英文）

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

# Part C — 案例拆解库（来自官方手册 vrfi1sk8a0，逐案例对应规则）

> **拆解依据说明**：手册案例视频为飞书内嵌流媒体，无法直接逐帧分析画面；以下拆解基于手册给出的**提示词原文 + 成片文字描述**。每个案例给出「用了什么模式 → 对应本指南哪条规则 → 可复用套路」。案例与 Part A / Part B / A7 / A9 的规则互链，避免重复搬运成片。

## C0. 案例总览表（全部案例 → 规则映射）

| # | 案例（手册章节） | 模式 | 商用方向 | 对应规则 | 提示词亮点 |
|---|---|---|---|---|---|
|1|望远镜寻MINIMAX装置|多图关键帧+运镜约束|品牌大片|A1(关键帧/@标注)+A3+A4(运镜)|4图连续关键帧、双圆镜片遮罩、rack focus、望远镜转场|
|2|史诗太空歌剧院线预告|文生+剪辑节奏|品牌大片|A3(切镜)+A6|硬切/爆闪/黑场/跃迁，电影预告片式文字包装|
|3|科幻悬疑电影短预告|文生|品牌大片|A2(风格)+A3|文字从深空渐入、被星光扫亮、字距展开|
|4|15秒轻悬疑犯罪片头|文生+动态图形|视觉创意|A3(转场)+声音设计|漫画拼贴、转场跟鼓点、BGM乐器时间线|
|5|古装武侠竹林短剧|文生|AI剧情|A2(色调)+表演约束+A6|冷蓝墨绿雪夜、浅景深、正反打、禁字幕|
|6|室内家庭争吵短剧|文生|AI剧情|A2+表演语气约束|竖屏9:16、真实表演、对峙升级|
|7|时尚眼镜广告|多模态(视频+图)|产品电商|A1(参考用途)+A5A|参考视频定节奏+人物图+眼镜图|
|8|Herman Miller椅子360|图/视频参考|产品电商|A3(运镜)+工程动画|白棚、慢节奏、功能可视化|
|9|皮皮犬2D反应游戏UI|文生(纯文字)|游戏创意|**C1 深度**|固定镜头、UI稳定、图1-4动作一一对应|
|10|灵宠图鉴UI|全参考(图)|游戏创意|**C2 深度**+B2|Image1 UI参考+Images2-5灵宠映射|
|11|机械臂抓取|文生|硬件工业|A3(固定镜头动作)|极简动作描述|
|12|机械臂换背景|精准编辑|硬件工业|**C11 深度**+编辑类|透视/光影/时序100%不变|
|13|黏土狐狸熔岩飞跃|文生+大动态运镜|动画风格化|A3(运镜)+A2|黏土质感、慢动作英雄飞跃|
|14|国风仙侠PV|多模态(图2人物+图1分镜)|动画风格化|A1+示例2|锁脸锁分镜、近景露脸远景背影|
|15|乙游男主PV|图参考(锁脸)|动画风格化|A1(人物参考)|严格角色身份参考|
|16|FPS第一人称|文生|动画风格化|A3(主观镜头)|手持游戏镜头、准星扫过|
|17|Minecraft像素化|多素材(6图+2视频)|多模态|**C5 深度**+A1|真实环境保留、局部像素化、参考视频节奏|
|18|咖啡→沙漠一镜到底|多素材(@图片1/@图片2)|多模态|**C6 深度**|微距转场、材质无痕转化、禁硬切|
|19|角色说话+音色克隆|音频参考|音色克隆|A1(音色参考)+TTS|音频1音色参考极简示例|
|20|猫换狗|精准编辑(角色)|编辑|A4(局部指令)|单条替换|
|21|加人/换外套|精准编辑(物体)|编辑|A4|局部增/改|
|22|去绿幕换童话背景|精准编辑(场景)|编辑|C11关联|背景匹配人物动作|
|23|改光影/换窗外|精准编辑(场景)|编辑|A4|改光照匹配|
|24|改台词+表演|精准编辑(声音)|编辑|A4(台词)+表演|音频1台词替换|
|25|高精度多条件编辑|精准编辑(多条件)|编辑|**C12 深度**+示例4|一次堆多条局部指令|
|26|易拉罐→可乐系列|精准编辑|编辑|C12关联|品牌替换+台词联动|
|27|魔术师西装互换|创意理解|编辑|C12关联|颜色互换、手套不变|
|28|涂鸦特效|创意+文字特效|编辑|C12关联|手绘涂鸦随靠近增多|
|29|Trap MV|多模态+Shot分镜|音乐MV|**C3 深度**+示例1|A7示例1|
|30|手绘发光动画融合|纯文字+成对约束|视觉/动画|**C4 深度**+示例5|A7示例5|

> 方法论内的 @标注示例、三类模式示例已分别对应 A1、A5，不重复列入。

## C1. 皮皮犬 2D 反应游戏 UI（pre 0，文生视频）

**原文片段**：生成一段10秒、4:3 横向构图的游戏视频…主角始终是同一只皮皮的小比格犬…视频是一个"按方向键躲手掌"的快节奏小游戏…图1当底部"上"箭头高亮时手掌从下向上伸…所有手掌方向、箭头高亮、小比格躲闪必须一一对应。

**结构拆解**：
- 模式：纯文字文生视频（无素材）。
- 绑定 Part A：A2（主体/地点/事件/风格/运镜全含）、A3（画面过程按图1-4 节拍分段）、A5C（纯文字分层写法）。
- 关键技巧：**「UI 稳定性约束」+「动作一一对应表」**——把"箭头高亮方向 → 手掌来向 → 角色躲闪动作"写成显式映射表，避免 H3 自由发挥错位。这是 A4 镜头铁律的进阶：不仅镜头对齐，连交互状态都对齐。
- 负面约束密集：不要现代电子UI、不要真实摄影、不要可读文字。

**可复用套路**：做"游戏/交互演示"类视频，把界面元素状态与角色动作列成**对应表**喂给 H3，一致性远胜散写。

## C2. 灵宠图鉴 UI（pre 1，全参考模式英文）

**原文片段**：Use Image 1 as precise UI/layout reference… mouse cursor also as precise cursor style reference… Use Images 2-5 as precise pet references: Image2=card A=MIRRA POD… Generate 15s 16:9. Camera fixed. Keep Image1's interface structure stable… four pets cute/agile… only animate mouse, selection, title, current pet.

**结构拆解**：
- 模式：**全参考模式（Full-Reference）**——对应 Part B B2。
- 绑定规则：A1（素材用途标注，这里用英文 Image N = 用途）、B2.2（四类标签）、B2.3（任务类型）。
- 关键技巧：**「稳定层 / 动画层」分离**——明确"界面结构稳定不变，只动画化鼠标/选中态/主展示灵宠/特效"。这是精准编辑思想的逆向应用：告诉模型哪些**必须锁死**。
- 负面约束：不要新增文字、不要乱码、不要UI扭曲、不要漂移。

**可复用套路**：UI/产品演示类，先声明"哪些层固定、哪些层动"，比只说"保持风格"有效得多。对应 B2 的 detailed_description 要点。

## C3. 成片大字幕 Trap MV（pre 2，多模态 + Shot 级分镜）— 关联 A7 示例1

**原文片段**：【参考素材说明】@图片3场景风格/@图片2文字包装/@图片1人物形象…【核心创意】10秒16:9 trap MV…【画面过程】Shot1面部极近特写…"TWO FLY"巨大粗体英文压入…808 bass砸下瞬间纵向压缩后回弹；hi-hat roll时字母边缘高速细碎震动…硬切。

**结构拆解**：
- 模式：多模态素材融合（@图片1/2/3 各司其职）+ 三段式（参考素材说明/核心创意/画面过程）。
- 绑定：A1（@标注13类之"场景/文字/人物参考"）、A0（三段式铁律）、A3（Shot级分镜）、A4（硬切/J-cut）、声音设计（文字随bass hit律动）。
- 关键技巧：**「文字作为节奏乐器」**——把屏幕文字的压缩/回弹/震动/扫描错位**绑定到具体鼓点(808 bass/hi-hat/snare)**，而非泛写"卡点"。这是把 A4 的"台词长短对齐镜头"升级为"视觉元素对齐音乐事件"。
- 防遮挡：文字"不遮挡眼睛"反复强调——对应 A3 的"主体保一致/不被破坏"。

**可复用套路**：音乐 MV/卡点视频，把每个视觉动效**锚定到具体乐器/节拍事件名**，成片同步感最强。

## C4. 手绘发光动画融合（pre 3，纯文字 + 正向/反向成对约束）— 关联 A7 示例5

**原文片段**：【参考素材说明】无参考素材（纯文字）【核心创意】15秒…将实拍傍晚老式电车车厢与手绘发光动画融合…【画面过程】0~3秒-正向：实拍从指尖画弧线开始…反向：不要平稳广告式构图。3~6秒-正向：…反向：不要新角色出现，所有形态必须首尾相连…

**结构拆解**：
- 模式：纯文字文生视频。
- 绑定：A5C（纯文字分层）、A2（风格/情感）、A6（避坑，这里用"反向约束"实现）。
- 关键技巧：**「正向/反向成对约束法」**——每个时间段既写"要什么"(正向)又写"不要什么"(反向)，且反向约束精准到"不要新角色/不要立体CG/不要切镜到别场景"。比单写禁忌更能压住 H3 自由发挥。
- **形态连续变形锚定**：用"保留前一形态痕迹"(车票→纸燕子→毛毛虫…)保证同一主体连续变形不跳戏。
- 相机"慢半拍+手持抖动"营造真实跟拍——对应 A3 运镜细节。

**可复用套路**：形变/转场类创意，用"正向要什么+反向不要什么"双写，并把连续形态用"首尾相连"锚定。

## C5. Minecraft 像素化（多素材联合参考）

**原文片段**：参考剪辑图1-6，严格参考示例视频视频1的镜头节奏、转场风格及音乐…仅将视频1画面中的树木、轿车转化为3D像素或体素积木风格(Minecraft style)，风格参考图1。像素化物体运动轨迹正常，保留真实环境阴影和透射光。

**结构拆解**：
- 模式：多素材融合（6图 + 2视频：参考视频1节奏/转场/音乐 + 图1风格）。
- 绑定：A1（素材用途：图1=风格、视频1=节奏转场音乐）、A5A（多模态融合）、编辑思想（局部替换）。
- 关键技巧：**「局部风格化，保留真实基底」**——只改指定物体为像素风，真实环境的阴影/透射光/运动轨迹全部保留。这是精准编辑的"选择性风格迁移"。
- 对应规则：与 C12 高精度编辑同源，但这里是"风格"而非"物体"替换。

**可复用套路**：做"现实×风格化"混合（如真人+动漫、实景+像素），明确"哪些保留真实、哪些变风格"。

## C6. 咖啡→沙漠 一镜到底（微距转场）

**原文片段**：@图片1镜头快速推进到咖啡表面奶泡纹理…在咖啡粉颗粒、奶泡起伏、液体旋涡与@图片2中沙丘沙脊、风蚀纹理高度相似的瞬间，自然无痕转化为沙漠地貌…严格避免画面开裂，不要黑屏，不要硬切，不要明显特效，一镜到底。

**结构拆解**：
- 模式：多素材融合（@图片1 微距咖啡 + @图片2 沙漠），纯文字驱动转场。
- 绑定：A1（@图片标注）、A3（一镜到底/无切镜）、A5A。
- 关键技巧：**「材质相似点触发无痕转场」**——找两个画面的"共同材质特征"(颗粒/纹理)作为转化契机，而非硬切。负面约束密集：不要开裂/黑屏/硬切/拼接感。
- 对应 A6 避坑："一镜到底中间不要拼接"。

**可复用套路**：做"无缝变形/世界切换"类，用"材质连续性"作为转场锚点，并堆负面约束保无痕。

## C7. 品牌望远镜 MINIMAX 装置（多图关键帧 + 遮罩 + 运镜约束）

**原文片段**：图1至图4连续关键帧，模拟老式望远镜寻MINIMAX装置。开头虚焦手持晃动后快速拉近rack focus至图1，图间望远镜扫视转场（甩动、运动模糊、光学拖影、曝光闪烁）在最模糊处切换并迅速稳定重新对焦。全程固定双圆镜片遮罩（黑色羽化暗角、位置大小边缘虚化绝对一致无变形漂移）仅内部画面运动。

**结构拆解**：
- 模式：多图关键帧（图生视频的扩展：不止首/尾帧，而是连续关键帧序列）。
- 绑定：A1（关键帧标注）、A3（运镜：rack focus/扫视转场）、A4（遮罩稳定性——"位置大小边缘虚化绝对一致无变形漂移"是硬约束）。
- 关键技巧：**「固定遮罩 + 内部运动」**——用"双圆镜片遮罩绝对不变"锁死框，只让内部画面动。这是 A4 镜头铁律的"框稳定"范式。
- Wes Anderson 式 35mm 胶片质感——对应 A2 特殊风格。

**可复用套路**：做"窥视/望远镜/取景器"视角，声明"遮罩/框绝对固定，仅内部运动"，避免 H3 漂移。

## C8. 15秒轻悬疑犯罪片头（文生 + 动态图形 + 声音）

**原文片段**：整体风格参考这些图的视觉语言：复古日系动画片头、硬边剪影、漫画拼贴、非对称分屏、强烈几何色块…片头动效像动态图形拼贴：黑底线框先出现，分屏边界快速划出，色块和画格逐块贴入…转场形式丰富：圆形黑胶遮罩、车门竖切、红线切割…所有转场跟随鼓点。BGM：原创15秒…低音持续音、紧张弦乐拨奏…

**结构拆解**：
- 模式：文生视频（参考图风格，无强制锁脸）。
- 绑定：A1（风格参考）、A2（风格/氛围60%悬疑40%爵士）、A3（转场设计）、声音设计（BGM 乐器编排详述）。
- 关键技巧：**「转场词典 + 鼓点绑定」**——列出具体转场类型(黑胶遮罩/车门竖切/红线切割…)并全部绑定鼓点，避免 H3 用柔和溶解。负面：不要柔和溶解/流体转场。
- 声音：把 BGM 的乐器组成、进入时间点(第3秒鼓点、第6秒贝斯…)写清——对应声音设计原则。

**可复用套路**：片头/包装类，给"转场类型清单 + 各自绑定鼓点"，并写清 BGM 乐器时间线。

## C9. AI 剧情：竹林 / 家庭争吵（文生 + 表演 + 色调）

**原文片段(竹林)**：16:9 横向电影画幅，夜晚竹林，冷蓝、墨绿、灰黑低饱和色调，薄雾弥漫，细雪飘落…浅景深，电影级光影…人物面部特写为主，正反打剪辑，节奏克制但紧张。不要字幕、不要现代元素…(家庭争吵)：竖屏9:16，真实真人表演…秦皓瑄语气愤怒委屈急切；中老年女性尖锐强势质问…强烈对峙感，节奏逐步升级。

**结构拆解**：
- 模式：文生视频（无素材，纯文字建立主体/场景/表演）。
- 绑定：A2（主体/地点/事件/风格/色调）、A5C（纯文字分层：大全景交代+中景承载+特写强调）、A6（密集负面：不要字幕/现代/动画感/喜剧）。
- 关键技巧：**「表演语气脚本化」**——把角色语气(愤怒/委屈/尖锐/强势)和情绪曲线(逐步升级)写成指令，引导 H3 的生成表演。这是 A2"主体事件"的细化到"表演维度"。
- 色调/光影写具体(冷蓝墨绿雪夜、浅景深、逆光)，而非泛写"电影感"。

**可复用套路**：剧情/表演类，把"角色语气 + 情绪曲线 + 色调光影"写成可执行指令，远胜"电影感"泛写。

## C10. 时尚眼镜广告（多模态参考）

**原文片段**：生成一支竖屏9:16高级时尚眼镜广告片，整体参考所给视频的分镜节奏、剪辑速度、白棚质感和冷峻时尚氛围。主视觉人物参考图片1，两位全身女模特…保持服装高级感、姿态、白棚光影、时装秀场气质。眼镜设计参考图3…人物外貌细节参考图2。

**结构拆解**：
- 模式：多模态融合（参考视频=分镜节奏/剪辑/氛围 + 图1人物 + 图3产品 + 图2细节）。
- 绑定：A1（素材用途分角色标注：视频=分镜节奏、图1=人物、图3=产品、图2=细节）、A5A、A5B（若有首帧）。
- 关键技巧：**「参考视频负责'节奏/剪辑/氛围'，图片负责'视觉实体'」**——把"动的部分"和"静的实体"分给不同素材，职责清晰。
- 负面：不要现代建筑/不要动画感(隐含保真实)。

**可复用套路**：广告/产品片，用"视频参考定节奏氛围 + 图片参考定人物/产品实体"的分工法。

## C11. 机械臂换背景（精准编辑 + 硬约束）

**原文片段**：改背景的提示词：将原视频中的桌面替换为标准办公室工位办公桌，背景整体替换为带百叶窗与金属文件柜的办公环境。新办公桌透视比例需与原镜头完全匹配，桌面材质需自然承接原视频光影投射，边缘阴影与高光方向必须与原场景光源严格一致。背景百叶窗与文件柜的景深虚化程度需与原视频焦点对齐…原视频的镜头运动轨迹、机械臂完整运动时序与速度、画面中其他物品相对位置与空间遮挡关系、以及整体光照氛围必须保持100%不变。

**结构拆解**：
- 模式：精准编辑（场景背景替换）。
- 绑定：编辑类（对应 A7 示例4 场景背景替换）、A4（局部指令遵循）。
- 关键技巧：**「编辑 = 改什么 + 不变清单(100%)」**——不仅说"换成办公室"，还穷举"必须100%不变"的维度(镜头轨迹/机械臂时序/物品遮挡/光照氛围)。这是高精度指令遵循的典范。
- 对应 C12 的"一次堆多条局部指令"。

**可复用套路**：任何替换/编辑，配套写"不变清单"比只说"改X"稳得多。

## C12. 高精度多条件编辑（一次堆多条局部指令）— 关联 A7 示例4

**原文片段**：将参考视频中的报纸替换为一本绿色封皮的书；人物所坐的椅子改为红色沙发；去掉人物佩戴的墨镜，保留清晰面部；移除汽车燃烧效果…照片改为黑色小本子；同时在画面左侧增加一棵树。

**结构拆解**：
- 模式：精准编辑（多条件并行）。
- 绑定：A7 示例4（精准编辑）、A4（局部指令遵循）、编辑思想。
- 关键技巧：**「多条独立局部指令并列，用分号/换行分隔」**——H3 高精度指令遵循可一并执行多条不冲突的局部修改。每条都是"把A改成B"或"去掉C保留D"的原子操作。
- 易拉罐→可乐系列、魔术师西装互换、涂鸦特效都是同族变体(品牌替换/颜色互换/新增特效)。

**可复用套路**：复杂编辑不要写一段模糊长句，拆成"每条一个原子操作"的清单，H3 执行更准。

---

## §3. 飞书 `@` 写法 → 官方 API 字段 速查映射

| 你想做的（中文） | 海螺 App 端写法（Part A） | 官方 API 结构化写法（Part B） |
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
