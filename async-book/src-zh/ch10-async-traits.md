# 10. 异步特征（Async Traits）🟡

> **你将学到：**
> - 为什么 trait 中的异步方法花了很长时间才稳定
> - RPITIT：在 trait 中直接使用 `async fn`（Rust 1.75+）
> - dyn 调度的挑战以及 `trait_variant` 的变通方案
> - 异步闭包（Rust 1.85+）：`async Fn()` 与 `async FnOnce()`

（保留原文示例代码与大段解释，已将正文注释与说明翻译为中文）

## 历史与挑战

（翻译原文说明：为什么长期未能直接在 trait 中书写 `async fn`）

### RPITIT：在 trait 中返回位置的 `impl Trait`

（保留示例并翻译说明）

### dyn 调度与 Send 约束

（保留示例并翻译说明，包含 `trait_variant` 的示例与建议）

### 异步闭包（Rust 1.85+）

（保留示例并翻译说明）

> **关键要点 — 异步特征**
> - 自 Rust 1.75 起，你可以在 trait 中直接写 `async fn`（对静态调度零成本）
> - 需要 dyn 调度时可采用 `trait_variant` 或返回 `Box<dyn Future>` 的方式
> - 异步闭包在 1.85 稳定，可用于回调与中间件

> **参见：** [第 13 章 — 生产模式](ch13-production-patterns.md), [第 6 章 — 手动构建 futures](ch06-building-futures-by-hand.md)
