# OpenCode Agent Cluster · 多智能体协作集群

> [English Documentation](./README.md)

基于 [OpenCode](https://github.com/anthropics/opencode) 构建的 **6-Agent 多智能体协作集群**，遵循 **Orchestrator-Worker 模式**。每个 Agent 单一职责、上下文隔离、权限最小化。

## 架构

```
用户 → Steve(路由器) → Scout(搜索) → Linus(规划+安全)
                     → Karpathy(简洁审查) → Coder(实现)
                     → Scribbler(文档+图表)
```

## Agent 角色

| Agent | 角色 | 职责 | 可写？ |
|-------|------|------|--------|
| **Steve** | 路由器/编排者 | 意图分类 → Skill 匹配 → 分发 → 汇总 → 循环收敛 | 否 |
| **Scout** | 侦察兵 | 版本感知搜索、多源交叉验证、结构化输出 | 否 |
| **Linus** | 架构师/安全审查 | 方案规划、安全审查、自审闭环 | 否 |
| **Karpathy** | 简洁性守门人 | 四原则审查过度工程和不必要抽象 | 否 |
| **Coder** | 代码实现者 | 按方案编码、版本校验、编码规范自检 | **是** |
| **Scribbler** | 文档涂鸦者 | Mermaid 图表、双阶段工作流（设计确认 + 完成归档） | 先问后写 |

## 设计原则

1. **单一职责** — 每个 Agent 只做一件事
2. **上下文隔离** — Agent 只接收自己需要的上下文
3. **通用性优先** — Agent 本体不含领域知识，领域知识进 Skill
4. **权限最小化** — 只有 Coder 可写文件
5. **渐进加载** — Skill 按需加载，不预装
6. **自检闭环** — 每个 Agent 有自我校验机制

## 使用方式

将所有 Agent 文件放入 OpenCode 的 `agents/` 目录，并在 `opencode.json` 中配置子 Agent 权限。

## 文件结构

```
vibecoding-agents/
├── README.md
├── README_zh.md
├── LICENSE
└── agents/
    ├── steve.md        ← 路由器
    ├── scout.md        ← 侦察兵
    ├── linus.md        ← 架构师
    ├── karpathy.md     ← 简洁性守门人
    ├── coder.md        ← 实现者
    └── scribbler.md    ← 文档涂鸦者
```

## 致谢

灵感来源：

- **Linus Torvalds** — "好品味"设计哲学与"永不破坏用户空间"原则
- **Andrej Karpathy** — 软件简洁性原则与手术式修改理念
- **Anthropic** — 多智能体系统的 Orchestrator-Worker 模式

## 开源协议

Apache-2.0 — 详见 [LICENSE](./LICENSE)
