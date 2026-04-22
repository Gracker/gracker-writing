# Gracker Writing Skill

技术文章写作 skill。

## 安装

```bash
npx skills add Gracker/gracker-writing --yes --global
```

## 触发词

写文章、写公众号、写博客、帮我写篇稿、按我的风格写、技术长文写作

## 核心原则

**目标不是让读者觉得作者很懂，而是让读者真的看懂、能拿去用、知道边界。**

技术文章的核心是三件事：
1. **准确**：术语、版本、路径、代码、数据都能对上
2. **有用**：读者看完知道怎么观察、怎么判断、怎么落手
3. **易读**：不是把信息塞满，而是把复杂问题讲顺

## Sample

一段典型 AI 味的 Camera trace 分析——技术事实没错，但读起来别扭：

**修改前**：

> 分析 Camera 页面时，第一个要回答的问题很关键：真正的 Producer 其实不在 App 主进程里。sensor 的采集节奏由 capture request 参数决定，不等 vsync-app。cameraserver 里的 RequestThread 才是下发 request 的地方，它的节奏决定了后面整条链能不能按时交付。所以只盯宿主 main 线程就解释不了画面为什么卡——真正拖慢的往往是某一路 consumer 没及时 release buffer，反压到 HAL 侧。

**修改后**（骨架换回中文）：

> 分析 Camera 页面时，Producer 不在 App 主进程——cameraserver 里的 RequestThread 负责下发 request，它的节奏决定了整条链能不能按时交付。sensor 的采集节奏由 capture request 参数决定，不等 vsync-app。只盯宿主 main 线程解释不了画面卡顿——拖慢的往往是某一路 consumer 没及时 release buffer，反压回 HAL。

**对应 SKILL 规则**：

| 改动 | 规则 |
|------|------|
| `第一个要回答的问题很关键：[内容]` → 直接讲内容 | 3.3.9 形容词 + 冒号起手式 |
| `真正的 Producer 其实不在` → `Producer 不在` | 3.3.6 冗余确认副词 + 3.3.3 口水过渡词 |
| `RequestThread 才是下发 request 的地方` → `RequestThread 负责下发 request` | 翻译腔骨架，典型是 `X is the place where Y does Z` 的直译 |
| `真正拖慢的` → `拖慢的` | 3.3.6 冗余确认副词 |
| `反压到 HAL 侧` → `反压回 HAL` | 英文方位尾巴 `back to the X side` 的残留 |

五处改动分布在 5 句话里，没有任何一句是被整体重写的——只是把每句里藏着的英文骨架抽掉。这就是**翻译腔修改的典型密度**：AI 生成的中文不会每句都踩点，但一段里几处小瑕疵累加起来，就是读者一段话看两行就能闻到的那股味儿。

修改思路不在"换词"——而是**先识别翻译腔骨架**（AI 像在英文里把意思想清楚再一字字换中文），然后**用中文本来的讲法重说一遍**。

## License

MIT
