# Hell Grind 原始制作简报 - 完整中文提炼

> **来源页面：** https://higgsfield.ai/@higgsfield.studio/projects/hell-grind
> **获取方式：** 页面动态加载的团队简报正文（通过 browser_console 读取 DOM innerText 提取，非页面 HTML 源码可见）
> **信息性质：** 团队自己写的一手资料，不是二手总结
>
> **各章节来源说明：**
> - 项目概况/工具链/第一至第十章：均来自上述页面的团队制作简报正文
> - 第十一章（目录结构推论）：来自同一页面的文件夹列表（Folders 区域）
> - 第十二章（官方教程）：见 ACADEMY-PROMPTBANK.md
> - 第十三章（评论区）：来自同一页面底部动态加载的715条评论

---

## 项目概况

- **片长：** 95分钟正片
- **团队：** 15人
- **预算：** 不到50万美元
- **生成周期：** 资产准备完成后14天
- **展映：** 2026戛纳电影节 Marché du Film
- **每一帧都是AI生成的**，无摄影机、无演员、无实景
- **视频和语音：** Seedance 2.0
- **角色和地点：** Soul Cinema
- **图像编辑：** Nano Banana Pro + Seedream 4.5
- **画面内文字、道具、地点反向角度：** GPT Image 2
- **团队结构：** 导演组 + 提示词工程师，每人负责自己的场景块

## 工具链确认（官方简报原文）

| 用途 | 工具 | 归属 |
|------|------|------|
| 视频和语音生成 | Seedance 2.0 | 字节跳动 Seed 团队 |
| 角色和地点参考图 | Soul Cinema | Higgsfield 自研 |
| 图像编辑/局部修改 | Nano Banana Pro + Seedream 4.5 | Nano Banana = Google；Seedream = 字节跳动 |
| 画面内文字/道具/反向角度 | GPT Image 2 | OpenAI |
| 提示词写作辅助 | Claude（加载 CINEDANCE/Lira/Acting 三个技能）| Anthropic |
| 项目管理 | Canvas（Higgsfield 平台功能）| Higgsfield |

---

## 一、核心问题

AI视频模型**没有跨镜头记忆**。

你在一个提示词里描述不完整，下一镜角色就会换脸、换衣服、换位置、换声音。一致性不是模型自带功能，是你通过「强制重复描述 + 减少模型自由度」人为制造出来的。

**铁律：Describe everything, every time. 描述词必须每次原样粘贴，绝不缩写。**

---

## 二、五大压缩规则（团队最终总结）

1. **Assets first** — 任何镜头生成前，角色、地点、道具必须全部锁定并完成压力测试。这一条比其他所有技巧加起来都省钱。
2. **Describe everything, every time** — 模型没有记忆。角色描述、地点描述、声音描述必须每次完整重复。
3. **Change one thing at a time** — 每次迭代只改一行。整段重写会丢掉已经生效的部分。所有修改必须进日志。
4. **Give the model less freedom** — 用角落代替整间房，用地标代替开放空间，用地图代替猜测，一镜只做一个主动作。
5. **If a shot will not come together — simplify the shot, not the words** — 10-15次迭代仍不理想，就拆镜、减动作、改角度。

> 团队原话："Every rule in this brief exists because a shot failed without it." 每一条规则都是因为一个镜头失败了才存在的。

> "The pipeline does not need fifteen people to work — it needs the rules followed. It scales down to a team of one." 这套流程不需要15人，需要的是遵守规则。它可以缩小到一个人。

---

## 三、前期制作：资产系统

### 资产 = 文本描述（descriptor）+ 参考图

文本是角色或地点的完整描述，每次原样粘贴到提示词里。参考图是模型用的锚点。两者缺一不可。

### 3.1 角色表（Character Sheet）

三张图：脸部特写 + 全身正面（**故意去掉头**）+ 全身背面。

**为什么正面无头？** 广角镜头时模型会去抓全身图上那个小而模糊的脸，导致脸部质量崩。去掉头后模型只能从特写取脸。

**角色表的制作要求：**
- 用 Soul Cinema 生成脸部（皮肤质感最好，但它是创意型模型，一次返回多个版本，选"最可信"的脸而不是"最美"的脸）
- 故意做成"无聊"的：中性灰背景、平光、真实毛孔、不修图、不加电影感
- 电影感不活在角色表里，活在地点和视频提示词里
- 角色表里加了胶片颗粒和电影镜头 → 角色会带着这个look进每个场景，停止对新光线的反应
- 模型最理解的是 **3/4视角的大幅肖像**（脸微微侧转，不要正脸）
- 检查眼睛：即使深色眼睛也需要瞳孔有反光（catch-light），没有反光的脸看起来是死的

### 3.2 点状修改（衣服、伤疤、血迹）

工作流：在 Nano Banana Pro 或 Seedream 4.5 上对原图做局部修改 → 用蒙版手工贴回原图。

**铁律：一张图永远不要完整跑模型两次。** 每多跑一次，纹理就死一次，颜色就漂移一次。两次之后脸会变成对称的塑料脸，这个死的纹理会伤害后面的视频表演。

### 3.3 压力测试

每个资产锁定前必须通过：10次不同姿势、不同光线的生成。角色必须在10次中全部可识别。不只单独测——要和其他资产同框、在真实场景的光线里测。单独看稳定的角色，和别人同框时经常崩。测试失败 → 问题出在你的描述，不是模型。改描述词，重测。

### 3.4 声音锁定

声音不是资产，是固定描述词。在写对话之前就锁定：音域、节奏、口音、说话方式。每次角色说话时原样粘贴到音频字段，永远不改。

示例：
```
Voice: deep, gravelly bass-baritone; slow, calculated pacing; London street accent; menacing calm — he never raises his voice.
```

声音也要做压力测试，方法同形象测试。如果漂移，回去加强锁定措辞。

### 3.5 表演习惯锁定

每个角色写一段行为描述（走路节奏、手部习惯、压力下的动作、眼睛行为）。场景里只能适配，不能改核心。

物理上做不到的动作**转移能量**，不删除：原本踱步的人坐下后，改成身体晃动 + 手指敲击。

### 3.6 状态拆分

每个状态是独立资产：湿身、受伤、换装 = `@roco`、`@roco_wet`、`@roco_blood`，各有自己的描述。

地点同理：白天、夜晚、雨天是三个不同资产。道具也一样：关键文物有三个版本——完整版（特写用）、血污小版（手掌中短暂展示用）、隐藏版（握拳只露蓝光用）。

**拆分状态比和模型对抗便宜。**

### 3.7 地点表

- **用3/4视角，不要正面图。** 正面"漂亮图"在广角镜头里变成扁平壁纸，超出边缘模型就乱编环境。3/4视角给模型深度信息，能正确放置角色，覆盖几乎一整圈的角度。
- **每个地点留一个锚点**（柱子、灯、沙发），把站位绑在锚点上。"英雄在灯旁边，面对门"有效；"英雄在房间里"是抽彩票。
- **保持单一光源逻辑：** 一个光源、一个阴影方向，永远不要有两个太阳——否则每个新角度都重新发明灯光。
- **反向角度方法一：** 在 GPT Image 2 或 Nano Banana 生成同一房间的另一个角落，匹配原图的软焦。
- **反向角度方法二（后期发现）：** 生成一段空镜视频，让摄像机慢慢走过空间——Seedance 会画出和你参考图一致的其他面。截图你需要的角度，用 Seedream 或 Nano Banana Pro 增强纹理和光照。一张图变一整套地点表。

### 3.8 命名与角色声明

所有资产统一标签（`@roco`、`@loc_cave_front`），全项目、全提示词、全界面只用这一套名字。一个项目一本名字字典。

喂给 Seedance 时，**命名每个参考的角色**：
```
@roco for character reference
@jaxx for character reference
@loc_cave_front for location reference
```

地点参考必须明确禁止继承：
```
@loc_street_rain for location reference — take only the space and the texture: wet asphalt, neon reflections. Do not use as a starting frame, do not inherit the composition, the angle or the color.
```

---

## 四、提示词骨架

### 团队使用的完整骨架顺序

1. **SCENE CONTEXT** — 带"EXACT N CHARACTERS - NO DUPLICATES"头部
2. **ACTIVE REFERENCES** — 角色和地点标签 + 角色命名
3. **LOCATION MAP** — GEO SPATIAL LAYOUT
4. **FIRST FRAME AND SPATIAL BLOCKING** — 第一帧谁站哪
5. **FORMAT MODE** — 一镜到底还是硬切，时长，实时
6. **OPTICS** — 镜头和焦平面
7. **CAMERA** — 摄像机行为 + 永远不做什么
8. **ACTION TIMING** — 按秒拆分动作
9. **PHYSICS** — 重量、接触、惯性
10. **LIGHTING** — 单一光源逻辑
11. **AUDIO** — 声音描述词 + 台词；SFX only
12. **CHARACTER ACTING** — 状态、目标、隐藏、身体节奏、变化
13. **STYLE** — Style Prefix，原样粘贴
14. **QUALITY** — 细节和稳定性要求
15. **POSITIVE CONSTRAINTS** — 每个数量和禁令，写成"画面里有什么"

### 关键写作规则

- **角色数量头部不是形式主义：** 模型喜欢加人和克隆家具。只有参考图在提示词里的人存在于画面中。家具要直接禁止："exactly ONE mannequin, NEVER render a second one."
- **现在时 + 短句**
- **每个动作节拍最多3句**，过载会糊。提示词本身可以长（团队跑到3000-4000词），长度不是敌人，过载的节拍才是。
- **只写正面动作：** 模型会忽略"不要仰倒"或做相反的。写"趴在肚子上"。
- **角色从第一帧就在画面里**，不看镜头（除非特意要求）
- **绝不写年龄：** 内容过滤器读到未成年就变严。用角色、衣服、动作代替年龄。
- **禁用词字典：** "dark" → "low key"，"jolting" → "rapid motion"
- **末尾强制 "SFX only. No music."**：音乐属于后期，生成时的音轨只会妨碍剪辑。
- **技术标签收尾：** Photoreal. NON-IP. [宽高比]. [时长]s. SFX only. NO CGI. Cinematic.

### Style Prefix（团队原版，每次原样粘贴）

```
Style: 8K IMAX. Photorealistic — no 3D render, no game engine, no game-cutscene aesthetic.
Cinematography: floating immersive camera that lives with the actors; natural motivated light; painterly composed frames, strong silhouettes against the light.
Lighting: Natural light only — contre-jour backlight, camera on shadow side, atmospheric haze throughout. Key light from sky and windows only.
Color: 60:30:10 — dominant / secondary / accent.
Camera: Physical cine lens. 180° shutter motion blur.
Skin: Pore-level realism — vellus hair, asymmetric moles, capillary flush, pore-shadow matching on-set light.
Acting: Hollywood — micro-pauses before reactions, precise eye-line, wet living eyes with catch-lights, visible breath and chest rise.
Physics: Gravity and inertia respected — mass has real weight, correct contact shadows. No floating props.
Composition: Rule of thirds + golden ratio. Every person moving from frame one.
Continuity: Characters, props, environment identical across every cut. No identity drift.
Technical: 24fps smooth motion. 8K detail. No jitter.
Audio: Environmental SFX only. No music. No subtitles.
```

---

## 五、GEO SPATIAL LAYOUT（空间锁定）

团队在简报中称之为"最昂贵的早期问题的解法"。

问题：角色传送、换位、摄像机跳到错误的一侧。原因：模型不记得上一个镜头谁站在哪。

解法：每场戏写一份**纯空间地图**，不含角色和动作，所有镜头原样粘贴。

示例：
```
GEO SPATIAL LAYOUT (locked across every shot — pure spatial map):
— PLATFORM = raised circular ritual stone disc at the edge of a cliff.
— ALTAR-MONOLITH: at the cliff edge, MID-RIGHT position relative to the platform.
— RITUAL CENTER: CENTER-LEFT, ~3 m from the altar.
— 180° AXIS: camera ALWAYS stays on the corpse-field side — it NEVER crosses the line.
— BACK-LIGHTING: crimson horizon glow comes from BEHIND the platform, rim-lighting silhouettes from camera's perspective.
```

**规则：**
- GEO 只是地图，地点的"长相"还是来自地点资产（描述词+参考图）
- 左右一律用 `frame-left` / `frame-right`（模型不懂"角色左边"）
- 位置用地标 + 米数："在祭坛旁"、"三米外"
- 明确写摄像机在哪一侧、永远不越哪条线
- **每切一镜，重新声明谁站在哪里、看向哪里**（模型不记得上一个镜头）
- 静态对话给角落，不给整间房（空间越小，模型的选择越少）

---

## 六、第一秒永远是广角定位置

每场戏开头约1秒：只定站位、光线、物体，**不做动作**。

模型会"拍照"记住布局，带到后续镜头。去掉这一秒，角色开始换位。

**技巧：**
- 让角色在这1秒说一声"hm"，模型更容易把这段当独立镜头处理
- 如果接上一条，把上一镜的尾音喂进这1秒，帮缝合
- 代价是1秒runtime，省的是几小时重拍

---

## 七、表演写法

### 核心原则：写行为，不写感受

活场景 = 角色想要什么 + 有东西挡路 + 他采取行动去得到它。情绪从冲突中自然产生。

给模型一个目标和一个障碍，让角色在整个场景中变换打法：开玩笑 → 失败 → 施压 → 失败 → 恳求。每次变换是一个可见事件：停顿、姿势变化、节奏变化。

### 写物理，不写形容词

在情绪词上（"悲伤"、"愤怒"、"震惊"），模型开始即兴发挥，结果肤浅。要写肌肉和身体的工作：颤抖、咬紧的牙关、绷紧的颧骨、从鼻子呼出的轻气。

- 每段动作加一句内心独白（标记 INNER），写角色在想什么、想要什么
- 加分阶段眨眼："一个慢眨 → 快速双眨 → 一个硬重置眨"
- 写明确的注视方向或游移的眼神
- 静态镜头里的微生命规则：每1-2秒一个可见微事件（呼吸抬起胸部、鼻翼动、眉头紧绷又放松）
- 把静止写成"保持的张力"，永远不要写"没人动"（会冻住画面）

### 三个让镜头活起来的技巧

1. **反应在对方说完之前开始：** 听者在中途就get到了，脸已经开始回答
2. **情绪不会瞬间关闭：** 重场面的呼吸仍然不平稳，手仍然不稳——这个尾巴带到下一镜，缝合剪辑
3. **让角色的手一直有事做：** 他不是"在对话"，他在修东西、数东西、倒东西，同时说话。最强重音 = 他因为听到的话而停下手头工作的那一刻

### 对话写法

台词只在 AUDIO 区写，绝不在 ACTION 区写一个字的台词。

结构：声音和情绪 → 引号内的台词 → 物理动作 → 面部反应。

Seedance 喜欢自己加"嗯"、轻笑和整句，所以提示词要有硬禁止：所有人只说引号内的台词；没有台词的人完全静音；写在动作里的"半笑"是面部表情，没有声音。

---

## 八、生产与迭代纪律

- 按场景块组织（每个场景一个 shotlist 文件，每镜有编号、时长、完整提示词）
- 描述词和 Style Prefix 作为常量：改一处，所有镜头同步更新
- 批量生成，场景内所有镜头共享同一份 GEO 和资产描述
- **每次迭代只改一行**，其余原样
- **必须写日志：** 提示词版本、改了什么、结果。没有日志无法复现好镜头
- **10-15次法则：** 超过就简化镜头

### 三个高压下诞生的解法

1. **复杂动作不放在时间线中间：** 团队的门打不开——英雄挪到门边就冻住了。解法：动作开头就打开提示词——"他已经在挥拳中途，门已经在裂"——走向门是另一个镜头。

2. **人群是一个"角色"资产：** 给一个身高和衣服的范围。1-2个领衔群众演员有自己的资产做特写。中景镜头直接说数量——"20+"——否则模型一次给你三个人，下一次给你一百个。

3. **两个空间之间的转场卡在门槛上：** 两个地点资产在一个提示词里，缝合点是一个有光线对比的门廊——"暖琥珀色的房间，拱门外面是冷蓝色走廊"。对比解释了调色变化，也原谅了小几何错误。

4. **巨人靠比例锚点存活：** 每个提示词里有大小对比，加上一个人体参照。没有这两个，模型悄悄把巨人缩回人类身高。

---

## 九、后期制作

### 剪辑与生成并行

剪辑师在场景到达时就开始组装，并下单缺什么："需要手的切镜头"、"需要更广的"。重拍只要几分钟，所以剪辑主动塑造生产，不等它。

**生成几乎总是感觉节奏慢：比感觉对的时候剪得更狠，并计划裁掉每条clip的首尾各半秒——边缘会漂移。**

### 清理

画面锁定后做单独的清理pass。AI素材几乎总是带有工作时看不到但大银幕上看得到的缺陷：多出来的手指、"沸腾"的纹理、招牌上的假文字。

- 小缺陷逐帧修
- 完全坏的镜头用保存的最终提示词重新生成，只改一行
- **第一优先：脸部和手的特写**
- 所有清理严格在调色之前

### 调色

每个生成自带一个"内置调色"，所以调色师先把同场景的邻镜统一到一个look。look本身在前期制作的地点资产里就埋好了——调色师是精修，不是发明。

### 声音

- 不重录语音。Seedance的唇同步台词直接从生成中清理：降噪、统一clip间的音色、把声音放进空间里
- 只有当clip完全没有可用语音时才进棚录
- 音效和音乐在后期建在持续环境音之上：一个共享的氛围把生成的镜头粘成一个空间，即使画面有轻微漂移

---

## 十、附件清单（团队提供的完整技能包）

团队在简报末尾列出了所有附件：

1. **完整制作简报** — 完整流程、决策和技巧细节
2. **CINEDANCE 技能包** — 写视频提示词的工具（writer / auditor / workbench）
3. **Lira 图像提示词技能** — 图像版的 CINEDANCE，知道每个图像模型的弱点
4. **统一表演系统** — 如何写活的表演：场景五支柱、提示词技巧、角色表演大师格式
5. **团队指南与经验** — 含学习心得
6. **11阶段生产流水线** — 完整的11步流程
7. **图解手册** — 含"slop gallery"（失败案例集）
8. **分镜表** — 按场景块分组

文件：
- `CINEDANCE HIGGSFIELD SKILL.md`
- `ACTING SKILL.md`
- `LIRA SKILL.md`

> 注意：团队声明"部分资产和工作文件在制作过程中丢失——少数参考材料可能不可用或只存在于后期版本中。"

## 十一、从公开目录结构读出的额外生产纪律

| 目录现象 | 推论出的纪律 |
|----------|--------------|
| 大场景 `Scene 27` 拆成 `27.1/27.2/.../27.6` | 一个大场景按动作节点拆成更小的子镜头，每个子镜头单独处理 |
| `Scene 67` 再拆成 `67 / 67A / 67B` | 同一个大场景不同版本物理隔离，不混改 |
| `Scene 36,38,40` 放在一起 | 逻辑连续、风格统一的一组镜头可以放一起管理 |
| `Scene 25 Roko vs Robots` 单独命名 | 关键高潮戏份单独标记，方便重点迭代 |
| `Regenerations` 有14593个文件 | 接受AI需要多次试错，不指望一次生成完美 |
| `Flashbacks` 整个单独目录 | 闪回/幻想这些特殊色调片段统一分类，方便统一风格 |
| `Credits` 单独归档 | 参考来源、授权信息全留档，方便追溯 |

---

## 十二、官方教程与补充资源

详细的 Academy 课程列表、46个摄像机提示词库、Seedance 2.5 完整功能参数，见 [ACADEMY-PROMPTBANK.md](./ACADEMY-PROMPTBANK.md)。

---

## 十三、评论区关键信息

从715条评论中提取到：

- 有用户问"How much did this cost to produce?"（制作成本多少）— 团队未在评论区公开回复
- 有用户提到"课程曾上传到 Academy 但后来下架了"（"The lecture was uploaded to Higgsfield Academy, but it's gone now"）
- 有用户感谢开源（"感谢开源"）
- 大量评论表达震惊和震撼，认为这是"AI电影的未来"
- 有用户表示受到激励要参与百万美元大赛

### 项目元数据
- 创建时间：2025年8月4日 18:17
- 总观看：340,780
- 总生成数：115,446
- 点赞：2,998
- 评论：715
- 展映：2026戛纳电影节 Marché du Film

---

*本文档基于 Higgsfield 官方团队在 Hell Grind 项目页面发布的原始制作简报完整提取。所有规则、方法、数字均来自一手资料。*
