# Gracker Writing

用于技术文章写作、审阅、精修和作者口吻恢复，也为社交稿提供表达检查。

写清问题和判断依据，同时保留作者的观察、取舍、疑问和生活细节。去 AI 味不靠禁词表，恢复活人感也不靠添加口头禅或编造经历。

## 安装

安装仓库默认分支的当前版本：

```bash
npx skills add Gracker/gracker-writing --yes --global
```

入口是 [SKILL.md](SKILL.md)。可以直接要求“按我的风格写”“精修这篇文章”“只给 review 意见”或“对照旧稿恢复作者口吻”。改稿范围由请求决定，不默认重写全文。

## 如何使用

- **新稿**：从读者问题和已有材料组织内容，选择适合体裁的结构。
- **精修**：修具体的含义、逻辑或表达问题，保留原有观点与叙述方式。
- **口吻恢复**：对照可信原稿找回被删的作者表达，同时保留已确认的技术纠错。
- **只审查**：给出具体位置、问题与影响，不擅自改正文。
- **社交与调研稿**：按读者目的选择材料，不强制反转开场、测评分数或行动清单。

## 参考文件

主入口按任务引导读取，不需要每次加载全部资料。

| 用途 | 参考 |
| --- | --- |
| 作者声音与自然表达 | [author-voice](references/author-voice.md)、[human-feel](references/human-feel.md) |
| 结构与局部表达 | [style-rules](references/style-rules.md)、[less-ai-tone](references/less-ai-tone.md) |
| 改稿范围与复核 | [refinement-mode](references/refinement-mode.md)、[quality-gate](references/quality-gate.md) |
| 校对、文档组织与排版 | [copy-editing](references/copy-editing.md)、[document-style-guide](references/document-style-guide.md)、[chinese-copywriting-guidelines](references/chinese-copywriting-guidelines.md) |
| 特定领域 | [android-terminology](references/android-terminology.md)，仅涉及该领域时读取 |
| 社交与调研表达 | [social-output-gate](references/social-output-gate.md)、[research-social-longform](references/research-social-longform.md) |

通用方法、作者偏好和领域说明分别维护。项目术语、渠道投递、自动任务行为与文件落点留在当前项目或调用任务中，不从单篇稿件直接升级成通用规则。已有材料中的代码、数据、引用和作者经历，都不能为了文风失真。

## 来源与许可

部分参考文件吸收了已有写作资料，并在对应文件中保留来源与采用范围；这些资料是编辑判断的参考，不是可据以识别作者身份的检测器。

本仓库使用 [MIT License](LICENSE)。
