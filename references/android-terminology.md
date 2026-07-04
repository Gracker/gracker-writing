# Android Terminology Boundary

Android、性能优化、系统机制类文章里，有些词看起来像黑话，但在具体语境里是领域术语。处理这类稿件时，先判断它能不能对应到系统对象、源码路径、线程、trace 轨道、slice/counter、buffer/fence 状态或可复现实验。能对应，就按术语保留；不能对应，再按黑话处理。

## 判断原则

- **有对象**:能说清涉及哪个模块、线程、服务、API、buffer、fence、trace 轨道或源码类。
- **有边界**:能说清起点、终点和关键中转层，而不是只说「全链路」「打通链路」。
- **有证据**:能用 Perfetto、logcat、dumpsys、源码、实验数据或复现步骤支撑。
- **不牺牲精确性**:为了躲黑话把术语改成更空的中文，属于反向降质。

## 不能机械判黑话的 Android 术语

以下词在 Android 技术稿里通常是有效术语，不能因为命中黑话词库就直接删除或替换。

- `渲染链路`:用于描述 UI 线程、RenderThread、BufferQueue、SurfaceFlinger、HWC、Display 等对象之间的帧生产、提交、合成和显示过程。写作时补清起点、终点和关键中转层。
- `输入链路`:用于描述 InputReader、InputDispatcher、Window、ViewRootImpl、View 层级或 Compose 节点的事件分发过程。写作时说明事件在哪个阶段阻塞、丢失或延迟。
- `Binder 调用链`:用于描述跨进程调用路径、Binder 线程池、system_server 服务和客户端线程之间的等待关系。写作时说明调用方、服务方和等待点。
- `Camera/音视频链路`:用于描述 Camera HAL、cameraserver、RequestThread、ImageReader、codec、Surface 或 producer/consumer 之间的 buffer 流转。写作时说明 buffer acquire/release、backpressure 或队列深度变化。
- `数据链路`:只有在描述采集、传输、解析、存储或上报的具体路径时才保留；如果只是把业务流程包装成「数据链路」，按黑话处理。
- `路径`:在 `代码路径`、`调用路径`、`慢路径`、`快路径`、`IO 路径` 中通常是术语；在「增长路径」「用户路径」这类抽象表达里按上下文判断。
- `透传`:在事件、参数、trace 标记、Binder 参数、Intent extra 等被原样传给下游时可以保留；如果只是说「能力透传」「价值透传」，按黑话处理。
- `兜底`:在 fallback、异常恢复、默认策略、降级策略中可以保留；如果只是替代「保障」，优先改成具体机制。
- `落盘`:在 trace、日志、heap dump、profile、缓存写入文件时可以保留；如果只是泛指「保存成果」，改成更具体的动作。

## 常见 Android 术语族

- **渲染与显示**:VSync、Choreographer、ViewRootImpl、RenderThread、HardwareRenderer、BufferQueue、Surface、layer、SurfaceFlinger、HWC、HAL、fence、FrameTimeline、jank。
- **输入与窗口**:InputReader、InputDispatcher、Window、WindowManagerService、ViewRootImpl、触摸事件分发、焦点窗口、ANR。
- **进程与通信**:Binder、Binder 线程池、system_server、ActivityManagerService、WindowManagerService、transaction、oneway 调用。
- **调度与性能**:main thread、RenderThread、sched slice、runnable、blocked、CPU/GPU frequency、DVFS、GC、thermal throttling。
- **Camera 与媒体**:Camera HAL、cameraserver、capture request、RequestThread、ImageReader、MediaCodec、producer/consumer、acquire fence、release fence。
- **内存与存储**:Java/Kotlin heap、native heap、graphics buffer、ashmem、dma-buf、heap dump、profile、page cache。

这些清单不是白名单。遇到新术语时仍按「对象、边界、证据」判断。

## 写作要求

1. 第一次出现关键术语时补一句范围说明，例如「这里的渲染链路指 App 提交 buffer 到 SurfaceFlinger latch 之间的过程」。
2. 图或时序说明不能跳过 trace 里可见的关键层。读者拿图对照 Perfetto 时能找到对应线程、counter 或 slice。
3. 同一段不要连续堆叠术语。连续出现 4 个以上新术语时，拆段或先给整体图。
4. 英文专有名词按 Android 社区常用写法保留，例如 SurfaceFlinger、RenderThread、BufferQueue、HWC、HAL、VSync、Binder、Perfetto、FrameTimeline。
5. 不为了「通俗」把精确术语改成空词。`fence` 不能泛化成「同步机制」后就不再解释，至少说明它约束的是哪一侧读写 buffer。

## 对照示例

✅ 可保留:

> 这条渲染链路从 Choreographer#doFrame 进入，RenderThread 提交 GPU 命令后，buffer 进入 BufferQueue，SurfaceFlinger 在下一轮 VSync 前 latch。

这里的「渲染链路」有起点、终点、中转层和 trace 观察点。

❌ 应改写:

> 打通渲染链路后，体验链路就能形成闭环。

这句话没有系统对象、边界和证据。改成具体动作:

> 先确认 App 是否按帧产生 buffer，再看 SurfaceFlinger 是否按 VSync 节奏 latch；两段都正常时，再看 HWC 合成耗时。
