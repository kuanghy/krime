# Krime（霜）

跨平台 AI Agent 桌面客户端，支持多模型，让 AI 真正动手完成任务。

## 核心定位

一个运行在本地的 **AI Agent 指挥中枢**，用户通过自然语言下达指令，Agent 调用工具自主完成任务。

- **编程开发**：读取项目结构、理解代码、编写和修改文件、执行构建与测试
- **通用自动化**：文件整理、信息抓取、数据处理，以及任何可通过 Shell 或 MCP 完成的工作

## 技术栈

| 层级 | 技术 |
|------|------|
| 前端 | Svelte 5 + TypeScript + Vite |
| UI | shadcn-svelte + marked + highlight.js |
| 桌面壳 | Tauri 2.x |
| 后端 | Rust（reqwest / tokio / sqlx / rmcp） |
| 密钥存储 | tauri-plugin-stronghold |

## 项目结构

```
krime/
├── src/              # SvelteKit 前端
├── src-tauri/        # Rust 后端（Agent Runtime / Provider / Tools）
├── static/           # 静态资源
├── docs/             # 架构设计文档
├── package.json
├── svelte.config.js
├── vite.config.ts
└── tsconfig.json
```

## 设计原则

- **本地优先**：工作区、会话、运行状态、规则和密钥默认保存在本机
- **Rust 为运行时真相源**：run 生命周期、审批、工具执行、取消在 Rust 统一管理
- **前端为投影层**：前端只消费事件和提交命令，不持有唯一运行状态
- **能力边界优先**：基于结构化能力描述控制权限，而非原始命令字符串白名单

## 开发状态

> 项目处于架构设计阶段，尚未开始编码实现。

详见 [架构方案概要设计](docs/架构方案概要设计.md)。

## License

[GPL-3.0](LICENSE)
