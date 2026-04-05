# QEMU 训练营基础阶段 Rust

`qemu_camp_basic_rust` 是 QEMU 训练营基础阶段的 Rust 语言练习仓库，当前基于完整的 Rustlings 题库整理而成。

这个仓库既包含学员要完成的练习题，也包含 Rustlings 命令行工具本体、评测入口和 GitHub Actions 自动评分流程。

当前 Rust 语言部分的 GitHub Classroom 邀请链接是：

- [https://classroom.github.com/a/Itda1slF](https://classroom.github.com/a/Itda1slF)

## 题库概览

### 基础信息

- 题库类型：完整 Rustlings 题库
- 练习总数：`95`
- 练习索引文件：`info.toml`
- 适用阶段：QEMU 训练营基础阶段 Rust 语言练习

### 练习覆盖主题

题库覆盖的内容包括但不限于：

- 变量、函数、条件分支、基础类型
- 所有权、借用、生命周期
- 结构体、枚举、模式匹配
- 集合类型、字符串、错误处理
- 泛型、trait、宏、测试
- 并发、智能指针、迭代器、转换
- Clippy、模块、哈希表、线程等 Rust 常见基础能力

## 目录结构

```text
qemu_camp_basic_rust/
├── Cargo.toml                  # Rustlings 工具依赖配置
├── info.toml                   # 练习索引与提示信息
├── README.md                   # 仓库使用说明
├── exercises/                  # Rust 练习题与章节说明
├── src/                        # Rustlings 命令行工具源码
├── tests/                      # 集成测试与评测入口
└── .github/workflows/rust.yml  # GitHub Actions 自动评测流程
```

## 开始练习

### 1. 准备 Rust 环境


请参考此文档完成 Rust 环境配置：[ArceOS Tutorial Book - 实验环境配置](https://rcore-os.cn/arceos-tutorial-book/ch01-02.html)

请先在 Linux / WSL2 / macOS 环境中完成 Rust 工具链安装，确保至少可以正常使用：

```bash
rustc --version
cargo --version
```

### 2. clone 仓库并进入目录

先通过 GitHub Classroom 邀请链接领取你自己的专属仓库，再执行 clone：

```bash
git clone <你的仓库地址>
cd qemu_camp_basic_rust
```

### 3. 安装 rustlings

推荐使用锁定依赖的方式安装，避免依赖版本漂移导致安装失败：

```bash
cargo install --force --path . --locked
```

### 4. 开始做题

推荐在仓库根目录执行以下命令：

```bash
rustlings list
rustlings watch
```

其中：

- `rustlings list` 用来查看全部练习及当前完成状态
- `rustlings watch` 会自动定位当前练习，并在文件变化时重新检查

## 常用命令

```bash
cargo install --force --path . --locked   # 安装本仓库里的 rustlings
rustlings watch                           # 自动监听并按顺序推进练习
rustlings run 练习名称                    # 单独运行某一道练习
rustlings hint 练习名称                   # 查看指定练习的提示
rustlings list                            # 查看全部练习与完成状态
rustlings reset 练习名称                  # 将指定练习恢复到初始状态
cargo test --test cicv --verbose          # 执行仓库评测入口
```

## 自动评测说明

当前仓库已经接入 GitHub Actions 自动评测，工作流文件位于：

- `qemu_camp_basic_rust/.github/workflows/rust.yml`

默认评测流程包括：

1. 准备评测结果目录
2. 执行 `cargo test --test cicv --verbose`
3. 生成 `.github/result/check_result.json`
4. 汇总通过题数与总分
5. 在非 `pull_request` 场景下，尝试将成绩回传到 OpenCamp

### 成绩上报说明

- OpenCamp 上报用户名来自触发 workflow 的 GitHub 用户名
- 课程 ID、token、API 地址来自仓库 secrets
- 当自动评分或成绩上报出现问题时，工作流会在 summary 中明确区分 `autograde_failed`、`skipped`、`failed`、`reported` 等状态，而不是只显示模糊的 `skipped`

## 本地评测结果

Rust 题库的本地评测输出文件为：

- `.github/result/check_result.json`

这个文件用于给 GitHub Actions 的自动评分解析器读取，一般不需要手动修改。

## 一句话总结

如果你只记住最核心的使用方式，可以直接按下面这个流程开始：

```bash
cd qemu_camp_basic_rust
cargo install --force --path . --locked
rustlings list
rustlings watch
```
