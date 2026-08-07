# 声音设计 / 音画同步（Sound Design & Audio-Visual Sync）

> 来源：`CyberJ0605/cinematic-video-prompt-engineer-skill`（声音桥 J-cut/L-cut、整体声场统一）、Runway prompting guide、geekjourneyx/awesome-ai-video-prompts（音画同步章）。
> AI 视频的"声音"分两层：① 模型**原生音频**（Veo 3.1 / Kling 3.0 / MiniMax H3 / Seedance 2.0 可生成对白/音效/配乐）；② 后期配音（HeyGen/Hedra/剪辑软件）。本文件讲提示词层如何**指挥声音与画面关系**。

---

## 00 声音桥（Sound Bridge）— 剪辑连贯核心

- `J-cut`：声音**先于**画面进入（下一镜的声音提前混入本镜结尾）→ 顺滑过渡、预示。
- `L-cut`：声音**延续到**下一镜画面之后（本镜声音拖到下一镜开头）→ 余韵、情绪延续。
- `audio bridge across shots`：跨镜画外音（voice-over / 环境声）统一连续性（CyberJ：复杂场景用"整体声音"统一多镜头）。
- `sound rupture / break`：在语义转折/关键词处让声音突然断裂（悬疑、冲击）。

**用法**：在提示词里写 "J-cut: next scene's rain sound starts under this shot" 或 "L-cut: her last word echoes into the empty hallway"。

---

## 01 声场设计（Sound Field）

| 维度 | 英文 tag | 说明 |
|---|---|---|
| 画内声 | `diegetic sound` | 画面内可信声源（脚步、钥匙、风） |
| 画外/配乐 | `non-diegetic score` | 情绪配乐、旁白 |
| 环境底噪 | `ambient bed / room tone` | 空间真实感（冰箱低频、远处电梯） |
| 拟音 | `foley (footsteps, fabric)` | 细节质感 |
| 静默 | `silence / dead air` | 留白即张力（CyberJ 案例：春晚笑声压低只剩筷子声） |
| 画外音 | `off-screen voice (OS)` | 电话、画外呼喊 |

**CyberJ 铁律**：每条提示词须含**可信光源 + 具体声场**；恐惧来自"空间与声音"（钥匙轻响、冰箱低频、远处电梯），不只靠画面。

---

## 02 音画同步（Beat-Sync / AV Sync）

- `music beat-sync`：画面节奏**对齐音乐节拍**（卡点视频核心，lmr1123 示例 6：标注 `Bass Drop` 发生秒数）。
- `climax alignment`：高潮画面落在副歌/重拍。
- `tempo ramp`：节奏由慢到快（如香水广告 0-3s 慢 → 4-8s 加速 → 9-15s 留白）。
- `lip-sync`：对白口型同步（原生音频模型 Kling/MiniMax H3/Veo 支持）。
- `SFX cue`：特定音效触发特定动作（开门声=门开）。

**时间戳分镜里标注**：在 `timestamp-storyboard-秒级分镜法.md` 的每段时间轴写 `音乐: Bass Drop @ 0:08`、`音效: 玻璃碎 @ 0:04`。

---

## 03 各风格声音要点

- **PV / 音乐 MV**（styles-风格库/01）：必须 `beat-sync`；写明曲风（synthwave / lo-fi / orchestral）。
- **AI 漫剧**（styles-风格库/05）：用 J-cut/L-cut 串情绪；对白用 `lip-sync`（Kling/MiniMax H3/Veo）。
- **商业/产品**（styles-风格库/06）：`ASMR` 质感（液体、布料）、品牌 jingle。
- **悬疑/恐怖**（CyberJ 案例）：低频环境 + 突然 `sound rupture`。
- **治愈/日常**：自然声（水流、风、鸟鸣）+ 轻配乐。

---

## 04 模型原生音频能力（选型参考）

| 模型 | 原生音频 | 提示词写法 |
|---|---|---|
| Veo 3.1 | 对白+音效+配乐最强 | 直接写 "ambient city sound, distant siren" |
| Kling 3.0 / O03 | 对白+音效 | "character speaks: '...', rain SFX" |
| MiniMax H3 | 原生双声道（全部结果默认带声）| 对白+音效+配乐；TTS 11 种语言、音色克隆/迁移；动漫向口型稳 |
| Seedance 2.0 | 音画同生（参考音频卡点） | `--audio` + "画面随节拍切换" |
| Sora 2 | 叙事音效 | 自然语言描述声场 |
| 无原生音频模型 | 后期配音 | 提示词只管画面，声音交剪辑 |

**反模式**
- ❌ 纯 T2V 模型硬要"可读歌词字幕"→ 乱码，字幕后期做。
- ❌ 忘记写声场 → 画面"无声感"空洞；至少给 `ambient bed`。
- ❌ 声音与情绪错位（欢快画面配哀伤配乐）→ 观感割裂。
