# 示例简报与期望输出（Examples）

> 用途：验证 skill 的决策与模板是否可用。每个示例给出「用户简报 → 期望的 agent 输出」。
> 对照 `decision-matrix.md`、`prompt-templates.md` 与 `references/styles/NN-xxx.md` 检查一致性。

---

## 示例 1 — 动漫音乐 PV

**用户简报**：「帮我做一个虚拟歌姬的动漫 PV，要卡点、舞台霓虹光、头发飘动，带音乐。」

```
【识别风格】PV / 动漫 MV — 关键词：虚拟歌姬、卡点、舞台、头发飘动
【推荐模型】主推：MiniMax H3 ｜ 备选：Vidu Q3, Kling 3.0
【选型理由】MiniMax H3 是动漫/风格化专精、输出有手绘动画感；卡点需音频→MiniMax H3/Kling 3.0/Vidu Q3 支持原生音频；锁脸用首尾帧或参考图。
【英文提示词】
Close-up to wide shot transition, a silver-haired virtual singer in glowing stage costume,
executing a dynamic spin with hair and ribbons fluttering, beat-synced camera cuts every 2 beats,
neon-lit concert stage with volumetric haze and crowd silhouettes,
rim light in cyan and magenta, additive glow, chromatic aberration on impact frames,
anime PV, cel shading, vibrant color grading, 2.5D parallax background, speed lines,
motion blur on fast moves, snap zoom, impact shake.
【中文说明】卡点靠音频驱动，建议用支持原生音频的模型并后期对轨；用 rim light cyan/magenta + additive glow 锚定 anime 打光；务必排除 photorealistic/3D render 防被洗成写实；锁角色一致性用参考图+首尾帧。
【负向词】blurry, deformed face, extra limbs, static camera, photorealistic, 3D render
```

---

## 示例 2 — 产品 3D 展示

**用户简报**：「做一个科幻要塞的 3D 写实展示，无人机环绕拉升，电影感。」

```
【识别风格】CG 写实 3D — 关键词：3D、写实、科幻要塞、无人机环绕、电影感
【推荐模型】主推：Veo 3.1 ｜ 备选：Sora 2, Seedance 2.0
【选型理由】Veo 3.1 电影级写实+光影/景深最佳；Sora 2 叙事/长镜头强；Seedance 物理与性价比好。需明确"3D rendered not footage"防止被当实拍。
【英文提示词】
Cinematic establishing shot, slow aerial drone pull-up, a massive sci-fi fortress rendered in 3D,
energy shields ripple across the surface, secondary motion on antennae and banners,
orbiting asteroids, volumetric god rays through dust,
global illumination, ray-traced reflections on metal, depth of field, HDR environment,
3D rendered, PBR materials, Unreal Engine 5 cinematic style, clean topology,
subtle film grain, lens flare.
【中文说明】明确写 3D rendered not real footage；clean topology, no melting 规避几何融化；写实 CG 优先 Veo/Sora，要精确运镜可换 Runway Gen-4。
【负向词】melting geometry, broken topology, 2D, hand-drawn, noisy, low poly artifacts
```

---

## 示例 3 — Logo 动态图形

**用户简报**：「做个科技公司的 logo 动效，等距视角，文字弹入，品牌蓝红。」

```
【识别风格】MG / 动态图形 — 关键词：logo 动效、等距、文字弹入、品牌色
【推荐模型】主推：Animora / MotionVid ｜ 备选：Runway Gen-4, Pika 2.0
【选型理由】MG 是 Animora 的专精赛道，电影级模型(Veo/Sora)在此反而弱；要屏内可读文字用 Wan 2.7。Runway 提供运动笔刷精控。
【英文提示词】
Isometric camera push-in, a clean vector logo assembling from scattered particles and lines,
kinetic typography pops in word by word with overshoot easing, data bars grow to full,
gradient background with subtle grid pattern and floating geometric shapes,
flat design, neon glow accents, glassmorphism panels,
motion graphics, after effects style, brand color palette (#0A84FF / #FF375F), loopable,
clean morph transitions, no film grain.
【中文说明】MG 不要交给 Veo/Sora；强调 clean vector shapes, flat design, no noise；需要屏内可读文字用 Wan 2.7（支持 12 国语言）。
【负向词】photorealistic, noisy texture, messy lines, illegible text, 3D render, live action
```

---

## 示例 4 — 手绘水彩动画

**用户简报**：「一只小狐狸水彩手绘动画，森林里跑，要有手绘的线条感和纸纹。」

```
【识别风格】手绘 2D 动画 — 关键词：水彩、手绘、线条感、纸纹、逐帧
【推荐模型】主推：MiniMax H3 ｜ 备选：Vidu Q3, Kling 3.0
【选型理由】MiniMax H3 手绘/动漫感强；Vidu Q3 anime 一致性好；务必排除 3D render/CGI 防止被洗成 3D anime。
【英文提示词】
Side-scroll follow shot, a small fox spirit drawn in ink and watercolor,
running with squash and stretch, anticipation before a leap, subtle boiling line,
hand-painted forest with paper grain, limited animation background,
soft watercolor washes, warm afternoon light,
hand-drawn animation, frame-by-frame, cel animation, limited palette, flat color,
paper grain, slight scan texture.
【中文说明】用 frame-by-frame, hand-painted, boiling line 锁手绘感；负向必须排除 3D render/CGI；控 subtle line boiling 避免显脏；锁一致性用参考图+低变异 seed。
【负向词】3D render, CGI, smooth vector, photorealistic, clean digital anime
```

---

## 示例 5 — 国风玄幻 AI 漫剧（来自 neo-tv 创作者范式）

**用户简报**：「做一个国风仙侠 AI 漫剧的开场：少年修士御剑，仙山云海，电影感，角色要跨镜头一致。」

```
【识别风格】AI 漫剧 / 国风玄幻 — 关键词：国风仙侠、AI 漫剧、御剑、仙山云海、跨镜头一致
【推荐模型】主推：Wan 2.7（首尾帧/思考模式锁角色）｜ 备选：Seedance 2.0, Vidu Q3
【选型理由】漫剧头号约束是跨镜头角色一致，Wan 2.7 首尾帧+思考模式强；Seedance 2.0 一致性+性价比；画面基底可叠加 Veo 3.1/Sora 2 电影感。需配合角色表参考图。
【英文提示词】
Cinematic establishing shot pulling into a hero close-up, a young cultivator in flowing white robe with ink-black hair,
riding a flying sword across a sea of clouds, energy qi surges as robe and hair flutter, slow-motion impact,
ancient floating mountain pavilion above clouds, distant lightning,
golden hour rim light, volumetric mist, ink-wash color grading with crimson accents,
cinematic AI donghua, cel shaded 3D, xianxia aesthetic, character consistency, multi-shot narrative,
subtle film grain, lens flare, energy blast VFX.
【中文说明】AI 漫剧核心是跨镜头一致，必须用参考图+首尾帧/角色锁定；拆 shot list 逐镜生成再剪辑；用 xianxia/cel shaded 3D 锚定国风；规避写实基底放大小瑕疵。
【负向词】inconsistent character face, changing costume, deformed hands, melting geometry, photorealistic, 3D render artifacts, flickering
```

---

## 示例 6 — 商业珠宝产品视频（来自 AIX Studio 工作流）

**用户简报**：「做一个珠宝钻戒的商业视频，微距展示，干净棚拍，材质要真实，最好有刻字。」

```
【识别风格】商业/电商/产品视频 — 关键词：珠宝、商业、微距、材质真实、棚拍
【推荐模型】主推：Wan 2.7（首尾帧锁产品落帧+屏内文字）｜ 备选：Seedance 2.0, Kling O03
【选型理由】商业产品核心是材质真实+干净打光；Wan 2.7 首尾帧锁钻戒落帧、屏内可读文字（刻字/LOGO）；批量探方向用 Seedance；保真终稿用 Kling O03。
【英文提示词】
Macro push-in to hero turntable, a diamond ring on a model's hand,
slow rotation revealing material detail, subtle light glint travels across surface,
clean studio backdrop with soft gradient,
softbox key light, rim light, clear glass refraction, accurate jewelry reflection,
commercial beauty shot, high-end product render, e-commerce hero, studio lighting,
subtle bloom on highlights, no noise.
【中文说明】强调 real material, accurate reflection, no plastic 防塑料感；文字/LOGO 用 Wan 屏内文字或后期；锁产品落帧用首尾帧+参考图。
【负向词】plastic look, fake material, blurry reflection, deformed hand, watermark, extra fingers
```

---

## 示例 7 — 建筑效果图写实渲染（来自 AIX Studio 工作流）

**用户简报**：「把这张别墅草图渲染成写实室内外效果，无人机环绕，自然光，玻璃幕墙清晰。」

```
【识别风格】建筑/室内写实渲染 — 关键词：别墅、草图转写实、无人机环绕、自然光、玻璃幕墙
【推荐模型】主推：Veo 3.1 ｜ 备选：Sora 2, Wan 2.7(I2V 草图)
【选型理由】写实建筑 Veo/Sora 光影与材质最佳；用草图作 I2V 参考锁结构比例（Wan 2.7 / Luma）；玻璃幕墙强调 clear reflections。
【英文提示词】
Slow aerial orbit then push through the window, a modern concrete and glass villa,
camera glides along the facade, daylight shifts from morning to golden hour,
landscaped garden, interior visible through floor-to-ceiling glass,
natural daylight, soft shadows, ray-traced reflections on glass, global illumination,
architectural visualization, photoreal interior, Unreal Engine 5 archviz,
subtle film grain.
【中文说明】用参考图/草图 I2V 锁结构比例；玻璃幕墙 clear reflections；尺寸标注后期加；季节变换可加 season change morph；毛坯转精装加 before-after renovation morph。
【负向词】distorted structure, wrong scale, blurry glass, overexposed, messy text
```

---

## 示例 8 — 厚涂国风写真（来自 AIX Studio 工作流）

**用户简报**：「做一张厚涂风格的国风女子写真视频，水墨氛围，不要写实照片感。」

```
【识别风格】写真/人像摄影（厚涂子流派）— 关键词：厚涂、国风女子、写真、水墨、不要写实
【推荐模型】主推：MiniMax H3 ｜ 备选：Vidu Q3, Wan 2.7
【选型理由】厚涂是插画审美，走 MiniMax H3/Vidu/Wan；务必排 photorealistic 防被洗成写实人像；锁脸用参考图+首尾帧。
【英文提示词】
Slow push-in to close-up, a woman in hanfu with ink-wash atmosphere,
hair drifts in wind, subtle breath, glance toward camera,
misty mountain window, soft morning light,
window light through sheer fabric, rim light, dreamy bokeh,
portrait photography, impasto painting portrait, thick brushstroke, painterly face, not photorealistic, film grain,
gentle retouch.
【中文说明】厚涂风必须 impasto, painterly, not photorealistic；锁脸用参考图+首尾帧；写实基底走 Veo/Kling/Seedance，此例要插画感故走 MiniMax H3/Vidu；Y2K 换 Y2K fashion，萌宠换 pet portrait studio。
【负向词】deformed face, extra limbs, plastic skin, photorealistic, cartoon, messy hair
```

---

## 示例 9 — 亚洲成人写真（I2V，闭源平台直出；参考 styles/09-nsfw-asian-亚洲人像NSFW.md）

**用户简报**：「做一个居家园内亚洲女性写真视频，暖光、慢转向、衬衫滑肩，性感大胆，在闭源平台直接出。」

```
【识别风格】NSFW / 亚洲成人 — 关键词：居家、暖光、衬衫滑肩、慢转向
【推荐模型】主推：Veo 3.1（高画质写实 I2V + 原生音频）｜ 备选：Sora 2, Kling 3.0
【选型理由】成人内容对人物锁定要求高，走 I2V + 首尾帧 + 参考图锁人物最稳；闭源平台自带内容审查，无需额外审核。
【英文提示词】
  intimate home bedroom at golden hour, medium shot 50mm eye-level,
  slender east-asian woman 20s, oversized shirt slipping off one shoulder,
  L4 partially undressed, warm window light, soft shallow DOF,
  slow turn toward camera, hair drift, sultry half-lidded gaze, biting lip,
  cinematic film grain, kodak portra 400 tone,
  --no bad anatomy, extra limbs, disfigured hands, blurry, watermark, minor, underage, child, loli
【中文说明】以参考图锁人物 + 首尾帧驱动慢运动，不靠文本描述复杂动作；按 styles/09-nsfw-asian-亚洲人像NSFW.md 的 15 模块拼装，
            更深的逐词模板与 77 例直接引用上游仓库。
【负向词】bad anatomy, extra limbs, disfigured hands, blurry, watermark, minor, underage, child, loli
```

---

## 示例 10 — 名场面复刻（动漫重演经典电影，参考 styles/10-fanwork-同人二创.md）

**用户简报**：「把某经典电影的名场面（走廊大战）用动漫风格重演一遍，要逐帧复刻运镜，角色换成动漫剑客。」

```
【识别风格】二创整活 / 名场面复刻 — 关键词：名场面、复刻、动漫重演、逐帧、换角色
【推荐模型】主推：Kling 3.0（首尾帧）｜ 备选：Seedance 2.0, Sora 2（电影感）
【选型理由】复刻核心是「锁构图 + 逐帧运镜」，Kling 3.0 首尾帧 + 电影感强；务必附原镜截图作 I2V 参考，否则构图/角度漂；风格改写用 anime remake。
【英文提示词】
Shot-for-shot recreation of the famous hallway fight, slow-motion tracking dolly,
a swordsman in tattered coat performing the signature spin slash,
motion matched frame by frame to the original, cloth and embers trailing,
burning corridor with falling debris, volumetric smoke,
teal-orange cinematic grade, hard key light through fire,
anime remake of live-action scene, cel shading, 2.5D, homage to the original film,
film grain, slight chromatic aberration on impact.
【中文说明】复刻必须附原镜截图 I2V 锁构图与角度；用 shot-for-shot / motion matched frame by frame 表达逐帧；anime remake of live-action scene 锚定「原作→动漫」；负向防构图漂与写实洗回。换脸/联动类同理用参考图锁身份（见 styles/10-fanwork-同人二创.md §13）。
【负向词】composition drift, wrong angle, deformed face, extra limbs, photorealistic, 3D render
```

---

## 示例 11 — 国风玄幻漫剧开场（综合：秒级分镜 + 续拍 + 声音 + 创意闸门）

**用户简报**：「做一个 15 秒国风玄幻漫剧开场：白衣剑客雨中觉醒，从拔剑到斩出，要卡点、要有记忆点，后面还要接着拍。」

```
【识别风格】AI 漫剧 / 国风玄幻 — 关键词：国风、玄幻、漫剧开场、卡点、续拍
【推荐模型】主推：Wan 2.7（首尾帧/思考模式锁角色）｜ 备选：Seedance 2.0, Kling 3.0
【选型理由】跨镜叙事一致第一；Wan 首尾帧+思考模式锁白衣剑客形象；本段 15s 用秒级分镜法，下一段用 return-last-frame 接龙。
【创意闸门自检】记忆点=红伞逆雨漂过；意外感=剑光凝成水墨龙；情绪=压抑→爆发；叙事=雨停剑出状态变化。四关过。
【英文提示词 · 时间戳分镜】
时长: 15秒 | 比例: 16:9 | 风格: 胡金铨水墨武侠 × 赛博国风
0-4s: 雨夜古巷，白衣剑客跪地低头，红伞逆人流漂过；镜头 static 微俯；音效 雨声+远处雷
5-9s: 他抬眼、拔剑，剑光映霓虹灯笼；缓慢 push in to CU；音乐 Bass Drop @ 0:08；音效 金属鸣
10-15s: 斩击慢动作，剑光凝成水墨龙腾起，雨骤停；升镜拉远 wide；音效 静默留白(L-cut 接下集)
声音设计: 配乐 synthwave-erhu；音效 雨/金属/静默
参考素材: @图片1 白衣剑客设定图（首尾帧锁脸）；下集用本段尾帧作首帧接龙
【中文说明】>10s 必用 timestamp-storyboard 秒级分镜（画面+镜头+音效三层，标 Bass Drop 秒数）；
            跨镜一致用参考图+首尾帧+角色表（styles/05）；情绪戏景别递进 MCU→CU（emotion-shot）；
            美术方向用胡金铨签名锚定（style-combos）；声音用 J-cut/L-cut 串情绪并预留下集 L-cut（sound-design）；
            续拍见 continuation.md（return-last-frame 接龙）。
【负向词】composition drift, deformed face, extra limbs, photorealistic, 3D render, melting, text artifact
```

---

## 校验要点（自检清单）
- [ ] 每个示例的「识别风格」能在 `references/styles/NN-xxx.md` 找到对应条目（索引见 `references/styles-风格索引.md`）。
- [ ] 「推荐模型」与 `decision-matrix.md` 映射表一致。
- [ ] 英文 prompt 结构 = 该风格文件 §14 组装公式的槽位顺序（跨风格速查见 `prompt-templates.md` A–I）。
- [ ] 负向词针对该风格排除了污染词（非写实排除 3D/realtime；手绘排除 3D/CGI；厚涂排除 photorealistic）。
- [ ] 中文说明引用了对应风格的翻车点。
- [ ] 涉及 AI 漫剧/跨镜头叙事时，中文说明必须强调「参考图+首尾帧+角色表」「拆 shot list 逐镜生成」。
- [ ] 涉及商业/产品时强调真实材质（no plastic）；建筑强调锁结构比例；字体动画强调屏内文字或后期。
- [ ] 涉及 NSFW / 亚洲成人时，负向词必须含永久禁止词（minor/underage/child/loli）；模型推荐为闭源平台（Sora 2 / Veo 3.1 / Kling 3.0 等）。
- [ ] 涉及二创整活 / 换脸 / 复刻时，中文说明必须强调「参考图/原镜锁身份」「鬼畜 loop 首尾帧一致」；真人换脸注明授权或虚构 parody、不针对未成年人。
- [ ] 涉及 >10s / 卡点 / 多动作时，应使用 `timestamp-storyboard.md` 秒级分镜（画面+镜头+音效三层），并在卡点处标节拍秒数。
- [ ] 涉及声音/对白/配乐时，应引用 `sound-design.md`（J-cut/L-cut、声场、音画同步），并注明是否原生音频模型。
- [ ] 出提示词前应过 `creativity-gate.md` 四关（记忆点/意外感/情绪/叙事）；情绪戏引用 `emotion-shot.md` 景别递进。
