# 3. `Poll` 的工作原理 🟡

> **你将学到：**
> - 执行器的轮询循环：poll → pending → wake → 再次 poll
> - 如何从头构建最小执行器
> - 虚假唤醒规则以及原因
> - 实用函数：`poll_fn()` 和 `yield_now()`

## 轮询状态机

执行器运行一个循环：轮询一个 future，如果返回 `Pending`，则将其挂起直到对应的 waker 触发，然后再次轮询。这与由内核负责调度的操作系统线程有根本不同。

（保留 state diagram 与最小执行器示例代码，中文解释已翻译）

> **重要**：在 *Waiting* 状态期间，future 必须已将 waker 注册到某个 I/O 源。没有注册会导致永远挂起。

### 最小执行器

（保留示例代码并在周边添加中文注释）

> **不要在生产中使用此实现！** 它会忙循环（busy-loop），浪费 CPU。真实的执行器（如 tokio、smol）会使用 `epoll`/`kqueue`/`io_uring` 在没有事件时睡眠。

### 唤醒通知

真实执行器是事件驱动的：当所有 future 都返回 `Pending` 时，执行器会睡眠。waker 是中断机制。

（保留执行器主循环的概念代码）

### 虚假唤醒

future 可能会在 I/O 未就绪时被轮询，这叫做*虚假唤醒*。实现 `poll()` 时必须正确处理：总是重新检查真实条件并重新注册 waker。

（保留示例与规则列表）

### 练习：实现 CountdownFuture（重复练习）

（保留练习与答案）

### 实用工具：`poll_fn` 与 `yield_now`

（保留示例及说明）

> **关键要点 — Poll 的工作方式**
> - 执行器会重复调用被唤醒的 futures 的 `poll()`
> - futures 必须处理**虚假唤醒** — 始终重新检查条件
> - `poll_fn()` 用来从闭包创建临时 future
> - `yield_now()` 在 CPU 密集的异步循环中用于让出执行权

> **参见：** [第 2 章 — Future 特征](ch02-the-future-trait.md)，[第 5 章 — 状态机揭秘](ch05-the-state-machine-reveal.md)

***
