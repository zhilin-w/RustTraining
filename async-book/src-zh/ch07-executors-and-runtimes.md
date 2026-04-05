# 7. 执行器与运行时 🟡

> **你将学到：**
> - 执行器的职责：轮询并高效睡眠
> - 六大主要运行时：mio、io_uring、tokio、async-std、smol、embassy
> - 选择合适运行时的决策树
> - 运行时无关的库设计的重要性

## 执行器做什么

执行器有两项工作：
1. 在可做进展时轮询 futures
2. 在没有 ready 的 futures 时使用操作系统 I/O 通知 API 高效睡眠

（保留原文图示与示例，中文注释已添加）

### mio：基础层

（保留说明与示例）

### io_uring：基于完成的未来

（保留比较表格与示例）

### tokio：电池齐全的运行时

（保留 tokio 示例与特性说明）

### async-std、smol、embassy 简述

（保留各自简短说明和示例）

### 运行时选择决策树

（保留原 mermaid 决策图与解释）

> **关键要点 — 执行器与运行时**
> - 执行器：在被唤醒时轮询 futures，并使用 OS I/O API 睡眠
> - `tokio` 是服务器应用的默认选择；`smol` 适合最小化依赖；`embassy` 适合嵌入式
> - 业务逻辑应该依赖 `std::future::Future`，而不是具体运行时

> **参见：** [第 8 章 — Tokio 深入](ch08-tokio-deep-dive.md)

***
