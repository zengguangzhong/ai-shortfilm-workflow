# AI 短视频工业化生产方法 | 从 Hell Grind 提炼

> 研究基于：[Hell Grind](https://higgsfield.ai/@higgsfield.studio/projects/hell-grind) — 95分钟全AI生成电影，15人团队，<50万美元，14天生成，2026戛纳展映。

## 文档导航

📚 **[PRODUCTION-BRIEF.md](./PRODUCTION-BRIEF.md)** — 核心文档
团队原始制作简报完整中文提炼。包含：五大生产规则、资产系统（角色表/压力测试/声音锁定/状态拆分）、GEO空间锁定、提示词骨架（15区块）+ Style Prefix原版、表演写法、迭代纪律、后期制作。一手资料，最权威。

📚 **[ACADEMY-PROMPTBANK.md](./ACADEMY-PROMPTBANK.md)** - 工具与参考
Higgsfield Academy 全部16门课程教学大纲 + 46个摄像机运镜提示词库（完整原文，可直接复制）+ Seedance 2.5 完整功能参数与示例。

📚 **[SEEDANCE-25-OFFICIAL.md](./SEEDANCE-25-OFFICIAL.md)** - 豆包官方升级介绍
ByteDance 飞书官方文档提炼。Seedance 2.5 七大核心能力（时间戳编辑/30s时长/真实感/对白/视频编辑/多模态参考）+ Seedream 5.0 Pro 四大更新 + 与 Higgsfield 产品页的对比。

📋 **[TEMPLATE.md](./TEMPLATE.md)** — 实操模板
1分钟短视频从零跑通工具包：提示词骨架模板 + GEO空间地图模板 + 分镜表模板 + 完整示例（雨夜女孩与机械鸟，含逐镜提示词）。

## 来源 URL 对照表

| 仓库文件 | 来源 URL | 获取方式 |
|----------|----------|----------|
| PRODUCTION-BRIEF.md 第一至十章 | https://higgsfield.ai/@higgsfield.studio/projects/hell-grind | 页面动态加载的团队简报正文，browser_console 读取 DOM innerText |
| PRODUCTION-BRIEF.md 第十一章 | 同上 | 页面 Folders 区域的文件夹列表 |
| PRODUCTION-BRIEF.md 第十三章 | 同上 | 页面底部动态加载的715条评论 |
| ACADEMY-PROMPTBANK.md 课程部分 | https://higgsfield.ai/academy/courses 及各课程子页面 | web_extract + browser_snapshot |
| ACADEMY-PROMPTBANK.md 提示词库 | https://higgsfield.ai/academy/apps/prompt-bank?section=camera | browser_console 提取动态加载内容 |
| ACADEMY-PROMPTBANK.md Seedance参数 | https://higgsfield.ai/seedance/2.5 | web_extract + browser_console 展开FAQ折叠面板 |
| SEEDANCE-25-OFFICIAL.md | https://bytedance.larkoffice.com/docx/EvLJdw9n8oX1HExDfllcA22jnLe | web_extract（飞书文档，部分需登录） |
| TEMPLATE.md | 基于以上所有页面的原则缩放 | 非原文直接引用，是原则的实操化 |

## 未获取内容（需要登录或视频播放）

- 三个技能文件完整内容：CINEDANCE SKILL.md / ACTING SKILL.md / LIRA SKILL.md（页面上只显示文件名，点击需登录）
- Canvas 预览内容（角色表/地点表/道具表的在线画布）
- 具体 Scene 文件夹里的实际文件（点击未跳转到文件列表）
- 95分钟视频本身（未播放）
- Academy 课程视频内容（只有教学大纲，视频本身未看）
- Prompt Bank 其他分类（只抓了 Camera 分类46个，可能还有 Lighting/Style 等分类）

## 一句话总结

模型没有记忆，一致性不是天生的，是靠「强制重复描述 + 减少模型自由度」人为制造出来的。这套方法不需要15人，一个人遵守规则就能跑。

## License

MIT
