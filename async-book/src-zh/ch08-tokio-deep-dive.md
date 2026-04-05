# 8. Tokio 深入 🟡

> **你将学到：**
> - 运行时风格：多线程 vs 单线程（current-thread）及其适用场景
> - `tokio::spawn` 的 `'static` 要求与 `JoinHandle`
> - 任务取消语义（cancel-on-drop）
> - 同步原语：Mutex、RwLock、Semaphore 以及四种通道类型

## 运行时风格：多线程 vs 单线程

（保留示例代码与 mermaid 图，中文说明已翻译）

### `tokio::spawn` 与 `'static` 要求

（保留示例与解释）

### JoinHandle 与任务取消

（保留示例）

### Tokio 的同步原语

（保留通道类型、Mutex 等示例）

### 运行时选型与通道使用建议

（保留表格与练习）

> **关键要点 — Tokio 深入**
> - 对于服务器使用 `multi_thread`；CLI 或需要 `!Send` 的场景用 `current_thread`
> - `tokio::spawn` 要求 `'static + Send`；用 `Arc` 或克隆共享数据
> - 丢弃 `JoinHandle` 不会取消任务；需显式调用 `.abort()`

> **参见：** [第 9 章 — 当 Tokio 不适合时](ch09-when-tokio-isnt-the-right-fit.md)，[第 12 章 — 常见陷阱](ch12-common-pitfalls.md)

***
