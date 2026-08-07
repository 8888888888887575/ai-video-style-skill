# 决策映射（Decision Matrix）

> 本文件是 skill 的「决策层」。输入一份创意简报（或目标风格名），agent 按下列流程输出：
> **① 识别风格 → ② 选模型（含理由与备选）→ ③ 套用提示词模板 → ④ 给出中文说明与避坑提示。**
> 所有结论的论据来自 `styles.md`（索引）与各风格独立文件 `references/styles/NN-xxx.md`（风格特征，15 模块深度）与 `models.md`（模型能力）。
> **跨风格技法层**（非风格，各风格文件按需引用）：`cinematography.md`（运镜/灯光大词库）、`sound-design.md`（声音桥/音画同步）、`continuation.md`（续拍/分镜串联/长剧情拆分）、`style-combos.md`（导演签名/风格组合）、`timestamp-storyboard.md`（秒级分镜法）、`creativity-gate.md`（创意四关）、`emotion-shot.md`（情绪/微表情）。

---

## 决策流程（Decision Flow）

```
收到简报
  │
  ├─ 用户直接给了风格名？ ──是──▶ 跳到「风格→模型」表
  │
  └─ 否，只有内容描述？ ──▶ 从描述中提取信号：
       是否有「卡通/动漫/二次元/插画/MV/卡点」→ 偏 PV / 手绘 / 动漫
       是否有「3D/渲染/产品/科幻/真实光照」→ 偏 CG
       是否有「Logo/文字/数据/图表/信息图/片头」→ 偏 MG
       是否有「手绘/水彩/逐帧/铅笔」→ 偏 手绘 2D
       是否有「写实/真人/电影感/广告」→ 偏 写实/真人
       是否有「像素/复古游戏/8-bit」→ 偏 像素
       是否有「漫剧/短剧/番剧/仙侠/玄幻/国风/角色连续/多镜头叙事」→ 偏 AI 漫剧
       是否有「商业/电商/产品/品牌TVC/珠宝/汽车/模特换装」→ 偏 商业/电商
       是否有「建筑/室内/装修/效果图/草图转写实」→ 偏 建筑/室内
       是否有「写真/人像/厚涂/婚纱/萌宠/打光流派」→ 偏 写真/人像
       是否有「字体/字幕/标题/歌词动画」→ 偏 字体动画
       是否有「成人/性感写真/NSFW/亚洲写真/JAV 风格」→ 偏 NSFW/亚洲成人（见 styles/09-nsfw-asian.md）
       是否有「二创/整活/换脸/名场面复刻/鬼畜/卡点/跨IP联动/梗图/表情包/风格迁移」→ 偏 二创整活（见 styles/10-fanwork.md，参考图锁身份）
  │
  ▼
按「风格→模型」表给出 主推 + 2 个备选（含音频/时长/预算约束）
  │
  ▼
套用 prompt-templates.md 对应模板，填入简报具体要素
  │
  ▼
附中文说明：为什么选这个模型、常见翻车点、是否需参考图/首尾帧/音频
```

---

## 风格 → 模型 → 模板 映射表

| 目标风格 | 主推模型 | 备选 1 | 备选 2 | 模块化风格文件 | 关键约束 |
|---|---|---|---|---|---|
| **PV / 动漫 MV** | MiniMax H3 | Vidu Q3 | Kling 3.0 / PixVerse v5.6 | [styles/01-pv.md](styles/01-pv.md) | 要卡点→需原生音频模型；锁脸用首尾帧 |
| **CG 写实 3D** | Veo 3.1 | Sora 2 | Seedance 2.0 / Kling O03 | [styles/02-cg.md](styles/02-cg.md) | 明确 `3D rendered not footage`；避 `melting` |
| **MG 动态图形** | **Animora/MotionVid** | Runway Gen-4 | Pika 2.0 / Wan 2.7(文字) | [styles/03-mg.md](styles/03-mg.md) | **勿用 Veo/Sora**；屏内文字用 Wan |
| **手绘 2D** | MiniMax H3 | Vidu Q3 | Kling 3.0 / PixVerse v5.6 | [styles/04-handdrawn.md](styles/04-handdrawn.md) | 排除 `3D render/CGI`；控 `boiling line` |
| **AI 漫剧 / 叙事** | Wan 2.7 | Seedance 2.0 | Vidu Q3 / Kling 3.0 | [styles/05-ai-drama.md](styles/05-ai-drama.md) | **跨镜头一致第一**：参考图/首尾帧/角色锁定；拆 shot list |
| **商业/电商/产品** | Wan 2.7 | Seedance 2.0 | Kling 3.0/O03 / Luma Ray 3 | [styles/06-commercial.md](styles/06-commercial.md) | 真实材质 `no plastic`；文字/LOGO 用 Wan 或后期；换装 I2V+首尾帧 |
| **建筑/室内渲染** | Veo 3.1 | Sora 2 / Seedance 2.0 | Wan 2.7 / Luma Ray 3 | [styles/07-architecture.md](styles/07-architecture.md) | 参考图/草图 I2V 锁结构比例；玻璃 `clear reflections` |
| **写真/人像摄影** | Veo 3.1 | Kling 3.0 / Seedance 2.0 | MiniMax H3(厚涂) / Vidu Q3 | [styles/08-portrait.md](styles/08-portrait.md) | 锁脸参考图+首尾帧；厚涂必须排 `photorealistic` |
| **NSFW / 亚洲成人** | Veo 3.1 / Sora 2 | Kling 3.0 / Seedance 2.0 | MiniMax H3 / Vidu Q3 / PixVerse | [styles/09-nsfw-asian.md](styles/09-nsfw-asian.md) | I2V+首尾帧锁人物；运行于闭源平台（平台自带审查）；逐词模板见上游仓库 |
| **二创整活 / 换脸 / 复刻** | Wan 2.7(I2V+首尾帧) | Kling 3.0 / Seedance 2.0 | MiniMax H3(鬼畜) / PixVerse(loop) / Vidu Q3 | [styles/10-fanwork.md](styles/10-fanwork.md) | **身份一致第一**：换脸/复刻/联动/迁移必用参考图+首尾帧锁身份；鬼畜 loop 首尾帧一致 |
| **数字人/口播** | HeyGen / Hedra | HappyHorse 1.1(动漫口型) | Synthesia | （专用工具，非 T2V） | 与通用 T2V 不同类 |

> 注：跨风格速查模板仍见 `prompt-templates.md`（A–I 九类英文模板速查）；每个风格文件的 §00 范例 + §14 组装公式为该风格的权威完整版。

---

## 常见约束的快速分支（Quick Branches）

### Q1：需要原生音频（对白/音乐/环境音）？
- 要 → Veo 3.1(最佳同步) / Kling 3.0 / Vidu Q3 / MiniMax H3 / Wan 2.7 / HappyHorse 1.1
- 不要 / 后期配 → 其余均可，Sora 2 无音频但叙事强

### Q2：时长需求？
- ≤8s 电影感 → Veo 3.1 / Seedance
- 10s → Kling 3.0 / Sora 2 / MiniMax H3
- 12–20s 长片 → Sora 2(至20s) / Vidu Q3(16s) / Wan 2.7(15s) / LTX 2.3(20s)
- 竖屏社媒短讯 → PixVerse v6 / HappyHorse / Luma

### Q3：预算 / 批量？
- 极低成本批量 → Seedance 2.0 Fast($0.022/s) / Wan 开源免费 / MiniMax H3 廉价档
- 不计成本要保真 → Kling O03 / Veo 3.1 / Sora 2

### Q4：要精确控制（运镜/某区域运动/首尾帧）？
- 运镜 & 运动笔刷 → Runway Gen-4
- 首尾帧锁产品落帧 → Wan 2.7 / Vidu Q3
- 屏内可读文字 → Wan 2.7

### Q5：自托管 / 隐私 / 可控？
- 开源自部署 → Wan 2.7 / LTX 2.3（需强 GPU）

### Q6：风格是 MG / 动态图形？
- **直接走 Animora/MotionVid**，不要用电影级写实模型硬做（它们此维度弱）。

### Q7：是 AI 漫剧 / 跨镜头叙事 / 角色连续？
- **一致性优先**：Wan 2.7（首尾帧/思考模式）、Vidu Q3（首尾帧/多输入）、Seedance 2.0、Kling 3.0 都支持。先建「角色表 + 场景表」作固定参考，拆 shot list 逐镜生成再剪辑。画面电影感可叠加 Veo 3.1 / Sora 2。
- **CG 漫剧 vs 2D 漫剧**：先问「要 3D 感还是纯 2D 感」——CG 漫剧走 Veo/Sora/Seedance/Kling/Wan（cel shaded 3D）；2D 漫剧走 MiniMax H3/Vidu/PixVerse。用错 → 风格被洗。

### Q8：是商业 / 电商 / 产品 / 品牌 TVC？
- 产品材质真实 + 干净打光优先 → Wan 2.7（首尾帧锁产品落帧 + 屏内文字）、Seedance 2.0（批量）、Kling O03（保真）、Luma Ray 3（产品干净）。
- 汽车 / 大片级 → Veo 3.1 / Sora 2 / Kling O03。模特换装用 I2V + 首尾帧锁姿态。

### Q9：是建筑 / 室内 / 写真 / 人像？
- 建筑渲染 → Veo/Sora/Seedance/Kling（写实）+ Wan/Luma（草图 I2V 锁结构，见 styles/07-architecture.md）。
- 写真人像 → Veo/Kling/Seedance（写实，见 styles/08-portrait.md）；厚涂/插画走 MiniMax H3/Vidu/Wan，且必须排 `photorealistic`。

### Q10：是 NSFW / 亚洲成人 / 性感写真？
- **模块对齐**：直接走 `styles/09-nsfw-asian.md`，其结构严格对齐 [`ShuaiHui/nsfw-prompt-templates-asian`](https://github.com/ShuaiHui/nsfw-prompt-templates-asian) 的 15 模块分类法（场景/景别/裸露液体/服装/光影/姿势/表情/胶片/妆容/发型/瑕疵/纹身/道具/人格卡）。
- **技术路径**：以 I2V（图生视频）+ 首尾帧 + 参考图锁人物为主，纯 T2V 对成人姿态与人物锁定极不稳定。
- **运行环境**：用户实际在闭源平台（Sora 2 / Veo 3.1 / Kling 3.0 / Seedance 2.0 / MiniMax H3 / Vidu Q3 / PixVerse / Runway）生成，平台自带内容审查，无需在本 skill 层做额外审核。

### Q11：时长 >10s / 卡点 / 多动作 / 续拍？
- **>10s 或多动作**：用 `timestamp-storyboard.md` 秒级分镜法（每段标 画面+镜头+音效），不要写一段模糊长 prompt。
- **卡点视频**：必须在分镜标节拍秒数（如 `Bass Drop @ 0:08`），原生音频模型（Kling/MiniMax H3/Veo/Seedance）直接写声场。
- **跨镜/续拍/漫剧**：见 `continuation.md` — 长剧情 >30s 必拆，用参考图+首尾帧+角色表锁一致，或 Seedance `return-last-frame` 视频接龙。

### Q12：要声音 / 对白 / 配乐 / 音画同步？
- 原生音频模型（Veo 3.1 / Kling 3.0 / MiniMax H3 / Seedance 2.0 / Sora 2）可直接在 prompt 写声场、对白、音效。
- 用 `sound-design.md` 的 J-cut/L-cut 串情绪、整体声场统一多镜头；至少给 `ambient bed` 避免无声空洞。
- 无原生音频的模型：prompt 只管画面，声音交后期（HeyGen/Hedra/剪辑）。

### Q13：要电影感 / 强美术方向 / 对抗平庸？
- **美术锚定**：用 `style-combos.md` 的导演签名（胡金铨/王家卫/张艺谋/诺兰…）或 27 视觉风格定基底，比泛写"中国风/科幻"命中率高。
- **创意闸门**：出提示词前过 `creativity-gate.md` 四关（记忆点/意外感/情绪弧线/叙事变化），平庸则迭代。
  - **情绪戏**：按 `emotion-shot.md` 做景别递进（MCU→ECU）与微表情，对话戏给听者二级表演。

### Q14：要上传图/视频/音频做多模态参考，或要精准编辑/替换？
- **多模态参考驱动**：**MiniMax H3** 是此类需求首选——支持图(≤9)/视频(≤3)/音频(≤3)自由组合（混合≤12 文件），用 `@图片1/@视频1/@音频1` 在提示词标注每个素材用途（人物参考锁脸 / 动作参考 / 场景参考 / 音色参考 / 风格参考 / 视频编辑…）。
- **精准编辑**：替换角色/物体、改背景/光影、换台词/音色、局部修改保持其余不变 → H3 高精度指令遵循强，直接给参考图/视频 + 修改指令。
- **提示词范式（H3 专属三段式）**：`参考素材说明 + 核心创意 + 画面过程说明`；台词长短对齐镜头、需出现的文字/Logo 写出原文、跨 shot 的 J-cut/L-cut 明确写出即可响应。速查见 `prompt-templates.md 模板 K`；**完整 @标注分类 / 镜头拆分铁律 / 真实示例 → `references/h3-prompt-cookbook.md`**。
- 其它强多模态/编辑模型：Vidu Q3（首尾帧+多输入）、Wan 2.7（首尾帧+思考模式）、Kling 3.0/O03（人体运动+I2V）。

---

## 输出格式约定（Agent Output Schema）

当 agent 使用本 skill 时，最终回复建议按此结构：

```
【识别风格】<风格名> — <一句话理由>
【推荐模型】主推：<模型> ｜ 备选：<模型1>, <模型2>
【选型理由】<2–3 句，引用 models.md 的强项/约束>
【英文提示词】
  <按模板填好的完整 prompt>
【中文说明】<风格要点 + 避坑 + 是否需参考图/首尾帧/音频>
【负向词】<针对性负向词>
```

---

## 反模式提醒（Anti-patterns）

- ❌ 用 Veo/Sora 硬做 MG → 应用 Animora/Runway。
- ❌ 做手绘却没排除 `3D render/CGI` → 会被洗成 3D anime。
- ❌ 做 PV 卡点却选无音频模型且不做后期对轨 → 卡不住拍。
- ❌ 写实长片用 8s 模型硬拼 → 一致性崩；用 Sora2/Vidu/Wan 长片档。
- ❌ 纯文本不附参考图 → 一致性/风格命中率显著下降，尽量 I2V/首尾帧。
- ❌ 做 AI 漫剧却只用单条 T2V 不锁角色 → 跨镜脸/服装漂移；必须用参考图+首尾帧+角色表。
- ❌ 把 AI 漫剧当单条风格短片做 → 应拆 shot list 逐镜生成再剪辑拼接。
- ❌ 做商业产品却没强调真实材质 → 出塑料感；必须 `real material, accurate reflection, no plastic`。
- ❌ 建筑渲染不锁结构比例 → 比例错乱；用参考图/草图 I2V。
- ❌ 写真厚涂却没排 `photorealistic` → 被洗成写实人像；明确 `painterly, impasto`。
- ❌ 字体动画用纯 T2V 又要求可读文字 → 乱码；用 Wan 2.7 屏内文字或后期 AE/PR。
- ❌ NSFW 生成中混入未成年相关描述 → 触碰红线；任何 prompt 永久排除 `minor / underage / child / loli` 等词（其余尺度由闭源平台自身审查处理）。
- ❌ 二创整活不锁身份（换脸没参考图 / 复刻没原镜截图 / 联动没角色图）→ 出陌生人、构图漂、梗失效；必须参考图 + 首尾帧。
- ❌ >10s / 卡点却写一段模糊长 prompt → 必漂/错位；用 `timestamp-storyboard.md` 秒级分镜（画面+镜头+音效）。
- ❌ 卡点视频不标节拍秒数 → 画面与音乐错位；原生音频模型直接写声场。
- ❌ 长片一条硬撑 >30s → 一致性崩；按 `continuation.md` 拆分 + 拼接。
- ❌ 声音完全不提 → 画面"无声感"空洞；至少给 `ambient bed`，可用 J-cut/L-cut 串情绪（见 `sound-design.md`）。
- ❌ 美术方向只写"中国风/科幻" → 命中率低；用 `style-combos.md` 导演签名锚定。
- ❌ 输出"安全但无聊"的提示词 → 过 `creativity-gate.md` 四关对抗平庸。
