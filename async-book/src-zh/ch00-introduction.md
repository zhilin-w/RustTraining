# 异步 Rust：从 Futures 到生产

## 演讲者介绍

- Microsoft SCHIE（硅与云硬件基础设施工程）团队首席固件架构师
- 在安全、系统级编程（固件、操作系统、虚拟机监控器）、CPU 与平台架构以及 C++ 系统方面具有行业经验
- 自 2017 年（在 AWS EC2）开始使用 Rust，并一直热爱这门语言

---

本指南深入讲解 Rust 中的异步编程。与大多数从 `tokio::main` 开始并略过内部实现细节的教程不同，本书从第一性原理构建理解——`Future` 特征、轮询（poll）、状态机——然后再逐步讲到实际模式、运行时选择与生产环境常见陷阱。

## 适合的人群

- 能够编写同步 Rust 但被异步概念困惑的 Rust 开发者
- 来自 C#、Go、Python 或 JavaScript，熟悉 `async/await` 但不熟悉 Rust 模型的开发者
- 曾被 `Future is not Send`、`Pin<Box<dyn Future>>` 或“程序为什么挂起？”等问题困扰的任何人

## 前置知识

你应当对以下内容比较熟悉：
- 所有权（ownership）、借用（borrowing）与生命周期（lifetimes）
- 特征（traits）与泛型（包括 `impl Trait`）
- 使用 `Result<T, E>` 和 `?` 操作符
- 基本的多线程（`std::thread::spawn`、`Arc`、`Mutex`）

无需先前的异步 Rust 经验。

## 如何使用本书

**首次阅读建议按顺序阅读。** 第一部分到第三部分相互依赖。每章包含：

| 符号 | 含义 |
|------|------|
| 🟢 | 初学者 — 基础概念 |
| 🟡 | 中级 — 需要前面章节作为基础 |
| 🔴 | 高级 — 深入内部或生产模式 |

每章包含：
- 顶部的 **“你将学到什么”** 概述
- 面向视觉学习者的 **Mermaid 图**
- 隐藏答案的内联练习
- 汇总核心思想的 **关键要点**
- 指向相关章节的 **交叉引用**

## 节奏建议

| 章节区间 | 主题 | 建议时间 | 检查点 |
|----------|-------|----------|--------|
| 1–5 | 异步工作原理 | 6–8 小时 | 能解释 `Future`、`Poll`、`Pin`，并理解为何 Rust 没有内置运行时 |
| 6–10 | 生态系统 | 6–8 小时 | 能手动构建 futures、选择运行时并使用 tokio API |
| 11–13 | 生产级异步 | 6–8 小时 | 能编写生产级别的异步代码：流（streams）、正确的错误处理和优雅关机 |
| Capstone | 聊天服务器 | 4–6 小时 | 完成一个整合所有概念的真实异步应用 |

**总估计时间：22–30 小时**

## 练习说明

每个内容章节都有内联练习。Capstone（第 17 章）将所有内容整合为一个项目。为了最大化学习效果：

1. **先尝试做练习再看答案** — 挣扎是学习的关键
2. **手动敲代码而非复制粘贴** — 对 Rust 语法的肌肉记忆很重要
3. **运行每个示例** — `cargo new async-exercises` 并随练习测试代码

## 目录

### 第一部分：异步的工作原理

- [1. 为什么 Rust 中的异步不同](ch01-why-async-is-different-in-rust.md) 🟢 — 根本区别：Rust 没有内置运行时
- [2. `Future` 特征](ch02-the-future-trait.md) 🟡 — `poll()`、`Waker` 与协定
- [3. `Poll` 的工作原理](ch03-how-poll-works.md) 🟡 — 轮询状态机与最小执行器
- [4. `Pin` 与 `Unpin`](ch04-pin-and-unpin.md) 🔴 — 自引用结构为何需要固定
- [5. 状态机揭秘](ch05-the-state-machine-reveal.md) 🟢 — 编译器如何从 `async fn` 生成状态机

### 第二部分：生态系统

- [6. 手动构建 futures](ch06-building-futures-by-hand.md) 🟡 — 从头实现 TimerFuture、Join、Select
- [7. 执行器与运行时](ch07-executors-and-runtimes.md) 🟡 — tokio、smol、async-std、embassy 的选型
- [8. tokio 深入](ch08-tokio-deep-dive.md) 🟡 — 运行时类型、`spawn`、通道与同步原语
- [9. 当 tokio 不适合时](ch09-when-tokio-isnt-the-right-fit.md) 🟡 — LocalSet、FuturesUnordered、运行时无关的库设计
- [10. 异步特征（Async Traits）](ch10-async-traits.md) 🟡 — RPITIT、dyn 调度与 async 闭包

### 第三部分：生产环境异步

- [11. 流（Streams）与异步迭代器](ch11-streams-and-asynciterator.md) 🟡 — 异步迭代、多值流
- [12. 常见陷阱](ch12-common-pitfalls.md) 🔴 — 9 个生产级错误及其避免方法
- [13. 生产模式](ch13-production-patterns.md) 🔴 — 优雅关机、背压、Tower 中间件
- [14. 异步是优化不是架构](ch14-async-is-an-optimization-not-an-architecture.md) 🔴 — 同步内核 + 异步外壳的设计理念

### 附录

- [摘要与速查卡](ch16-summary-and-reference-card.md) — 快速查阅表格与决策树
- [Capstone：异步聊天服务器](ch17-capstone-project.md) — 构建完整异步应用

***

