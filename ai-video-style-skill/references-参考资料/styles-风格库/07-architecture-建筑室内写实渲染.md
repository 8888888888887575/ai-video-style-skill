# 07 · 建筑 / 室内写实渲染（Architectural & Interior Visualization）

> 定位：建筑立面 / 室内空间 / 装修效果图的写实渲染视频——草图转写实、效果图换季节、毛坯转精装、平面转实景、光追设计。AIX Studio「AI + 设计院 / 家装」高频赛道。
> 与通用写实 CG 的区别：**结构比例不可错**。建筑观众能一眼看出层高、开间、梁柱是否合理，因此本类几乎全程依赖**参考图 I2V 锁结构**，纯 T2V 只用于概念探索。
> 结构严格对齐 `_TEMPLATE-风格母版.md` 15 模块。提示词正文英文，中文仅作注释。

---

## 00 范例（Examples）

### 例 1 · 草图转写实（I2V，锁结构）
```
[Reference image: hand-drawn architectural elevation sketch]
Transform the reference sketch into a photorealistic architectural rendering while keeping
the exact same massing, floor count, window grid and facade proportions,
slow drone arc around the building at constant radius, 24mm wide, eye-level to slightly low angle,
late afternoon natural daylight with soft directional shadows, clear blue sky with thin cirrus,
board-formed concrete with visible tie holes, warm oak louvres, glass curtain wall with clear reflections
of the sky and neighbouring trees, global illumination, ray-traced soft shadows,
architectural visualization, Twinmotion-grade realism, balanced exposure
--no changed floor count, warped windows, melting geometry, distorted perspective, extra buildings, garbled signage
```
> 草图转写实第一原则：**先声明"保持不变的量"**（体量 / 层数 / 窗格 / 比例），再谈材质与光。不写这句必被重设计。

### 例 2 · 室内 walkthrough 一镜
```
Interior walkthrough of a 3.2-metre-high open-plan living room in a modern apartment,
continuous one-shot camera gliding forward from the entry through to the balcony door,
20mm wide with corrected verticals, steadicam smoothness, constant walking pace,
morning daylight flooding through floor-to-ceiling windows, soft bounce off the pale oak floor,
warm 3000K downlights as accent, balanced exposure with no blown-out window,
micro-cement wall, matte oak flooring with realistic plank joints, linen sofa with natural drape,
photoreal interior, ray-traced global illumination, accurate scale of furniture to ceiling height
--no fisheye distortion, tilted verticals, blown-out windows, floating furniture, impossible room proportions
```
> 室内广角必须写 `corrected verticals`，否则墙线外扩像鱼眼；`no blown-out window` 是室内片第一曝光问题。

### 例 3 · 效果图换季节（首尾帧）
```
[First frame] The same residential courtyard in lush summer: green canopy, bright foliage, dry paving.
[Last frame] The identical courtyard in deep winter: bare branches, snow on the roof and paving, frozen pond.
Locked-off camera, identical framing and focal length, only the season changes,
summer: high 5600K daylight, crisp shadows / winter: low-angle 4000K pale sun, long soft shadows, cool ambient
building geometry, material palette and window layout remain strictly identical between frames,
gradual seasonal morph transition, snow accumulating on horizontal surfaces only
--no changed building, moved windows, different camera angle, melting architecture, inconsistent scale
```
> 换季只允许变**植被 / 地面覆盖 / 光的角度与色温**三项；建筑本体必须逐像素稳定。

### 例 4 · 毛坯转精装（Before–After）
```
[First frame] A bare concrete shell apartment: unfinished walls, exposed conduit, dusty screed floor, no fittings.
[Last frame] The same room fully finished: warm oak flooring, plastered white walls, integrated linear lighting,
a linen sofa and a low walnut coffee table, sheer curtains at the window.
Locked-off camera, identical framing, window position and room dimensions unchanged,
lighting shifts from flat overcast daylight to layered warm interior lighting with a soft daylight fill,
photoreal interior render, realistic material transitions, accurate ceiling height maintained
--no changed room shape, moved window, altered ceiling height, warped door frame, furniture clipping into walls
```
> 毛坯转精装最容易「顺手改户型」：必须写死 `window position and room dimensions unchanged`。

### 例 5 · 夜景光追设计
```
Exterior night view of a glass-and-steel office lobby seen from the plaza,
slow lateral slider move from left to right, 35mm, eye level, tripod-smooth,
ray-traced lighting: warm interior lighting spilling through the curtain wall onto wet paving,
crisp specular reflections of facade lights on the polished stone plaza, cool blue dusk sky as ambient,
clear glass with accurate reflections and transmission, brushed steel mullions, polished granite paving,
architectural visualization, cinematic dusk grading, balanced exposure between interior and exterior
--no over-exposed interior, muddy reflections, foggy glass, flickering lights, warped mullion grid
```
> 夜景的难点是**内外曝光平衡**；玻璃必须写 `accurate reflections and transmission`，否则会糊成黑板或白板。

---

## 01 场景主题（Scene & Theme）

### 子类型词库
- `architectural exterior visualization` — 建筑外观表现
- `interior design render` — 室内设计效果图
- `sketch to photoreal conversion` — 草图 / 手绘转写实
- `seasonal variation render` — 效果图换季节
- `bare shell to finished interior` — 毛坯转精装
- `floor plan to 3D scene` — 平面转实景
- `ray-traced lighting design` — 光追照明设计
- `urban masterplan flythrough` — 规划总平飞览
- `landscape and courtyard design` — 景观庭院
- `commercial space (retail / office / hospitality)` — 商业空间
- `renovation before-after morph` — 改造前后对比

### 空间类型 → 视角 / 光线 / 材质 速查表
| 空间类型 | 推荐视角 | 主光 | 招牌材质 |
|---|---|---|---|
| 住宅客厅 | `eye level 1.6m, 20–24mm` | `window daylight + warm downlight` | `oak floor, micro-cement, linen` |
| 卧室 | `eye level, 24mm corner view` | `soft morning light, sheer curtain diffusion` | `wool rug, matte plaster, warm wood` |
| 厨房 / 餐厅 | `eye level, 28mm` | `under-cabinet strip + daylight` | `stone countertop, matte lacquer, brass` |
| 办公 / 商业 | `35mm, slightly low` | `even ceiling lighting + curtain wall daylight` | `terrazzo, glass, brushed aluminium` |
| 建筑外观 | `drone 15–30m, 24mm` | `golden hour or overcast` | `board-formed concrete, glass curtain wall` |
| 夜景外观 | `plaza eye level, 35mm` | `interior spill + facade accent` | `wet paving, polished granite, steel` |
| 景观庭院 | `low 35mm, human scale` | `dappled tree light` | `gravel, timber deck, water surface` |

### 联动规则
- 空间类型决定**相机高度**：室内一律 `eye level 1.5–1.7m`，抬高即失真。
- 换季 / 改造类必须走**首尾帧**；单帧 T2V 无法保证建筑本体一致。

---

## 02 景别构图（Shot Size & Composition）

### 景别与构图词库
- `wide establishing exterior` — 建筑定场
- `corner two-point perspective` — 两点透视角部（外观最常用）
- `one-point perspective interior` — 一点透视室内（纵深感）
- `human-scale eye level view` — 人视点（客户最认这个）
- `detail shot of junction / material transition` — 节点 / 材质交接特写
- `aerial masterplan top-down` — 总平俯视
- `framed view through doorway` — 门洞框景
- `corrected verticals, no keystone` — 竖线校正（建筑摄影铁律）

### 设备 / 焦段词库
- `20mm ultra wide with corrected verticals` 室内超广（必配校正）
- `24mm` 外观 / 大空间 · `35mm` 自然建筑视角 · `50mm` 局部与节点
- `tilt-shift lens look` 移轴（专业建筑摄影签名）
- `drone orbit rig` 无人机环绕 · `motorised slider` 滑轨 · `steadicam walkthrough` 稳定器行进

### 构图 → 用途 速查表
| 用途 | 构图 | 焦段 | 关键约束 |
|---|---|---|---|
| 方案汇报封面 | `corner two-point perspective` | 24mm | `corrected verticals` |
| 空间尺度说明 | `one-point perspective interior` | 20–24mm | 必带人体尺度参照 |
| 材质说服 | `detail junction shot` | 50mm | 浅景深 + 真实纹理 |
| 客户带看 | `eye-level walkthrough` | 20mm | 稳定、匀速、无畸变 |
| 总平分析 | `aerial top-down` | 24mm 俯视 | 保持正交感 |
| 夜景形象 | `plaza eye level` | 35mm | 内外曝光平衡 |

### 联动规则
- **室内广角必须写 `corrected verticals, no keystone`**，否则墙体外扩、家具变形，专业度立刻归零。
- 尺度说服靠**参照物**：写 `human figure for scale` 或 `standard 750mm table height`，比写 "spacious" 有效得多。
- 移轴（`tilt-shift`）与鱼眼互斥，写移轴同时必须 negative `fisheye distortion`。

---

## 03 主体特征（Building & Space Attributes）

### 建筑形体词库
- `rectilinear massing with cantilevered upper floor` 方正体量 + 悬挑
- `stepped terraces with planted setbacks` 退台绿化
- `continuous horizontal window bands` 水平长窗
- `regular window grid, evenly spaced mullions` 规则窗格
- `pitched roof with clean eaves` 坡屋顶
- `double-height atrium with mezzanine` 挑空中庭 + 夹层

### 空间尺度词库（防"房间比例不合理"）
- `2.7m standard ceiling height` / `3.2m generous ceiling height` / `double-height 5.4m` — 层高
- `4m x 5m living area` — 开间进深
- `900mm circulation clearance` — 通道净宽
- `human figure for scale` — 人体尺度参照
- `standard door height 2100mm` — 门高基准
- `furniture proportioned to room size` — 家具与房间成比例

### 一致性锚点（I2V 必带）
- `keep the exact same massing and floor count` 体量与层数不变
- `window layout and mullion grid unchanged` 窗格不变
- `room dimensions and ceiling height unchanged` 房间尺寸与层高不变
- `reference image guided, structure locked` 参考图锁结构
- `only materials and lighting change` 只改材质与光（换季 / 精装用）

### 联动规则
- **凡是"改"的需求（换季 / 精装 / 改材质）都必须先写"不改什么"**，这是本类第一铁律。
- 层高一旦写死，家具尺寸必须同步（`furniture proportioned to room size`），否则出现巨型沙发。

---

## 04 材料配置（Material Palette · 选读）

- `board-formed concrete with visible tie holes` 木纹清水混凝土 · `fair-faced concrete, smooth` 光面清水
- `warm oak louvres` 暖橡木格栅 · `matte oak flooring with plank joints` 哑光橡木地板
- `micro-cement wall, seamless` 微水泥墙 · `lime plaster with subtle trowel marks` 石灰批荡
- `travertine slab with natural veining` 洞石 · `polished granite paving` 抛光花岗岩
- `glass curtain wall with clear reflections` 玻璃幕墙 · `brushed steel mullions` 拉丝钢竖梃
- `perforated metal screen` 穿孔金属板 · `corten steel with even patina` 耐候钢

### 联动规则
- 材质数量控制在 **4–6 种**：超过会互相打架且模型难以维持一致。
- 每种材质写**一个瑕疵特征**（`tie holes` / `natural veining` / `trowel marks`），这是写实与"渲染味"的分界线。

---

## 05 光影氛围（Lighting & Mood）

### 自然光词库
- `soft overcast daylight` — 阴天柔光：材质最忠实，方案汇报首选
- `late afternoon directional sunlight` — 午后斜射：立体感最强
- `golden hour warm rake light` — 黄金时刻掠射：形象照
- `blue hour dusk with interior spill` — 蓝调时刻：夜景形象照最佳窗口
- `high noon harsh sun with short shadows` — 正午硬光（慎用）
- `dappled light through tree canopy` — 树影斑驳（景观）
- `north-facing diffuse light` — 北向漫射（工作室感）

### 人工光词库
- `integrated linear cove lighting` 灯槽线性光 · `warm 3000K downlights` 暖筒灯
- `under-cabinet strip light` 橱下灯带 · `wall washer grazing the plaster` 洗墙掠射
- `pendant over dining table` 餐吊灯 · `facade accent uplight` 立面上射
- `practical lamps visible in frame` 画内实用光源（增真实感）

### 时段 × 情绪 × 曝光 速查表
| 时段 tag | 色温 | 情绪 | 曝光要点 |
|---|---|---|---|
| `morning daylight` | 5000K 偏冷 | 清爽、通透 | `no blown-out window` |
| `soft overcast` | 6000K 中性 | 客观、材质忠实 | 全局均匀，忌死黑 |
| `late afternoon` | 4000K 暖 | 温暖、生活 | 长影不可过硬 |
| `golden hour` | 3200K 强暖 | 形象、宣传 | 逆光需 `balanced exposure` |
| `blue hour dusk` | 外冷内暖 | 高端、都市 | 内外曝光比是成败关键 |
| `night with facade lighting` | 混合 | 商业、地标 | 忌过曝内透 |

### 联动规则
- **室内必带 `balanced exposure` + `no blown-out window`**：这是建筑视频最高频的翻车点。
- 蓝调时刻的公式：`cool ambient sky + warm interior spill + wet paving reflection`，三者缺一不成立。
- 多光源场景写 `layered lighting: ambient + task + accent`，否则模型会打成一片平光。

---

## 06 动作运动（Motion & Camera · 视频核心，最详尽）

### 6.1 静态级运动（空间"活"起来）
- `sunlight patch slowly creeping across the floor` — 光斑缓慢移动（最高级的建筑动态）
- `sheer curtain breathing in a light draught` — 纱帘轻拂
- `dust motes drifting in the light shaft` — 光柱浮尘
- `water surface gently rippling` — 水面微波
- `tree canopy swaying slightly, dappled shadows shifting` — 树影晃动
- `steam rising from a cup on the table` — 桌上热气（生活气息）

### 6.2 动态级运动（环境与人）
- `a person walking through the space at natural pace` — 人穿过空间（尺度参照 + 生命感）
- `sliding door opening smoothly` — 推拉门开启
- `elevator doors parting in the lobby` — 电梯门开
- `passing cars leaving light trails on the plaza` — 车流光轨（夜景）
- `snow accumulating on horizontal surfaces` — 积雪堆积（换季）
- `foliage transitioning from green to autumn gold` — 植被换季

### 6.3 镜头运动（Camera Move）
- `slow drone arc at constant radius` — 无人机等半径环绕（外观标配）
- `drone crane-up reveal over the roofline` — 升起揭示
- `steadicam walkthrough at constant pace` — 稳定器行进（室内标配）
- `lateral slider left to right` — 横向滑轨
- `slow push-in through a doorway` — 穿门推进
- `locked-off static` — 锁死机位（换季 / 前后对比必用）
- `tilt-up along the facade` — 沿立面上摇

### 6.4 招牌运动（Signature Moves）
- `drone orbit + crane-up combo` — 环绕接升起，建筑形象片万能开场
- `one-shot interior walkthrough (oner)` — 室内一镜到底，客户带看首选
- `threshold traversal: pass through a doorway into the next space` — 穿门过渡，串联户型
- `time-lapse day-to-night on a locked-off frame` — 定机位日夜变化
- `before-after morph with locked camera` — 定机位前后对比溶解
- `reveal by curtain opening / light switching on` — 遮挡揭示

### 6.5 「改造 / 换季」首尾帧工作法
| 步骤 | 要点 | 关键 tag |
|---|---|---|
| 1 锁机位 | 首尾帧完全同框、同焦段 | `locked-off camera, identical framing` |
| 2 声明不变量 | 体量 / 窗位 / 层高 / 房间尺寸 | `geometry and dimensions unchanged` |
| 3 只列变量 | 换季 = 植被+地面+光；精装 = 材质+家具+灯 | `only materials and lighting change` |
| 4 写过渡 | 描述状态变化，不描述镜头变化 | `gradual morph transition` |
| 5 校验 | 叠帧比对窗格与墙线 | negative 补 `moved window, changed room shape` |

### 6.6 运动速度 → 稳定性 速查表
| 场景 | 速度 tag | 稳定性 | 常见翻车 |
|---|---|---|---|
| 室内行进 | `constant walking pace` | `steadicam smoothness` | 加速漂移、墙体扭曲 |
| 无人机环绕 | `slow constant angular speed` | `constant radius` | 半径变化导致建筑变形 |
| 滑轨横移 | `steady lateral move` | `tripod-smooth` | 视差错乱、幕墙抖动 |
| 光影时间流逝 | `slow sun arc over the scene` | `locked-off` | 阴影跳变而非渐变 |
| 前后对比 | `no camera move` | `absolutely locked` | 机位偏移 = 对比失效 |

### 联动规则
- **建筑视频宁慢勿快**：镜头越快，几何越容易融化；`slow` 是本类默认修饰。
- 环绕必须写 `constant radius`，否则模型会边转边推，建筑透视持续变形。
- 一镜到底（oner）时长受模型限制：超过单条上限就拆成"穿门过渡"多镜，接口放在门洞处最隐蔽。

---

## 07 人物与生活痕迹（Staging · 选读）

- `a single person for scale, walking away from camera` 背向行人（不抢主体又给尺度）
- `seated figure reading by the window` 窗边阅读
- `subtle signs of life: an open book, a used cup, folded throw` 生活痕迹
- `no faces visible, figures softly motion-blurred` 面部不可见 + 轻微运动模糊（规避人脸崩坏）

### 联动规则
- 建筑片里**人是尺度工具不是主角**：一律写 `no faces visible, motion-blurred figures`，既真实又规避人脸风险。
- 生活痕迹控制在 3 处以内，多了变成杂乱。

---

## 08 风格滤镜（Art Direction & Render Style）

### 渲染风格词库
- `photoreal architectural visualization` — 写实建筑表现（主路线）
- `Twinmotion-grade realism` / `Unreal Engine 5 archviz` — 实时引擎级
- `Corona / V-Ray offline render look` — 离线渲染器质感（更柔更真）
- `editorial architectural photography look` — 建筑摄影杂志感
- `soft Nordic minimal interior` — 北欧极简
- `warm Japandi interior` — 日式侘寂 × 北欧
- `industrial loft aesthetic` — 工业 loft
- `conceptual white model render` — 白模概念（方案阶段）
- `hand-drawn sketch overlay hybrid` — 手绘叠加（草图阶段）

### 镜头 / 摄影质感
- `tilt-shift architectural photography` 移轴 · `corrected verticals` 竖线校正
- `neutral colour grading, accurate white balance` 中性调色（材质不失真）
- `subtle film grain` 轻颗粒（削弱"渲染味"）
- `high dynamic range with recovered highlights` HDR 高光保留
- `crisp micro-contrast, no oversharpening` 微反差锐利但不过锐

### 参考锚点
| 锚点 tag | 视觉签名 | 适用类型 |
|---|---|---|
| `Tadao Ando concrete light` | 安藤忠雄：清水混凝土 + 一束光 | 文化 / 极简建筑 |
| `Peter Zumthor material atmosphere` | 卒姆托：材质与氛围优先 | 小体量 / 精品 |
| `Kengo Kuma timber lattice` | 隈研吾：木格栅、消隐 | 日式 / 文旅 |
| `Iwan Baan documentary archphoto` | 建筑纪实摄影：有人、有天气 | 落成实景 |
| `MIR / Brick Visual archviz` | 顶级效果图：氛围优先于炫技 | 竞赛表现 |
| `Kinfolk interior editorial` | 低饱和、静物、自然光 | 室内软装 |
| `Nordic minimal white oak` | 白 + 橡木 + 大量漫射光 | 住宅 |

### 联动规则
- 走**方案汇报**用 `soft overcast + neutral grading`（材质忠实）；走**宣传形象**用 `golden hour + cinematic grading`。两者不要混。
- 白模（`conceptual white model`）必须 negative 掉 `photoreal materials`，否则会被自动上材质。

---

## 09 材质细节（Materials & Realism · 选读）

- `clear glass with accurate reflections and transmission` 通透玻璃（反射 + 透射同时成立）
- `low-iron glass, minimal green tint` 超白玻璃 · `frosted glass with soft diffusion` 磨砂玻璃
- `concrete with subtle formwork imperfections` 混凝土模板痕 · `weathered surface with rain streaks` 雨痕风化
- `matte plaster with slight surface irregularity` 哑光批荡微起伏
- `timber with visible grain and joint lines` 木纹与拼缝 · `stone with natural veining, book-matched` 石材对纹
- `wet paving with specular reflection` 湿地面镜面反射
- `fabric with natural drape and thickness` 织物垂坠与厚度

### 「玻璃不糊」专项规则
| 症状 | 原因 | 修法 |
|---|---|---|
| 玻璃变黑板 | 没交代反射内容 | 写 `reflecting the sky and neighbouring trees` |
| 玻璃变白板 | 过曝 + 无透射 | 加 `accurate transmission, balanced exposure` |
| 反射像脏雾 | 缺 `clear` 限定 | 写 `clear reflections, clean glass, no haze` |
| 幕墙格子扭曲 | 几何未锁 | 加 `regular mullion grid unchanged` + negative `warped mullion` |
| 夜景内透过曝 | 内外曝光比失衡 | 写 `balanced interior-exterior exposure` |

### 联动规则
- 反射材质（玻璃 / 湿地 / 抛光石材）必须**指明反射的对象**，否则模型填灰。
- 每种材质配一个瑕疵（雨痕 / 模板痕 / 拼缝），是摆脱"塑料渲染味"的最有效手段。

---

## 10 后期特效（Post & Compositing · 选读）

- `subtle lens flare from the setting sun` 落日炫光（克制）
- `atmospheric haze for depth layering` 大气透视分层（远景必备）
- `light trails from passing cars` 车流光轨（夜景）
- `volumetric god rays through the atrium` 中庭体积光
- `gentle bloom on interior light sources` 灯具柔光晕
- `before-after wipe transition` 前后对比划擦
- `season morph cross-dissolve` 换季溶解

### 联动规则
- `atmospheric haze` 是建筑远景**看起来有距离**的关键，缺了会像贴图拼贴。
- 体积光只在有介质时成立：写 god rays 必须同时写 `dust / haze in the air`。

---

## 11 道具场景（Set Dressing & Context · 选读）

- `mature street trees with realistic canopy density` 成熟行道树 · `low planting beds along the facade` 立面绿篱
- `parked cars scaled correctly to the building` 尺度正确的停放车辆
- `context buildings blurred in the background` 虚化的周边建筑
- `sheer curtains, wool rug, ceramic vase` 室内软装三件套
- `books and a throw on the sofa` 沙发上的书与毯（生活感）
- `outdoor timber deck with furniture` 户外木平台家具

### 联动规则
- 周边环境（context）必须写 `scaled correctly` 或 `blurred in the background`，否则出现巨人树、玩具车。
- 室内软装 3–5 件即可；堆满会挤压空间感并引发穿模。

---

## 12 负向规则（Negative Prompt & Forbidden Combos）

### 通用 negative 词库
- `melting geometry, warped architecture, bending walls` — 几何融化（本类头号翻车）
- `distorted perspective, tilted verticals, keystone effect` — 透视 / 竖线歪斜
- `fisheye distortion, barrel distortion` — 广角桶形畸变
- `impossible room proportions, wrong ceiling height` — 比例失真
- `floating furniture, furniture clipping into walls` — 家具悬浮 / 穿模
- `blown-out windows, over-exposed interior, crushed blacks` — 曝光失控
- `muddy reflections, foggy glass, black glass` — 玻璃糊
- `garbled signage, gibberish text, unreadable dimensions` — 文字标注乱码
- `extra buildings, duplicated windows, changed floor count` — 结构被重设计
- `flickering lights, inconsistent shadow direction` — 光照跳变

### 子类型专用 negative
| 子类型 | 必须排除 | 原因 |
|---|---|---|
| 草图转写实 | `changed floor count, redesigned facade, extra buildings` | 模型最爱"顺手重设计" |
| 室内 walkthrough | `fisheye distortion, tilted verticals, blown-out windows` | 广角三大病 |
| 换季 | `changed building, moved windows, different camera angle` | 只准变季节 |
| 毛坯转精装 | `changed room shape, altered ceiling height, moved door` | 只准变饰面与家具 |
| 夜景光追 | `over-exposed interior, flickering lights, muddy reflections` | 曝光与反射 |
| 总平飞览 | `inconsistent scale, toy-like buildings` | 尺度一致性 |

### 禁止组合表（Forbidden Combos）
| 冲突组合 | 后果 | 正确做法 |
|---|---|---|
| `ultra wide 20mm` + 无 `corrected verticals` | 墙线外扩、鱼眼感 | 广角必配竖线校正 |
| `fast camera move` + `complex facade` | 立面栅格融化 | 建筑一律 slow |
| `drone orbit` 无 `constant radius` | 边转边推、透视持续变形 | 显式写等半径 |
| 改造 / 换季 + 任意运镜 | 首尾帧无法对齐 | 必须 `locked-off` |
| 改需求 + 未声明不变量 | 建筑被重设计 | 先写"保持不变的量" |
| `ray tracing` + `conceptual white model` | 白模被上材质 | 白模需 negative 掉写实材质 |
| `volumetric god rays` 无介质描述 | 光柱悬空不自然 | 同时写 `haze / dust in the air` |
| 室内 + 无 `balanced exposure` | 窗口死白 | 必写曝光平衡 |
| 玻璃 + 无反射内容 | 黑板 / 白板玻璃 | 指明反射的天空与树木 |
| 家具堆满 + 小空间 | 穿模与比例崩 | 软装 3–5 件，写 `proportioned to room size` |

### 冲突避免总则
- 本类负向的核心是**几何可信度**：形变类、透视类、比例类三组必须常驻。
- 任何"修改现状"的需求，负向里都要显式禁止修改建筑本体。

---

## 13 推荐模型（Model Mapping · 见 models-模型能力矩阵.md）

| 需求 | 主推 | 备选 | 为何契合 |
|---|---|---|---|
| **草图 / 效果图转写实（I2V）** | **Wan 2.7** | Luma Ray 3 | I2V 最强 + 首尾帧，思考模式先规划再生成，对"保持结构"这类多约束指令遵循度高；开源可自部署批量跑图纸 |
| **换季 / 毛坯转精装（首尾帧）** | **Wan 2.7** | Vidu Q3 | 首尾帧锁死机位与几何，只让状态变化；Vidu Q3 多输入架构可同时喂参考图 + 首尾帧 |
| **建筑形象大片 / 无人机环绕** | **Veo 3.1** | Sora 2 / Kling O03 | Veo 电影级写实、光影景深与调色最接近实拍航拍素材 |
| **室内一镜到底 walkthrough** | **Sora 2** | Veo 3.1 | 时序连贯与空间物理最强，最长 20s，适合长走位不崩 |
| **极致保真 / 夜景反射** | **Kling 3.0 / O03** | Veo 3.1 | O03 复杂场景（多光源、反射、大气）连贯性 2026 顶级 |
| **批量方案比选** | **Seedance 2.0** | — | Fast 档极便宜、提示遵循高，先出 10 版角度再挑终稿 |
| **快速产品级 I2V 短镜** | **Luma Ray 3** | Seedance 2.0 | 输出干净无伪影，5s 空间小镜很稳 |
| **精确运镜（滑轨 / 定速环绕）** | **Runway Gen-4** | — | 运镜控制行业最佳，可精确执行等半径环绕与横移 |
| **高分辨率交付 / 大屏** | **LTX 2.3** | — | 开源 4K、20s、可自部署，适合展厅与数字标牌 |

### 工作流建议
1. **概念阶段**：草图 / 白模 → Seedance 2.0 批量探角度与氛围。
2. **深化阶段**：定稿效果图 → **Wan 2.7 I2V 锁结构**出主镜；换季 / 改造走首尾帧。
3. **形象片**：关键镜用 Veo 3.1 / Sora 2 / Kling O03 提级，无人机环绕 + 室内 oner 各出一条。
4. **交付**：文字标注、尺寸、图例一律后期加（模型内文字必乱）；需要屏内文字时才用 Wan 2.7。

---

## 14 组装公式（Assembly Formula）

### 槽位顺序
```
[01 空间类型 + 项目定位]
+ [02 视角 + 焦段 + corrected verticals + 构图]
+ [03 形体 / 尺度参数 + 一致性锚点（改造类先写"不变量"）]
+ [05 自然光 + 人工光分层 + 时段色温 + balanced exposure]
+ [06 单一主镜头运动（slow）+ 环境微动]
+ [08 渲染风格 + 参考锚点 + 中性调色]
+ (选读 3–5: 04 材料配置 / 07 人物尺度 / 09 材质细节 / 10 后期 / 11 环境道具)
+ [12 negative 段（必含形变 + 透视 + 比例三组）]
→ 模型选择见 [13]
```

### 必选 / 选读
- **必选**：01 / 02 / 03 / 05 / 06 / 08 / 12 / 13 / 14
- **选读（每条取 3–5）**：04 材料 / 07 人物 / 09 材质 / 10 后期 / 11 道具
- **建筑额外强制**：凡涉及既有图纸 / 效果图的改动，**必须 I2V + 首尾帧**，且 03 中显式声明不变量。

### 最小可用示例
```
Interior render of a 3.0-metre-high Nordic minimal living room, human figure for scale,
one-point perspective, 24mm with corrected verticals, eye level 1.6m, slow push-in, steadicam smoothness,
room dimensions and window position unchanged, furniture proportioned to room size,
soft overcast daylight through floor-to-ceiling windows plus warm 3000K cove lighting,
balanced exposure, no blown-out window,
matte oak flooring with plank joints, micro-cement wall, linen sofa with natural drape,
photoreal architectural visualization, neutral colour grading, subtle film grain,
sunlight patch slowly creeping across the floor
--no fisheye distortion, tilted verticals, blown-out windows, floating furniture, melting geometry, garbled text
```

### 交付前检查清单
1. 是否写了 `corrected verticals`？2. 室内是否写了 `balanced exposure / no blown-out window`？
3. 改造类是否先声明"不变量"？4. 首尾帧是否 `locked-off` 且只变一个维度？
5. 环绕是否写 `constant radius`？6. 玻璃是否指明反射内容？
7. 尺度参照（人 / 门高 / 层高）是否给了？8. negative 是否含形变 / 透视 / 比例三组？
