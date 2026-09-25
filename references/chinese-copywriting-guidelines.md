# 中文文案排版指北（采用稿）

来源：sparanoid《中文文案排版指北》（简体中文版）。
仓库：https://github.com/sparanoid/chinese-copywriting-guidelines
许可：MIT，Copyright (c) 2023 Sparanoid, Inc. 采用稿保留版权声明；完整原文以仓库为准。
抓取：2026-09-25，commit `9a5fbeb842f39644352fd79b5d8c6764718105cc`

本文件只迁入写作时要执行的排版规则。工具列表、CSS `text-spacing`、站点名录不迁入。可见正文与机器可读内容的边界仍按 `copy-editing.md`。

## 空格

中文与半角英文、独立数字、版本号之间加半角空格。数字与英文单位之间也加空格。

正确：

- `在 LeanCloud 上，数据存储是围绕 AVObject 进行的。`
- `今天花了 5000 元。`
- `带宽 10 Gbps，SSD 一共 20 TB`
- `Android 15`、`HTTP 请求`、`提升 5 个百分点`

错误：

- `在LeanCloud上`
- `花了 5000元` / `花了5000元`
- `10Gbps` / `20TB`

例外：

- 度数、百分号与数字之间不加空格：`90°`、`15%`。不要写成 `90 °`、`15 %`。
- 产品官方写法保留：`豆瓣FM`。
- 代码、路径、字段、URL、trace 名、线程名不加空格：`user_id`、`SurfaceFlinger::commit`、`sched/sched_switch`。
- 全角标点与相邻字符之间不加空格：`一部 iPhone，好开心！` 不是 `iPhone ，` 或 `iPhone， 好`。

Markdown 链接两侧建议留空格：`请 [提交 issue](url) 再分配`。不是硬性 L1。

## 标点

- 中文句子用全角中文标点，不用 `嗨!`、`"喵"`。
- 完整英文整句、英文专名内部用半角标点：`「Stay hungry, stay foolish.」`
- 中文句子里的英文书名、报刊名用斜体或原名，不套《》。
- 不重复标点：`！` 可以，`！！`、`？？！！` 不行。`？！` 可以保留。
- 简体中文可见正文优先直角引号 `「」`，内层 `『』`。代码、命令、英文原文保持原样。

## 名词与大小写

- 专有名词按官方大小写：`GitHub`，不是 `github` / `GITHUB` / `Github`。
- 常见归一见 `copy-editing.md`。Android 术语：`VSync`、`SurfaceFlinger`、`RenderThread`、`BufferQueue`、`FrameTimeline`、`HWC`。
- 不要用不地道缩写：`TypeScript` 不要写成 `Ts`，`HTML5` 不要写成 `h5`，`React` 不要写成 `RJS`。

## 与阮一峰规范的关系

- 中文与数字之间：本 skill 采用指北，**加空格**。
- 数字与 `%` / `°`：采用指北，**不加空格**。
- 引号：采用指北争议项里的直角引号，与 `copy-editing.md` 一致。
- 句子风格、标题层级、数字增减表达：走 `document-style-guide.md`。

## 交付前扫描

只扫可见正文。

```
[一-龥][A-Za-z]
[A-Za-z][一-龥]
[一-龥][0-9]
[0-9][一-龥]
[0-9](Gbps|GB|GiB|TB|MB|KB|ms|ns|Hz|GHz)
[0-9] °|[0-9] %
！！|？？|。。。
```

命中后先看是不是代码、路径、官方产品名或 `%`/`°` 例外，再改。不要对整篇 Markdown 跑自动加空格工具。
