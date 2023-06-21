![banner](https://user-images.githubusercontent.com/4198311/89027545-461dd180-d35d-11ea-9972-7bf1b07f942d.png)

# John Ray Tracing 2023

![GitHub top language](https://img.shields.io/github/languages/top/Danny2003/John-Raytracing-2023)
![License](https://img.shields.io/github/license/Danny2003/John-Raytracing-2023)
![GitHub repo size](https://img.shields.io/github/repo-size/Danny2003/John-Raytracing-2023)

## 课程介绍

- 本项目为 2022-2023 学年暑期小学期课程
- 项目助教：[钟有为](https://github.com/Danny2003/)、[岑康瑞](https://github.com/Kr-Panghu/)、[杨子董](https://github.com/yzddzy/)

具体安排暂定如下：

- **日程**

  - **Week 1**：介绍项目与前期准备（Task 0）、熟悉 Rust 语法（Task 1）、学习完成教程 book 1（Task 2）
  - **Week 2**：学习完成教程 book 2（Task 3）和多线程优化内容（Task 4）
  - **Week 3**：学习完成 book 3 优化内容（Task 5）
  - **Week 4**：自主学习完成进阶内容（💠 标记的内容）、结课展示 & code review

- **分数**

  - | 任务       | 分数占比（总计 100%）                 |
    | ---------- | ------------------------------------- |
    | **Task 0** | 5%                                    |
    | **Task 1** | 15%                                   |
    | **Task 2** | 20%                                   |
    | **Task 3** | 30%                                   |
    | **Task 4** | 10%                                   |
    | **Task 5** | 10%                                   |
    | **进阶内容** | 10% *（5% 作为基本分，5% 作为 Bonus）*   |
    | **presentation 与 结课展示** | 5% *（作为 Bonus，总分不溢出 100%）* |
    | **code review** | 5% *（基本给满，代码风格太差酌情扣分）* |

---

## 导言

　　Welcome to Ray Tracing 2023 ! 
   
　　本项目主要内容为学习 Rust 语言并实现一个光线追踪渲染器（基于路径追踪算法）。以这个形式，你能通过学习一门新的（而且漂亮的）语言—— Rust 来加深对编程语言设计、编译原理的理解，同时又能趣味性地了解 Computer Graphics 的基础工作。项目设有 presentation 和结课展示环节。使用自己手写的渲染器，发挥艺术才能，创造出惊艳全场的超现实大作吧！

　　下文中 `something` 表示命令行指令或文件，💠 标记表示该条目为进阶内容。

　　你可以直接点击网页右上角的 “Use this template” 绿色按钮将这个项目复制到自己的 GitHub Profile 中。接下来，你需要做一些准备工作。

---

## Task 0: Preparation

- [ ] 在 `raytracer/Cargo.toml` 中，修改作者信息
- [ ] 在 `LICENSE` 中，将作者修改为自己。你也可以换成其他许可证
- [ ] 配置 Rust 环境
  - 使用 [rustup](https://www.rustwiki.org.cn/zh-CN/book/ch01-01-installation.html) 安装 Rust（推荐使用[梯子](https://glados.rocks/)访问，该梯子可凭教育邮箱免费使用一年）。如果下载速度很慢，可以考虑使用 [SJTUG Mirror](https://mirrors.sjtug.sjtu.edu.cn) 的 rust-static 和 crates.io 镜像
  - 之后，你需要安装一些工具。首先，你需要定位到项目目录。而后，运行 `rustup component add clippy rustfmt`
  - 接着，运行 `make ci`。如果程序可以正常运行，那么环境就已经配置成功了
- [ ] 配置 GitHub Actions
  - 如果你的 Repo 直接使用题面模板
    - 那么在上述操作完成后，将库 push 到 GitHub 上。在 GitHub Action 中，“Lint and Test” 和 “Build and Upload” 都应当通过（该功能位于 Github Repo 网页上方项目名称旁的 Actions 选项卡）
    - Repo 已经设置好的 Github actions 需要 `git push --tags` 才能触发，即 `git push` 时提交任意标签。
    - 程序生成的结果会出现在 GitHub Actions 的 Artifacts 中。`output` 文件夹下的内容应当是程序运行时生成的。对 output 文件夹的修改不应该被同步到 GitHub 上（参考 `.gitignore`）
  - 💠你也可以自己学习设计工作流程（可以参考题面 Repo `.github/workflows/cargo.yml`）
  - 我们要求所有的 checkpoints 呈现在 GitHub Actions 中，不得晚于 Deadlines，有三天的 Late days
- [ ] 最后，你可以把 `README.md` 中的教程部分删除，换成自己项目的描述、运行方法等信息

## Deadline 0: 2023-06-21 23:59

- [ ] code review
  - 运行题面 Demo 代码或 Hello World
  - GitHub Actions 成功完成工作流程
  - 每位学生提交 GitHub Repo 链接

## Task 1: Learn about Rust

我们希望用几天的时间让大家熟悉 Rust 的语法。请阅读 [***Rust 程序设计语言(The Rust Programming Language)***](https://www.rustwiki.org.cn/zh-CN/book/)（或者你认为合适的教程）学习，以下为 Tips：

- 通常来说，你只需要用到前 7 章和第 10.2 节的内容
- 如果碰到了 lifetime 相关的问题，请仔细阅读第 4 章，特别是 4.2 的例子。当然，你也可以通过第 15 章中的智能指针解决一部分 lifetime 导致的问题
- Rust 的面向对象特性（trait，对应 C++ 的类）可以在 10.2 中找到
- 涉及到多线程渲染时，你可以阅读第 15、16 章的内容

为了快速上手语法，你可以使用 Rust 语言完成以下[力扣（LeetCode）网站](https://leetcode.cn/)练习（不检查）：

- [ ] [88. 合并两个有序数组](https://leetcode.cn/problems/merge-sorted-array/)
- [ ] [2181. 合并零之间的节点](https://leetcode.cn/problems/merge-nodes-in-between-zeros/)
- [ ] [94. 二叉树的中序遍历](https://leetcode.cn/problems/binary-tree-inorder-traversal/)

## Task 2: Book 1

了解完 Rust 语法，就可以开始学习和动手实现 ray tracer 了！[***Ray Tracing in One Weekend - The Book Series***](https://raytracing.github.io) 是一套十分经典的教程，从原理和实践角度详细地阐释了 ray tracing 的基础知识，本项目便是基于该教程展开：

- [ ] 学习 Ray Tracing book 1，使用 Rust 语言实现该部分程序，并渲染成果图
- [ ] 建议仔细阅读官方文档中文教程中 `使用包、Crate和模块管理不断增长的项目` 章节的内容，管理你的文件结构，方便阅读与调试

## Deadline 1: 2023-06-25 23:59

- [ ] code review
  - Rust 基础语法特性掌握（范围不超出前 7 章与第 10.2 节）
  - book 1 最终成果图
  - book 1 相关实现细节

## Task 3: Book 2

- [ ] 完成 Ray Tracing book 2，要求同 Task 2

## Task 4: Mutithreading

- [ ] 实现多线程渲染

## Deadline 2: 2023-07-2 23:59

- [ ] code review
  - 多线程相关实现细节
  - book 2 最终成果图
  - book 2 相关实现细节

## Task 5: Book 3

通过 book 1 & 2 的学习，你已经实现了一个基于路径追踪算法的光线追踪渲染器，这个渲染器的逻辑十分简单而显然。接下来，你将接触到真正的光线追踪知识，学习一个十分基础而重要的算法——蒙特卡洛算法。在 book 3 中详细阐述了蒙特卡洛算法以及它在我们的渲染器中的应用。

- [ ] 完成 Ray Tracing book 3

## Deadline 3: 2023-07-9 23:59

- [ ] code review
  - book 3 最终成果图
  - 理解蒙特卡洛算法及相关概念
  - 💠尝试找出教程中的问题（错误），并在自己代码中加以解决或改进

## 💠Task 6: 整点花活

通过 *Ray Tracing in One Weekend* 教程的学习，你已经基本掌握了路径追踪算法。正如 book 3 书名 *The Rest of Your Life*，光线追踪和 CG 是一片无垠的知识领域，投入一生的时间或许也无法学尽。本项目剩余的时间便交由你来自由探索，有几个大致方向可供参考：

- [ ] **Track1: 自己设计的艺术品**
- [ ] **Track2: Advanced Program Features**
  请参考 [Alex Chi 学长设计的内容](https://github.com/skyzh/raytracer-tutorial#task-2-advanced-ray-tracer)
- [ ] **Track3: GPU-based RayTracing**
  实时光线追踪（需要支持DXR技术的GPU > GTX1060）。
- [ ] 其他更 exciting 的 idea！

最终成果形式不限，可以是一张图、一份实验报告或一场展示。标记💠的进阶部分除了自主设计艺术品外的大部分内容 John 班的助教们也没有实现过，因此请同学们自主学习，只要写出了除了自主设计艺术品/自主配置 Github Actions 外任意一项进阶部分即可给满分，自主设计艺术品可以拿到进阶部分基本分，最后结课展示时大家互评艺术品，评分最高的三个同学分别可以拿到进阶部分分数 5 分，4 分，3 分的 bonus。

## Deadline 4: 2023-07-15 23:59（注意是最后一周**周六**）

- [ ] code review
  - Task 6 最终成果
  - 💠进阶内容

---

## More Information

### Makefile

[`Makefile`](https://github.com/Danny2003/John-Raytracing-2023/blob/master/Makefile/) 中包含了运行 raytracer 的常用指令。如果没有安装 `make`，你也可以直接运行 `cargo balahbalah`。

* `make fmt` 会自动格式化所有的 Rust 代码
* `make clippy` 会对代码风格做进一步约束
* `make test` 会运行程序中的单元测试。你编写的 `Vec3` 需要通过所有测试
* `make run_release` 会运行优化后的程序。通常来说，你需要用这个选项运行 raytracer。否则，渲染会非常慢
* `make run` 以 debug 模式运行程序
* `make ci` = `fmt + clippy + test + run_release`。建议在把代码 push 到远程仓库之前运行一下 `make ci`

### GitHub Actions

这个仓库已经配置好了 GitHub Actions。只要把代码 push 到远程仓库，GitHub 就会进行下面两个检查。

* **Lint and Test** 会运行所有单元测试，并检查代码风格
* **Build and Upload** 会运行优化后的程序，并将 output 目录下生成的文件传到 build artifacts 中

---

## Self-learning Reference

* [Rust 官方文档中文教程](https://www.rustwiki.org.cn/)
* [Rust 程序设计语言(The Rust Programming Language)](https://www.rustwiki.org.cn/zh-CN/book/)
* [通过例子学 Rust(Rust By Example)](https://www.rustwiki.org.cn/zh-CN/rust-by-example/)
* [rustlings](https://github.com/rust-lang/rustlings) 包含许多 Rust 小练习。如果你希望通过练习来学习 Rust 语言，可以尝试一下这个参考资料。
* [Ray Tracing in One Weekend — The Book Series](https://raytracing.github.io)
* （Advanced）过程宏相关
  * [Procedural Macros](https://doc.rust-lang.org/reference/procedural-macros.html) (关注 Function-like procedural macros 即可)
  * [quote crate](https://crates.io/crates/quote)
* （Advanced）JSON / yaml 读取
  * [serde-json](https://docs.serde.rs/serde_json/)，只需要关注其中的 untyped 部分。
  * [yaml-rust](https://docs.rs/yaml-rust/0.4.4/yaml_rust/)
  * 通常来说，你并不需要使用到下面这个序列化/反序列化的包。
  * [serde](https://serde.rs)

## 致谢

　　本项目的最初创建者是 [Alex Chi](https://github.com/skyzh/) 学长。

　　ACM 班沿用该项目多年，例如 2022 年的 [PPCA-Raytracer-2022](https://github.com/ACMClassCourse-2021/PPCA-Raytracer-2022)。

　　John 班在 2021 年也使用了该项目，见 [raytracer-tutorial](https://github.com/Mighty-A/raytracer-tutorial)。

　　我们基于前人经验，根据 2022 级 John 班的需求，进行了一些调整。感谢 Alex Chi 学长和 ACM 班前辈们的宝贵经验和付出！
