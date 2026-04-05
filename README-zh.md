**许可证** 本项目采用 [MIT License](LICENSE) 与 [Creative Commons Attribution 4.0 International (CC-BY-4.0)](LICENSE-DOCS) 双重许可。

**商标** 本项目可能包含项目、产品或服务的商标或徽标。对 Microsoft 商标或徽标的授权使用须遵循 Microsoft 的[商标与品牌指南](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general)。在修改版本中使用 Microsoft 商标或徽标不得引起混淆或暗示 Microsoft 赞助。任何第三方商标或徽标的使用须遵守相应第三方的政策。

# Rust 培训书籍（中文）

七套培训课程，涵盖面向不同编程背景的 Rust 入门、异步、进阶模式与工程实战。

本资料将原创内容与 Rust 生态中优秀资源的理念与示例结合，目标是提供深入且技术准确的课程，按教学逻辑组织分章内容。

> **免责声明：** 这些书籍为培训材料，不代表权威参考。我们力求准确，但在关键细节上请以 [官方 Rust 文档](https://doc.rust-lang.org/) 与 [Rust Reference](https://doc.rust-lang.org/reference/) 为准。

### 致谢与灵感来源

- [**The Rust Programming Language**](https://doc.rust-lang.org/book/) — 基础参考
- [**Jon Gjengset**](https://www.youtube.com/c/JonGjengset) — 深入 Rust 内部的讲解
- [**withoutboats**](https://without.boats/blog/) — 异步设计、`Pin` 与 futures 模型
- [**fasterthanlime (Amos)**](https://fasterthanli.me/) — 系统级编程长文
- [**Mara Bos**](https://marabos.nl/) — 原子与锁机制
- [**Aleksey Kladov (matklad)**](https://matklad.github.io/) — Rust 分析器、API 设计与错误处理
- [**Niko Matsakis**](https://smallcultfollowing.com/babysteps/) — 语言设计与借用检查器内部机制
- [**Rust by Example**](https://doc.rust-lang.org/rust-by-example/) 与 [**Rustonomicon**](https://doc.rust-lang.org/nomicon/) — 实用范例与 unsafe 深入
- [**This Week in Rust**](https://this-week-in-rust.org/) — 社区发现与资讯
- …以及 Rust 社区中诸多博文、演讲与 RFC 的贡献者

## 📖 开始阅读

选择与你背景相匹配的书籍。书籍按难度分组，便于规划学习路径：

| 等级 | 说明 |
|------|------|
| 🟢 **入门桥接** | 从其他语言迁移到 Rust 的入门教材 |
| 🔵 **深度解析** | 针对 Rust 子系统的专题深入 |
| 🟡 **进阶** | 给有经验 Rustacean 的模式与技巧 |
| 🟣 **专家** | 类型驱动与正确性高阶主题 |
| 🟤 **工程实践** | 工程、工具链与生产就绪实践 |

| 书籍 | 等级 | 适合人群 |
|------|------|---------|
| [**Rust for C/C++ Programmers**](c-cpp-book/src/SUMMARY.md) | 🟢 入门桥接 | 关注所有权、RAII、FFI、嵌入式、no_std |
| [**Rust for C# Programmers**](csharp-book/src/SUMMARY.md) | 🟢 入门桥接 | 从 C#/Java/Swift 迁移到 Rust |
| [**Rust for Python Programmers**](python-book/src/SUMMARY.md) | 🟢 入门桥接 | 动态语言到静态类型、无 GIL 并发 |
| [**Async Rust**](async-book/src/SUMMARY.md) | 🔵 深度解析 | Tokio、流、取消安全 |
| [**Rust Patterns**](rust-patterns-book/src/SUMMARY.md) | 🟡 进阶 | `Pin`、分配器、无锁结构、unsafe |
| [**Type-Driven Correctness**](type-driven-correctness-book/src/SUMMARY.md) | 🟣 专家 | 类型状态、幻影类型、能力令牌 |
| [**Rust Engineering Practices**](engineering-book/src/SUMMARY.md) | 🟤 工程实践 | 构建脚本、交叉编译、CI/CD、Miri |

每本书通常包含 15–16 章，附带 Mermaid 图、可编辑的 Rust playground 示例、练习与全文搜索功能。

> **提示：** 你可以直接在 GitHub 上查看 Markdown 源文件，或通过本地服务获得更好体验：

本地服务推荐步骤：

```bash
# 如未安装 Rust，请先通过 rustup 安装：
# https://rustup.rs/

cargo install mdbook@0.4.52 mdbook-mermaid@0.14.0
cargo xtask serve          # 构建所有书籍并打开本地服务器
```

---

## 🔧 给维护者的说明

<details>
<summary>本地构建与编辑说明（展开查看）</summary>

### 先决条件

请先通过 [rustup](https://rustup.rs/) 安装 Rust，然后：

```bash
cargo install mdbook@0.4.52 mdbook-mermaid@0.14.0
```

### 构建与本地服务

```bash
cargo xtask build               # 将所有书籍构建到 site/ 供本地预览
cargo xtask serve               # 在 http://localhost:3000 上构建并服务
cargo xtask deploy              # 构建到 docs/（用于 GitHub Pages）
cargo xtask clean               # 删除 site/ 与 docs/
```

构建或服务单本书：

```bash
cd c-cpp-book && mdbook serve --open    # 然后打开 http://localhost:3000
```

### 部署

站点在推送到 `main` 分支时会通过 .github/workflows/pages.yml 自动部署到 GitHub Pages，无需手动操作。

</details>
