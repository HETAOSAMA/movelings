# 🏃‍♂️ Movelings

[![Rust](https://img.shields.io/badge/rust-1.70+-blue.svg)](https://www.rust-lang.org)
[![Move](https://img.shields.io/badge/move-sui-orange.svg)](https://sui.io/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)

学习 Move 编程语言的互动式练习。

通过一系列循序渐进的练习，掌握 Move 语言的核心概念和 Sui 区块链开发技能。

## 📚 项目简介

Movelings 是一个交互式的 Move 语言学习工具，包含：

- 🎯 **渐进式练习**：从基础语法到高级概念
- 🔄 **自动检测**：实时反馈和错误提示
- 💡 **智能提示**：从代码注释中自动提取学习指导
- 📊 **进度跟踪**：记录学习进度，支持断点续学
- 🎨 **友好界面**：清晰的命令行界面和丰富的 emoji 提示

## 🚀 快速开始

### 前置要求

1. **安装 Rust**：

   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   source ~/.cargo/env
   ```
2. **安装 Sui CLI**：

   ```bash
   cargo install --locked --git https://github.com/MystenLabs/sui.git --branch testnet sui
   ```
3. **验证安装**：

   ```bash
   rustc --version
   sui --version
   ```

### 安装和运行

1. **克隆仓库**：

   ```bash
   git clone https://github.com/your-username/movelings.git
   cd movelings
   ```
2. **启动学习**：

   ```bash
   cargo run
   ```

## 🎮 使用指南

### 基本命令

| 命令                        | 功能               | 示例                        |
| --------------------------- | ------------------ | --------------------------- |
| `cargo run`               | 显示主菜单和概览   | -                           |
| `cargo run <练习名>`      | 检查特定练习       | `cargo run 00_intro`      |
| `cargo run list`          | 列出所有练习和进度 | -                           |
| `cargo run hint <练习名>` | 获取练习提示       | `cargo run hint 00_intro` |
| `cargo run progress`      | 查看详细进度报告   | -                           |
| `cargo run reset`         | 重置所有进度       | -                           |

### 学习流程

1. **查看菜单**：

   ```bash
   cargo run
   ```
2. **开始第一个练习**：

   ```bash
   cargo run 00_intro
   ```
3. **根据提示修改代码**：

   - 打开 `exercises/00_intro/sources/intro.move`
   - 按照注释中的 TODO 和 HINT 完成练习
   - 保存文件
4. **重新测试**：

   ```bash
   cargo run 00_intro
   ```
5. **获取帮助**（如果卡住）：

   ```bash
   cargo run hint 00_intro
   ```
6. **查看进度**：

   ```bash
   cargo run list
   ```

### 练习结构

```
exercises/
├── 00_intro/           # 🌱 Move 基础入门
│   ├── Move.toml       # 包配置文件
│   └── sources/
│       └── intro.move  # 练习代码
├── 01_variables/       # 📦 变量和类型
├── 02_functions/       # 🔧 函数定义
├── 03_structs/         # 🏗️ 结构体
├── 04_resources/       # 💎 资源和所有权
├── 05_modules/         # 📚 模块系统
└── ...                 # 更多练习
```

## 📖 练习大纲

### 🌱 基础部分

- **00_intro** - Move 语言介绍和基本语法
- **01_variables** - 变量声明、可变性和类型
- **02_functions** - 函数定义、参数和返回值
- **03_if** - 条件语句和布尔逻辑
- **04_primitive_types** - 基础数据类型
- **05_vecs** - 向量和集合操作

### 🏗️ 中级部分

- **06_structs** - 结构体定义和使用
- **07_enums** - 枚举类型和模式匹配
- **08_modules** - 模块系统和可见性
- **09_error_handling** - 错误处理和断言
- **10_generics** - 泛型编程

### 💎 高级部分

- **11_resources** - 资源类型和线性类型系统
- **12_capabilities** - 权限控制和安全模式
- **13_events** - 事件发射和监听
- **14_testing** - 单元测试和集成测试
- **15_publishing** - 包发布和部署

## 💡 提示系统

Movelings 支持智能提示系统，会自动从练习代码中提取指导信息：

### 提示格式

```move
/*
练习描述

// HINT: 这是一个提示
// TODO: 这是需要完成的任务
// 1. 第一步操作
// 2. 第二步操作
*/

module example::example {
    // TODO: 实现这个函数
    // public fun my_function() { ... }
}
```

### 获取提示

```bash
# 查看特定练习的所有提示
cargo run hint 00_intro

# 练习失败时会自动显示提示
cargo run 00_intro
```

## 📊 进度跟踪

### 查看进度

```bash
# 简单列表视图
cargo run list

# 详细进度报告
cargo run progress
```

### 进度文件

进度保存在项目根目录的 `.movelings_progress` 文件中：

```
00_intro
01_variables
02_functions
```

### 重置进度

```bash
cargo run reset
```

## 🛠️ 开发和扩展

### 添加新练习

1. **创建练习目录**：

   ```bash
   mkdir exercises/XX_new_topic
   cd exercises/XX_new_topic
   ```
2. **创建 Move.toml**：

   ```toml
   [package]
   name = "new_topic"
   edition = "2024.beta"

   [addresses]
   new_topic = "0x0"
   ```
3. **创建练习文件**：

   ```bash
   mkdir sources
   # 创建 sources/exercise.move
   ```
4. **添加提示和 TODO**：

   ```move
   /*
   // HINT: 学习新概念的提示
   // TODO: 完成特定任务
   // 1. 步骤一
   // 2. 步骤二
   */
   ```

### 自定义配置

可以修改 `src/main.rs` 中的默认提示：

```rust
fn show_default_hints() {
    let hints = vec![
        "自定义默认提示1",
        "自定义默认提示2",
        // ...
    ];
}
```

## 🤝 贡献指南

欢迎贡献！您可以：

- 🐛 报告 bug
- 💡 建议新功能
- 📝 改进文档
- 🎯 添加新练习
- 🔧 优化代码

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 📚 相关资源

- [Move 语言官方文档](https://move-language.github.io/move/)
- [Sui 开发文档](https://docs.sui.io/)
- [Sui 示例项目](https://github.com/MystenLabs/sui/tree/main/examples)

---

**开始您的 Move 学习之旅吧！** 🚀

如有问题，请查看 [Issues](https://github.com/your-username/movelings/issues) 或创建新的 issue。
