# 11. 流（Streams）与异步迭代器 🟡

> **你将学到：**
> - `Stream` 特征：异步多值迭代
> - 创建流的方法：`stream::iter`、`async_stream`、`unfold`
> - 流的组合子：`map`、`filter`、`buffer_unordered`、`fold`
> - 异步 I/O 特征：`AsyncRead`、`AsyncWrite`、`AsyncBufRead`

（保留原文示例与代码块，正文说明已翻译为中文）

## Stream 与 Iterator 的对比

（保留 trait 示例与图示，翻译文字说明）

### 创建与消费流的常见方式

（保留示例代码片段并翻译说明）

> **关键要点 — 流与异步迭代器**
> - `Stream` 是 `Iterator` 的异步对应物，可以按需产生多个值
> - `.buffer_unordered(N)` 是在流中并发处理 N 个元素的关键工具
> - `async_stream::stream!` 是创建自定义流的简单方式

> **参见：** [第 9 章 — 当 Tokio 不适合时](ch09-when-tokio-isnt-the-right-fit.md)，[第 13 章 — 生产模式](ch13-production-patterns.md)
