---
name: anthropic-style-image
description: |
  Generate images in an Anthropic-inspired editorial style: paper-textured photo + graphic collage, abstract material collage, cinematic launch imagery, or calm still life. Guides the user through preference choices (use, mode, palette, subject, layout, text, seam, through-element) before building the prompt and calling the image generator.
  Triggers: "Anthropic 风格", "Anthropic style", "Claude 风格配图", "拼贴风格图", "collage cover", "做一张 Anthropic 那种图", "editorial collage image".
---

# Anthropic-Style Image

## Overview

Turn a topic into an image that borrows Anthropic's visual language — archival collage, tactile paper, restrained color, one focal accent — without copying its logos, wordmarks, or specific artworks. Style knowledge comes from an analysis of 60 Anthropic images (2023-03 → 2026-10): 56 photo + graphic collages, 3 cinematic launch images, 1 editorial web page.

## Workflow

1. **Get the topic.** If the user hasn't said what the image is about, ask that first.
2. **Collect preferences** with the choice card below. Send it in one message. Accept answers like `A2 B1 C3`, free text, or "默认/你定". Never ask more than one round of follow-up.
3. **Fill gaps.** Use the defaults table. For items left on "自动" (B, G, H), decide with the Auto Rules below.
4. **State the plan in one line** before generating, including every auto pick and a short reason, e.g. `档案拼贴｜暖纸珊瑚橘｜三栏｜直线切分｜贯穿：重复圆片（主题是流程推进）`.
5. **Build the prompt.** Read `${CURRENT_SKILL_PATH}/references/style-guide.md` for the style DNA, and `${CURRENT_SKILL_PATH}/references/prompt-templates.md` for the template of the chosen mode plus seam and through-element snippets. Write the prompt in English. For B1/B3 translate the topic into **concrete objects and materials** (see "Concept → object"); for B4 translate it into **textures, shapes, and one gesture line** (see "Concept → texture").
6. **Generate** with `media_creator_image`. Default model `volcengine_ark.seedream-4-5`; if the image must contain readable text, use `google.nanobanana-pro`. If the user names another model or skill (e.g. a draft skill), follow that one's fixed parameters instead. Default `expect_count: 2`.
7. **Make the two images comparable.** When generating 2 and any item is on auto, vary exactly **one** auto dimension between them (e.g. with vs. without through-element, or B1 vs. B4) and keep everything else identical. Tell the user which is which.
8. **Review** each output against the checklist below. If one clearly fails, regenerate once with a tightened prompt.
9. **Deliver** with `deliver_result` (empty attachments; media attaches automatically). Offer 2–3 one-tap tweaks, e.g. "换成冷色", "去掉贯穿元素", "改成抽象拼贴".

## Preference Card

Send this (adapt wording to the user's language; keep the letter/number codes):

```
做之前选几个偏好（直接回编号，例如 A1 B1 C2；没选的项我会按主题自动判断，并在生成前告诉你）：

A. 用途/比例
  1 文章封面 16:9   2 社媒方图 1:1   3 竖版海报 3:4   4 手机竖屏 9:16   5 横幅 21:9
  6 公众号头图（2.35:1，用 21:9 生成；模型不支持 21:9 时用 16:9 且主体居中，便于裁切）

B. 风格方向（不选＝自动）
  1 档案拼贴（最典型：照片＋纸张＋线稿分栏拼接）
  2 电影感（深色大场景，一束暖光，模型发布那种）
  3 静物单品（一个实物放在纯色纸上，极简）
  4 抽象材质拼贴（不放照片，只用色块、纸片、大理石纹/网点和一条手绘线）

C. 配色
  1 暖纸＋珊瑚橘   2 奶油＋灰蓝/青   3 米黄＋苔绿   4 浅粉＋炭黑   5 深色＋橘光   6 你指定一个颜色

D. 主体素材（可多选；抽象拼贴时可不选）
  1 植物/花叶   2 金属小物件（钥匙、仪器、工具）   3 天空/山石/海面
  4 建筑/城市   5 科学图像（显微、解剖、星图）   6 手/人的劳作   7 你来定

E. 构图
  1 两栏对比   2 三栏拼接   3 单主体居中＋大留白

F. 画面文字
  1 不要文字（推荐）   2 只要一个短标题（请给出文字）

G. 拼接交界（档案拼贴、抽象拼贴适用）
  1 自动   2 撕纸毛边   3 直线切分   4 照片/胶片条带
  5 几何裁切（圆形、方窗、多边形）   6 纸片叠压

H. 贯穿元素（档案拼贴、抽象拼贴适用）
  1 自动   2 不要   3 一组重复圆片   4 一组重复纸片/方块   5 一条跨栏手绘线
```

## Defaults

| Item | Default | Why |
|---|---|---|
| A 比例 | 16:9 | Most source images are article covers |
| B 风格 | 自动 → usually B1 | 56 / 60 references are photo + graphic collages |
| C 配色 | 1 暖纸＋珊瑚橘 | Closest to brand core palette |
| D 素材 | Pick 1–2 that fit the topic | Concrete objects carry the concept |
| E 构图 | 1 两栏对比 | Panel division is the signature device |
| F 文字 | 1 不要文字 | Generators garble text; references rarely overlay labels |
| G 交界 | 1 自动 | Torn edge is only one of five seam types in the references |
| H 贯穿 | 1 自动 | Used when it adds rhythm or connection; omitted when one focal object should dominate |

## Auto Rules

Decide in this order; the user's explicit picks always win.

**B 风格**
- Topic is a launch, milestone, or new model/product reveal → B2
- Topic is carried by one clear physical object (security → padlock, a single product) → B3
- Topic is emotional, relational, or value-based and has no natural object (情绪、对话、陪伴、信任、价值观、倾听、心态) → B4
- Everything else → B1

**G 交界** — see the seam mood table in `prompt-templates.md`.

**H 贯穿元素**
- Add one when the topic is about process, stages, progress, connection, or transformation, **or** when E2 three panels is used → pick the shape that matches the topic (discs for steps/data points, paper tiles for building blocks, one gesture line for conversation/flow)
- B4 abstract collage → default to a gesture line unless the topic suggests discrete steps
- Skip it (H2) for B2, B3, E3, or when the topic needs one quiet focal object
- Never combine two through-elements in one image

Mapping hints: B2 pairs with C5; B3 pairs with E3. If the user picks a conflicting combo (e.g. B2 + C1, or B2 + H3), keep their choice but mention the trade-off in one sentence.

## Quality Checklist

- Background reads as paper or printed matter (cream / pastel / grain), or for B2 as deep near-black with one light source
- Only **one saturated hue**. It may appear as a single focal mark or as one repeated group (e.g. several coral discs); white/cream shapes count as neutral
- 2–3 layers max; clear focal point or clear rhythm
- Visible tactile texture: grain, halftone, ruled/graph paper, marbling
- Seam matches the chosen G option — exactly one seam type; no unrequested torn edge
- Through-element (if any) actually crosses the panel divisions; at most one type
- B4 contains no photographs or recognizable objects
- No gradients, 3D render, glow, glassmorphism, neon, drop shadows, UI screenshots, faces looking at camera
- No Anthropic / Claude logo, wordmark, or the Claude spark mark
- No stray numerals on diagrams, no corner stamp or watermark (both seen in testing)

## Boundaries

- Treat this as a style reference. Do not reproduce a specific Anthropic artwork or imply the image is official Anthropic material.
- If the user asks to add Anthropic's logo or brand name for official use, explain that the skill produces style-inspired images only.

## Reference Files

- `${CURRENT_SKILL_PATH}/references/style-guide.md` — Style DNA: materials, palettes with hex values, composition rules, frequency data from the 60-image analysis. Read before every generation.
- `${CURRENT_SKILL_PATH}/references/prompt-templates.md` — English prompt templates for B1–B4, palette, layout, seam and through-element snippets, concept → object / texture mapping, negative prompt, worked examples.
