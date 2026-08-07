# 导演风格速查 + 风格组合矩阵（Director Anchors & Style Combos）

> 来源：`lmr1123/seedance-video-prompt`（导演风格速查）、`ELK-milu/Seedance2-skill`（导演风格速查 10 位）、`aituberapp/ai-video-skill`（27 视觉风格）、本 skill styles/05「命名美学锚定」。
> 核心方法：**用导演/流派视觉签名锚定美术方向**，比泛写"中国风/科幻"命中率高得多。

---

## 00 导演 / 流派风格速查表（命名美学锚定）

| 导演/流派 | 关键词（英文 tag） | 视觉签名 | 适用风格 |
|---|---|---|---|
| 王家卫 | `slow shutter, neon, yellow-green tint, rain, long lens` | 暧昧、都市疏离、抽帧 | 文艺/都市/二创 |
| 韦斯·安德森 | `symmetrical composition, candy color, storybook, centered` | 强迫症对称、童话色 | 奇幻/广告/喜剧 |
| 张艺谋 | `big color blocks, high saturation, ritual, red` | 大色块、仪式感、红 | 史诗/古装/国风 |
| 诺兰 | `IMAX, practical scale, low-key, realistic` | 实景宏大、冷峻 | 科幻/悬疑/大场面 |
| 胡金铨 | `ink-wash negative space, eastern zen, minimal frame, peking-opera movement` | 水墨留白、禅意、京剧身段 | 武侠/国风（styles/05） |
| 赛博朋克 | `neon, purple-blue-pink, rain, volumetric fog` | 霓虹湿夜 | 科幻/夜景 |
| 新海诚 | `vivid sky, light shafts, detailed background, nostalgic` | 湛蓝天空、光影、乡愁 | 动漫/治愈 |
| 是枝裕和 | `natural light, handheld, intimate, muted` | 生活流、自然光 | 日常/家庭 |
| 黑泽明 | `deep focus, stark contrast, widescreen, fog` | 史诗黑白对比 | 古装/史诗 |
| 蒂姆·伯顿 | `gothic, pale, asymmetrical, whimsy-dark` | 哥特暗黑童话 | 奇幻/暗黑 |

**用法**：在提示词里写 "in the style of 胡金铨's ink-wash wuxia aesthetic" 或 "Wes Anderson symmetrical framing, candy palette"。可类推（张艺谋红 / 新海诚天空 / 王家卫雨夜）。

---

## 01 风格组合矩阵（Style A × Style B）

| 组合 | 效果 | 提示词写法 |
|---|---|---|
| 赛博朋克 + 国风 | 东方未来都市 | `cyberpunk neon × chinese rooflines, holographic lanterns` |
| 胶片复古 + 写真 | 日系怀旧 | `kodak portra 400 × soft window light` |
| 极简 + MG | 高级品牌动效 | `flat minimal × kinetic typography` |
| 水墨 + 3D | 三维国风 | `ink-wash shading × 3D rendered, toon` |
| 蒸汽波 + 动漫 | 复古未来 | `vaporwave × anime cel-shade, purple gradient` |
| 纪录片 + 写实 | 伪纪录 | `documentary handheld × photorealistic` |
| 黏土 + 治愈 | 定格萌系 | `claymation × soft pastel` |

**联动规则**：组合时**只换美术层 tag**，不冲突的运动/镜头层可共用（见 `cinematography.md`）。

---

## 02 视觉风格清单（Visual Style Catalog，27+）

综合 aituber 27 视觉风格 + 本 skill 风格库，可按"美术基底"挑：
1. `photorealistic` 写实真人
2. `cinematic` 电影感
3. `anime` 日式动漫
4. `manhua / donghua` 国漫
5. `3D pixar` 皮克斯 3D
6. `3D render` 写实 3D
7. `toon shaded` 三渲二
8. `cel-shaded` 赛璐珞
9. `ink-wash` 水墨
10. `watercolor` 水彩
11. `oil painting` 油画
12. `sketch / line art` 线稿
13. `claymation` 黏土
14. `pixel art` 像素
15. `low-poly` 低多边形
16. `vaporwave` 蒸汽波
17. `cyberpunk` 赛博朋克
18. `steampunk` 蒸汽朋克
19. `retro / 80s` 复古
20. `noir` 黑色电影
21. `horror / gore` 恐怖
22. `fantasy` 奇幻
23. `sci-fi` 科幻
24. `documentary` 纪录
25. `stop-motion` 定格
26. `paper-cut` 剪纸
27. `ukiyo-e` 浮世绘
28. `impressionist` 印象派
29. `flat design` 扁平
30. `kinetic typography` 动态文字

> 选型时先定「基底风格」→ 再叠「导演签名」→ 再定「运动/镜头」（三层叠加最稳）。

---

## 03 与风格库的关系

- 命名美学锚定是 **styles/05 AI 漫剧**「技术专题：命名美学锚定」的扩展版。
- 基底风格与 `styles/01-10` 一一对应；本表用于**跨风格检索**与**组合实验**。
- 组合冲突见各风格文件「禁止组合表」（如手绘必须排 `3D render/CGI`）。
