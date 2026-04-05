# 2. `Future` 特征 🟡

> **你将学到：**
> - `Future` 特征：`Output`、`poll()`、`Context`、`Waker`
> - Waker 如何通知执行器“再次轮询我”
> - 协定：如果不调用 `wake()`，程序会静默挂起
> - 如何手动实现一个真实的 future（例如 `Delay`）

## Future 的构成

异步 Rust 中的一切最终都实现了这个特征：

（保留 trait 代码块）

Future 是可以被轮询的对象：被问到“完成了吗？”，并返回 `Ready(value)` 或 `Pending`。

### Output、poll()、Context、Waker

（保留序列图示与示例代码，文字说明翻译如下）

执行器调用 `poll(cx)`，future 检查资源是否就绪；如果未就绪，它会注册 `waker` 并返回 `Poll::Pending`。当资源准备好时，资源应调用 `waker.wake()`，执行器会再次轮询该 future，最终返回 `Poll::Ready`。

（保留 Ready42 示例与 Delay 示例代码，中文注释已加入）

> **关键洞察**：在 C# 中，TaskScheduler 会自动处理唤醒；在 Rust 中，必须由你或所用的 I/O 库负责调用 `waker.wake()`，否则程序会静默挂起。

### 练习：实现 CountdownFuture

（保留练习与解答示例代码，注释翻译）

> **关键要点 — Future 特征**
> - `Future::poll()` 返回 `Poll::Ready(value)` 或 `Poll::Pending`
> - 在返回 `Pending` 之前必须注册 `Waker`，以便执行器知道何时重新轮询
> - `Pin<&mut Self>` 保证 future 在内存中不会被移动（见第 4 章）
> - async/await、组合子等都是建立在该特征之上的

> **参见：** [第 3 章 — Poll 的工作方式](ch03-how-poll-works.md)，[第 6 章 — 手动构建 futures](ch06-building-futures-by-hand.md)

***
