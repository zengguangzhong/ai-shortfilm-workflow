# 可复制模板：1分钟短视频从零跑通工具包

> 完全基于 Hell Grind 原则缩放，复制就能用。

---

## 目录
- [一、短视频提示词骨架模板](#一短视频提示词骨架模板复制即用)
- [二、分镜表 + GEO 空间地图模板](#二分镜表--geo-空间地图模板)
- [三、完整1分钟示例](#三完整1分钟示例1个角色--1个地点)

---

## 一、短视频提示词骨架模板（复制即用）

```markdown
EXACT 1 CHARACTER — NO DUPLICATES: [角色名].
@[角色标签] for character reference — take only face, body, clothing, skin texture. 100% matches the reference.
[在这里粘贴角色完整描述，每次原样重复]
@[地点标签] for location reference — take only the space and the texture: [简要纹理描述]. Do not use as a starting frame, do not inherit the composition, the angle, or the grade.
GEO SPATIAL LAYOUT (locked across every shot — pure spatial map):
[粘贴本场戏的GEO地图，所有镜头原样复用]
SCENE CONTEXT
[时间、天气、整体氛围，1-3句]
FIRST FRAME AND SPATIAL BLOCKING
SHOT 1 (~1.0s) — a wide that FIXES THE POSITIONS and does nothing else: [角色站位 + 关键物体位置]. No camera move, no action beat.
ACTION TIMING
1.0s–[结束秒] — [按时间拆分动作，每个节拍最多3句，现在时，正面描述]
CHARACTER ACTING
[角色名] — emotional state: [状态]. What they want in this moment: [目标]. What they are hiding: [隐藏的]. Dominant body rhythm: [身体节奏]. Visible habits in this beat: [习惯动作]. What changes across the shot: [本镜变化].
STYLE PREFIX
Cinematic photorealism, natural film grain, 35mm cine lens, shallow depth of field, realistic physics, correct contact shadows, gravity and inertia respected, no floating objects, natural skin texture with visible pores, [本场景灯光描述].
Photoreal. NON-IP. 16:9. [时长]s. SFX only. No music. Cinematic. 8K detail, pore-level skin, no jitter, no flicker; the faces stay exactly their references at every distance.
```

**使用强制规则：**
- ✅ 角色描述、GEO、Style Prefix 一旦锁定，**所有镜头必须原样粘贴**
- ✅ 每次迭代**只改 ACTION TIMING 或 CHARACTER ACTING 里的一行**
- ✅ 生成时强制选 `SFX only`，音乐后期加

---

## 二、分镜表 + GEO 空间地图模板

### GEO 空间地图模板（每场戏只写一次，所有镜头复用）

```markdown
GEO SPATIAL LAYOUT (locked across every shot — pure spatial map):
— [主要空间结构，例如 STREET runs left-right]
— [关键地标1]: [位置描述，frame-LEFT/RIGHT + 大概距离]
— [关键地标2]: ...
— 180° AXIS: camera ALWAYS stays on the [某侧] side — it NEVER crosses the line.
— BACK-LIGHTING / MAIN LIGHT: [光源方向和性质]
```

### 分镜表模板

| 镜号 | 时长 | 景别 | 内容（一句话） | 角色位置 | 关键动作 | 备注 |
|------|------|------|----------------|----------|----------|------|
| 01 | 1s | 广角 | 定位置 | 角色在frame-LEFT | 无动作 | 第一秒定位置 |
| 02 | 4s | 中景 | ... | ... | ... | |
| 03 | 5s | 特写 | ... | ... | ... | |
| ... | | | | | | |

**拆镜原则（来自原项目）：**
- 每镜只做一个主动作
- 复杂动作拆成 2–3 镜
- 对话拆成「说话镜 + 反应镜」
- **每场戏开头必须有1秒广角**定位置

---

## 三、完整1分钟示例（1个角色 + 1个地点，可直接改造成自己的）

**故事：** 雨夜，一个疲惫的女孩在街头发现一只受伤的机械鸟，蹲下观察。
**角色标签：** `@girl`
**地点标签：** `@loc_street_rain`

### 角色描述（锁定后每次原样粘贴）

```
A young East Asian woman in her mid-20s, short black hair slightly damp from rain, pale skin with visible pores, wearing a dark oversized hoodie and black jeans, tired eyes with a small catch-light, quiet and restrained expression.
```

### GEO 地图（本场所有镜头复用）

```
GEO SPATIAL LAYOUT (locked across every shot — pure spatial map):
— STREET runs left-right across the frame.
— NEON SIGN on the far wall, frame-RIGHT, about 8 meters from camera, casting pink-blue light.
— WET ASPHALT reflects neon colors.
— SIDEWALK on frame-LEFT, slightly elevated.
— 180° AXIS: camera ALWAYS stays on the sidewalk side — it NEVER crosses into the street center.
— BACK-LIGHTING: neon glow comes from frame-RIGHT, rim-lighting figures from camera's perspective.
```

### 分镜表示例（约55秒）

| 镜号 | 时长 | 景别 | 内容 |
|------|------|------|------|
| 01 | 1s | 广角 | 定位置：女孩站在人行道，低头看向地面 |
| 02 | 5s | 中景 | 女孩撑伞缓慢走近，停住 |
| 03 | 6s | 中近景 | 女孩蹲下，伞倾斜，手伸向机械鸟 |
| 04 | 5s | 特写 | 女孩手指轻轻触碰机械鸟，表情从疲惫转为好奇 |
| 05 | 4s | 特写 | 机械鸟微微闪烁灯光 |
| 06 | 6s | 中景 | 女孩抬头看向远方，雨仍在下 |

### 镜03完整提示词示例（直接可复制修改）

```markdown
EXACT 1 CHARACTER — NO DUPLICATES: GIRL.
@girl for character reference — take only face, body, clothing, skin texture. 100% matches the reference.
A young East Asian woman in her mid-20s, short black hair slightly damp from rain, pale skin with visible pores, wearing a dark oversized hoodie and black jeans, tired eyes with a small catch-light, quiet and restrained expression.
@loc_street_rain for location reference — take only the space and the texture: wet asphalt, neon reflections. Do not use as a starting frame, do not inherit the composition, the angle, or the grade.
GEO SPATIAL LAYOUT (locked across every shot — pure spatial map):
— STREET runs left-right across the frame.
— NEON SIGN on the far wall, frame-RIGHT, about 8 meters from camera, casting pink-blue light.
— WET ASPHALT reflects neon colors.
— SIDEWALK on frame-LEFT, slightly elevated.
— 180° AXIS: camera ALWAYS stays on the sidewalk side — it NEVER crosses into the street center.
— BACK-LIGHTING: neon glow comes from frame-RIGHT, rim-lighting figures from camera's perspective.
SCENE CONTEXT
Rainy night. Soft continuous rain. Neon lights reflecting on wet ground. Quiet empty street.
FIRST FRAME AND SPATIAL BLOCKING
SHOT 1 (~1.0s) — a wide that FIXES THE POSITIONS and does nothing else: GIRL already crouched on the sidewalk frame-LEFT, umbrella tilted, looking down at a small mechanical bird on the wet asphalt. No camera move, no action beat.
ACTION TIMING
1.0s–4.0s — GIRL slowly extends her right hand toward the mechanical bird. Fingers hesitate just above it. Rain runs off the edge of the umbrella. Her shoulders stay slightly hunched against the cold.
4.0s–6.0s — Her fingertips gently touch the metal surface. She freezes, eyes focused, breath visible in the cold air.
CHARACTER ACTING
GIRL — emotional state: tired but suddenly curious. What she wants in this moment: to understand what she found. What she is hiding: how lonely she has been. Dominant body rhythm: slow, careful, slightly hunched. Visible habits in this beat: she keeps the umbrella tilted to shield the object, fingers hesitate before contact. What changes across the shot: the hesitation turns into a soft, focused stillness.
STYLE PREFIX
Cinematic photorealism, natural film grain, 35mm cine lens, shallow depth of field, realistic physics, correct contact shadows, gravity and inertia respected, no floating objects, natural skin texture with visible pores, soft volumetric rain, neon rim light from the right, low-key lighting.
Photoreal. NON-IP. 16:9. 6s. SFX only. No music. Cinematic. 8K detail, pore-level skin, no jitter, no flicker; the faces stay exactly their references at every distance.
```

---

## 开始行动（最小实践步骤

1. 直接复制上面的骨架和示例，改成你自己的主题
2. 先做角色三视图（记住：脸部特写 + 全身正面无头 + 全身背面），做完压力测试（10次不同姿势都能认出角色
3. 写好GEO空间地图，生成第一镜（先用720p测试）
4. 严格遵守：**一次改一行 + 超过15次不理想就简化镜头

---

*如果你有具体主题，直接告诉我：故事一句话 + 目标时长 + 角色数量，可以直接生成完整分镜+提示词初稿。
