# Gracker 的作者声音与旧稿修复

用于改已有博客、复核前序润色，以及用户要求恢复个人口吻的场景。先看原稿，再判断要不要改。以下观察来自 Gracker 旧文，描述他的写法，不是所有技术作者的统一模板。

## 原稿里值得保留的东西

| 写法 | 原文依据 | 编辑时怎么处理 |
| --- | --- | --- |
| 从手头的小麻烦讲起 | Nokia X 连不上，查了很久，后来给别人配置时又忘了怎么做 | 保留为什么写这篇、在哪台设备上遇到什么。不要缩成“本文介绍设备连接问题”。 |
| 愿意说自己没做成 | 通知中心里“试过用 db4o 这种对象数据库来进行存储，发现行不通” | 失败经历有信息。保留尝试和结果，再接正确做法；不要改成无主语的规范建议。 |
| 边操作边解释判断 | 过度绘制实战里去掉 `setBounds()` 后，颜色减少了，列表项却变浅了 | 保留观察顺序和副作用。若原结论不成立，改结论，留下当时怎么试的。 |
| 跟同行说话，有一点随口的玩笑 | Log2File 的“其他自己脑补”；Android Studio 的“已经完成了，没有下一步了” | 可以原样保留，不要求每句都新增技术知识。不要在别的文章里复制这些口头禅。 |
| 承认写作和生活不那么整齐 | 通知中心“拖了一段时间才写完”；年终记录“各位看官一笑而过即可～” | 这些是作者的处境和与读者的关系，不能全当元叙述删掉。 |
| 工程判断与个人感受并存 | 过度绘制入门写换公司、忙、发现自己懂得少，然后再讲工具和源码 | 不必把这样的开头改成三句摘要。进入技术解释后保持对象和边界清楚即可。 |
| 用问题带读者走完推理 | 三星重启案例追问“那怎么编译过的呢”；Vsync 篇问能否早点合成、少等一会儿 | 原来的答案有误，可以改答案，保留促使作者继续查的问题。不要把设问一律换成结论句，也不要给没有问句的文章硬加问答。 |
| 技术之外还有身边的人和生活 | 三星案例理解 SystemUI 开发者的辛苦，接到媳妇做这一块六年多、“晚上加个鸡腿”；CPU 篇结尾分享自己拍的照片 | 这些细节不必承担技术论据的任务。不要仅因偏离技术主题就删掉，也不要把具体的人改成泛泛的“开发者很辛苦”。没有原稿依据，不能添家人、照片或生活场景。 |

这些写法的共同点是作者对具体事情有反应。第一人称、括号、设问、吐槽、感叹号都可能承载这种反应；它们本身不构成 AI 味。技术复盘、翻译札记、年终记录的口气可以不同，不要统一成冷静的说明书，也不要反过来给每篇补热闹。

## 对照原文的修复方法

1. 找到用户认可的原稿、历史提交或前序快照。Git HEAD 可能已经被其他 agent 改过，不能自动当作最初原文。找不到依据时保留现文，记录缺口，不凭感觉补经历。
2. 对照三类内容：作者的经历与表达、需要保留的技术纠错、新增的解释或补注。代码修正不意味着同段的经历也得删掉。
3. 原稿有“我试过”，修订稿只剩“原文尝试”时，检查是否把作者写成了被研究的对象。本人做的事恢复本人叙述；引用别人、翻译别人或编辑补注，保留对应的来源身份。
4. 技术结论需要收窄时，让经历和边界都在。例如“我试过 db4o，没走通”可以保留，后面说明可以存必要字段；不能恢复成“Notification 无法持久化”。
5. 新版本说明写清版本、变化和替代办法。能在开头交代的，不必每段反复说“原文保留”“不能据此证明”“本次核查”。独有的证据限制仍要留在相关结论附近。
6. 回读整段及中英文对应稿，检查有没有把取舍变成命令、把失败变成一般规律、把没做过变成已验证，或只在中文保留作者、英文改成第三人称摘要。

用户明确要求“恢复、还原、修复前序润色”时，可以从有出处的旧稿补回内容。这属于有依据的恢复，不是凭空新增材料，也不受纯精修“只改 11 类句式”的范围限制。仍只改已证实的损失和生硬表达，不借机重写全文。

## 修复示例

**真实失败被规范建议盖住**

- 原稿：“试过用 db4o 这种对象数据库来进行存储，发现行不通”。
- 被磨平后：“应用可以把需要的文本、包名、时间等字段存入自己的数据库。”
- 恢复方向：“我当时试过用 db4o 保存整个通知对象，没走通。需要持久化的话，可以把文本、包名、时间等必要字段存进自己的数据库。”具体 API 和持久化限制继续保留。

**本人排查被写成文献综述**

- 被磨平后：“原文找到了 ID 为 `FilesList` 的 ListView，并尝试去掉……”。
- 恢复方向：“接着往下看，`CustomViewAbove` 里有一个 ID 为 `FilesList` 的 ListView。我当时试着去掉了……”。保留列表项变浅的副作用，再说明这还不能算优化成功。

**不能借恢复语气撤销纠错**

- Android Studio 原文里的“已经完成了，没有下一步了”可以放回源码已能阅读的位置。
- 同文过时的命令、错误文件名和版本日期不能因“原话更生动”一起放回。
- 过度绘制原稿的“点个赞”曾紧跟一个改变了外观的尝试，不能原样接到那里暗示验证成功。

**机械删词把作者的话删坏了**

- OpenClaw 实践原稿：“也要说实话。只想把它当 ChatGPT 替代品的人……”是在讲自己的使用边界。
- 后续改稿删掉“说实话”，只剩“也要。”，句子已经不成立。
- 恢复方向：找回整句“也要说实话”，连同后面不适用的人群一起读。词库命中只能提示检查，不能直接对子串做删除；若确实需要删提示语，也必须完整改好句子，不留下残句。

## 最后检查

- 修改后的“我”都能在原文或用户材料中找到依据；没有新编实验、心理活动、设备、数据或读者反馈。
- “没用过”“没走通”“当时这样判断”的不确定性还在，没有被改成权威断言。
- 作者原有的玩笑、称呼、设问和情绪，有具体问题才改；词频、句长、第一人称出现次数不是独立的删除理由。
- 原稿中的生活旁白和对具体人的体谅仍在；英文稿也不能把它们压成通用的经验总结。
- 保留技术纠错、版本限制、来源链接、代码和历史地址；恢复的字句不改变它们的含义。
- 删词后回读整句和前后段，确认没有残句、悬空指代或缺失的转折；原有自我限定不因命中提示语而消失。
- 不以修改数量交差。原文好好的，就保留。

## 样本出处

以下链接固定到本次复核使用的历史提交；它们是文本依据，不是当前技术正确性的证明。

- [Ubuntu / Nokia X](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/ubuntu-adb-can-not-find-devices.md)
- [通知中心实战](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/android-service-build-your-own-notification-servers-app.md)
- [Log2File](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/android_log_to_file.md)
- [过度绘制入门](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/android-performance-optimization-overdraw-1.md)、[过度绘制实战](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/android-performance-optimization-overdraw-2.md)
- [Android Studio 源码阅读](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/view-android-source-code-with-androidstudio.md)
- [2023 年记录](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/2023-review.md)
- [三星重启案例](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/samsung_crash.md)
- [Systrace Vsync](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/Android-Systrace-Vsync.md)、[Systrace CPU](https://github.com/Gracker/Blog/blob/faa1ed543aec17bf8f0c8a1f1348f888c3f6784d/Blog/source/_posts/Android-Systrace-CPU.md)
- [OpenClaw 实践的较早原稿](https://github.com/Gracker/Blog/blob/6dabce4363c4b33928a8153d78fbb2f2422f207c/Blog/source/_posts/OpenClaw-Local-Practice.md)（用于核对“也要说实话”，当前 HEAD 已包含后续删词）
