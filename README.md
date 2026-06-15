# OpenCode Agent Cluster

A **6-agent collaborative cluster** built on [OpenCode](https://github.com/anthropics/opencode), designed around the **Orchestrator-Worker pattern**. Each agent has a single responsibility, minimal context, and least privilege.

> [中文文档](./README_zh.md)

## Architecture

```
User → Steve (router) → Scout (research) → Linus (planning + security)
                      → Karpathy (simplicity review) → Coder (implementation)
                      → Scribbler (docs + diagrams)
```

## Agents

| Agent | Role | Does | Write? |
|-------|------|------|--------|
| **Steve** | Router & Orchestrator | Intent classification → Skill matching → dispatch → aggregate | No |
| **Scout** | Researcher | Version-aware search, multi-source cross-validation, structured output | No |
| **Linus** | Architect & Security Reviewer | Architecture planning, security review, self-audit loop | No |
| **Karpathy** | Simplicity Gatekeeper | Guard against over-engineering and unnecessary abstraction | No |
| **Coder** | Implementer | Follows plan, version validation before coding, style self-check | **Yes** |
| **Scribbler** | Documenter | Mermaid diagrams, dual-phase workflow (design confirmation + archive) | Ask first |

## Design Principles

1. **Single Responsibility** — Each agent does exactly one thing
2. **Context Isolation** — Agents receive only the context they need
3. **Domain-agnostic Core** — Domain knowledge lives in Skills, not agents
4. **Least Privilege** — Only Coder can write files
5. **Progressive Loading** — Skills loaded on demand, never preloaded
6. **Self-audit Loop** — Every agent validates its own output

## Usage

Place all agent files in your OpenCode `agents/` directory and configure sub-agent permissions in `opencode.json`.

## File Structure

```
vibecoding-agents/
├── README.md
├── README_zh.md
├── LICENSE
└── agents/
    ├── steve.md        ← Router
    ├── scout.md        ← Researcher
    ├── linus.md        ← Architect
    ├── karpathy.md     ← Simplicity Gatekeeper
    ├── coder.md        ← Implementer
    └── scribbler.md    ← Documenter
```

## Acknowledgements

Inspired by:

- **Linus Torvalds** — design philosophy of "good taste" and "never break userspace"
- **Andrej Karpathy** — software simplicity principles and surgical-change discipline
- **Anthropic** — Orchestrator-Worker pattern for multi-agent systems

## License

Apache-2.0 — See [LICENSE](./LICENSE)
