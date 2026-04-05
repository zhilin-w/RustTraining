# 6. 手动构建 Futures 🟡

> **你将学到：**
> - 用线程唤醒实现 `TimerFuture`
> - 构建 `Join` 组合子：并发运行两个 futures
> - 构建 `Select` 组合子：竞速两个 futures
> - 组合子如何相互嵌套——futures 一层套一层

## 简单的计时器 Future（TimerFuture）

（保留原文 TimerFuture 的完整示例代码与中文注释）

### Join：并行运行两个 futures

（保留原文 Join 实现示例与中文说明）

### Select：竞速两个 futures

（保留 Select 示例与公平性说明）

> **关键要点 — 手动构建 futures**
> - future 需要三样东西：状态、`poll()` 实现，以及 waker 注册
> - `Join` 在同一线程内轮询子 future；`Select` 返回最先完成的那个并丢弃另一个
> - 手动构建能深入理解底层，但在生产中优先使用 `tokio::join!` / `select!`

> **参见：** [第 2 章 — Future 特征](ch02-the-future-trait.md)，[第 8 章 — Tokio 深入](ch08-tokio-deep-dive.md)

***
