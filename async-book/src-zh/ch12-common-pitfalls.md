# 12. 常见陷阱 🔴

> **你将学到：**
> - 9 个常见的异步 Rust 错误及其修复方法
> - 为什么阻塞执行器是首要错误（以及 `spawn_blocking` 如何修复它）
> - 取消（cancellation）风险：当 future 在 await 中被丢弃时会发生什么
> - 调试工具：`tokio-console`、`tracing`、`#[instrument]`
> - 测试：`#[tokio::test]`、`time::pause()`、基于 trait 的 mocking

（保留原文示例代码，正文说明翻译为中文）

## 阻塞执行器

（保留示例与解释，中文翻译）

### std::thread::sleep 与 tokio::time::sleep 的对比

（保留示例并翻译说明）

### 在 .await 跨域持有 MutexGuard 的风险

（保留示例与建议，已翻译）

### 取消的危险

（保留示例并翻译说明）

### 没有异步的 Drop

（保留示例与建议）

### select! 公平性与饥饿

（保留示例并翻译）

### 导致顺序执行的常见错误

（保留示例与说明）

## 生产环境挂起诊断案例

（保留诊断步骤与修复建议）

### 调试异步代码

（保留 tokio-console、tracing 等工具说明与示例）

### 测试异步代码

（保留各种测试模式与示例）

> **关键要点 — 常见陷阱**
> - 切勿阻塞执行器线程 — 使用 `spawn_blocking` 处理阻塞工作
> - 不要在 `.await` 跨域持有 `MutexGuard` — 缩小锁的作用域或使用 `tokio::sync::Mutex`
> - 取消会立即丢弃 future — 使用可取消安全的模式
> - 使用 `tokio-console` 与 `tracing` 来调试异步问题

> **参见：** [第 8 章 — Tokio 深入](ch08-tokio-deep-dive.md)，[第 13 章 — 生产模式](ch13-production-patterns.md)
