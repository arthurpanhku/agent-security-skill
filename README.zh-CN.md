<div align="center">
  <img src="assets/logo.svg" alt="Agent Security" width="440">
  <p><strong>保护与加固 AI 代理系统的开放式安全研究</strong></p>
  <p>
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-4F46E5" alt="License: MIT"></a>
    <img src="https://img.shields.io/badge/version-1.0-6366F1" alt="Version 1.0">
    <img src="https://img.shields.io/badge/open%20research-welcome-22D3EE" alt="Open research">
    <img src="https://img.shields.io/badge/PRs-welcome-22c55e" alt="PRs welcome">
    <img src="https://img.shields.io/badge/refs%20verified-2026--06--30-64748B" alt="References verified 2026-06-30">
  </p>
  <p>
    <a href="README.md">English</a> ·
    <strong>中文</strong>
  </p>
  <p>
    <a href="zero-trust-for-ai-agents.md">核心框架</a> ·
    <a href="references-and-frameworks.md">外部参考</a> ·
    <a href="vendor-security-sources.md">厂商来源</a> ·
    <a href="SKILL.md">Skill 说明</a> ·
    <a href="CONTRIBUTING.md">贡献指南</a>
  </p>
</div>

---

> **开放式研究项目**：本项目是**香港大学（HKU）一名硕士研究生的自我研究项目**——独立、非商业，且不隶属于文中任何厂商。项目**欢迎开放贡献**：学界、业界及各界研究者均可参与，欢迎提交勘误、补充与可核验的新来源。

## 简介

汇集关于如何保护和加固 AI 代理（Agentic AI）系统的企业级安全框架、研究与最佳实践。核心基于 Anthropic 的 *Zero Trust for AI Agents*，并交叉引用 OpenAI、Google、Microsoft、NIST、MITRE、OWASP 等多方公开研究，力求**厂商中立、来源可核验**。

本项目帮助组织与开发者：

- 理解 AI 代理面临的安全威胁
- 用 Zero Trust 架构保护代理系统
- 满足合规要求（HIPAA、PCI-DSS、FedRAMP 等）
- 建立可观测、可响应的安全运营能力

## 核心内容

| 文档 | 内容 |
| --- | --- |
| [zero-trust-for-ai-agents.md](zero-trust-for-ai-agents.md) | 核心 Zero Trust 框架：威胁景观、三层架构、八阶段实施、提示词注入的架构性防御、Agentic SOAR、合规对齐 |
| [references-and-frameworks.md](references-and-frameworks.md) | 厂商中立的外部框架交叉引用与「威胁 → 框架」映射（所有链接于 2026-06-26 核验） |
| [vendor-security-sources.md](vendor-security-sources.md) | **LLM 厂商与科技大厂的第一方安全来源清单**：各家框架、护栏产品与开源红队工具（于 2026-06-30 核验） |
| [SKILL.md](SKILL.md) | 作为 Claude Skill 的功能说明与用法 |
| [templates/](templates/) | 可直接套用的安全产出模板（威胁建模、致命三要素、MCP 审查、egress 白名单） |

## 威胁景观

1. **提示词注入（Prompt Injection）** — 在输入/外部数据中插入恶意指令以覆盖预期行为
2. **工具中毒（Tool Poisoning）** — 受损的外部工具返回恶意数据或隐藏指令
3. **身份与权限滥用** — 被盗或泄露的代理凭证、横向移动、权限提升
4. **内存中毒（Memory Poisoning）** — 向代理记忆注入虚假信息
5. **供应链攻击** — 代理依赖链（模型、工具、流水线）中的组件被攻破
6. **MCP 与工具供应链威胁** — 工具描述投毒、rug pull、confused deputy、令牌窃取

> **关键认知**：间接提示词注入目前**没有可靠的「检测/过滤」解法**。稳健防御是**架构性**的——最小权限、隔离、限制爆炸半径（[致命三要素](zero-trust-for-ai-agents.md#defending-against-prompt-injection-architecture-over-detection)）。检测只能作为辅助层。

## Zero Trust 核心原则

| 原则 | 含义 | 实施 |
| --- | --- | --- |
| Trust Nothing | 默认不信任任何组件 | 密码学验证所有身份 |
| Verify Everything | 验证一切 | 可观测日志与审计跟踪 |
| Assume Breach | 假设已被攻破 | 工程化隔离与防御 |
| Respond at Agent Speed | 按代理速度响应 | 自动化威胁检测与响应 |
| Improve Continuously | 持续改进 | 渗透测试与红队演练 |

## 三层实施路线

| 层级 | 周期 | 重点能力 |
| --- | --- | --- |
| **Foundation** | 2–4 周 | 代理身份与认证、工具访问日志、输入校验、ACL |
| **Advanced** | 2–3 个月 | 密码学身份（mTLS）、任务范围权限、内存隔离、行为异常检测 |
| **Optimized** | 3–6 个月 | 持续验证、细粒度上下文权限、内存完整性、供应链验证、Agentic SOAR |

## 参考与框架

本项目交叉引用以下公开来源（完整清单与链接见 [references-and-frameworks.md](references-and-frameworks.md)）：

- **厂商**：Anthropic（Zero Trust for AI Agents）、OpenAI（Practices for Governing Agentic AI Systems）、Google（SAIF）、Microsoft（Taxonomy of Failure Modes in Agentic AI Systems）
- **标准**：NIST AI RMF / Generative AI Profile、MITRE ATLAS
- **社区**：OWASP Top 10 for LLM Applications、OWASP Agentic AI – Threats and Mitigations
- **学界**：Greshake et al.（间接注入）、AgentDojo（基准）、CaMeL（按设计防注入）、Willison（致命三要素 / Dual-LLM）

## 合规对齐

| 领域 | 框架 |
| --- | --- |
| AI 治理 / 管理体系 | ISO/IEC 42001:2023 |
| 医疗 | HIPAA |
| 支付 / 财务 | PCI-DSS、SOX |
| 政府 | FedRAMP、FISMA |

## 贡献

本项目欢迎**公开发布**的安全研究与框架贡献。流程：

1. Fork 本仓库
2. 创建特性分支（`git checkout -b feature/your-feature`）
3. 提交更改并附完整来源与引用
4. 推送并开启 Pull Request

详见 [CONTRIBUTING.md](CONTRIBUTING.md)。要求：内容须公开发布、提供可核验来源、保持客观准确、遵循现有 Markdown 风格。

## 项目结构

```
agent-security-skill/
├── README.md                       项目说明（英文，默认）
├── README.zh-CN.md                 项目说明（中文，本文件）
├── SKILL.md                        Skill 功能说明与用法
├── zero-trust-for-ai-agents.md     核心 Zero Trust 框架
├── references-and-frameworks.md    外部框架交叉引用（已验证）
├── vendor-security-sources.md      LLM 厂商与科技大厂第一方安全来源清单
├── CONTRIBUTING.md                 贡献指南
├── CHANGELOG.md                    变更日志
├── LICENSE                         MIT 许可证
├── project.json                    项目元数据
├── templates/                      可直接套用的安全产出模板
│   ├── threat-model-template.md        代理威胁建模模板
│   ├── lethal-trifecta-assessment.md   致命三要素快速评估
│   ├── mcp-server-vetting-checklist.md MCP 服务器审查清单
│   └── egress-allowlist.example.yaml   默认拒绝的出站白名单样例
├── agent-security-skill.skill      Skill 打包文件（ZIP）
└── assets/
    ├── logo.svg                    项目 Logo（横版）
    └── icon.svg                    项目图标（方形）
```

## 许可证

本项目采用 MIT 许可证 — 详见 [LICENSE](LICENSE)。

## 联系与支持

- 🐛 问题与建议：[Issues](https://github.com/arthurpanhku/agent-security-skill/issues)
- 💬 讨论与社区：[Discussions](https://github.com/arthurpanhku/agent-security-skill/discussions)

---

<div align="center">
  <sub>香港大学（HKU）硕士生自我研究项目 · 独立非商业，欢迎各界开放贡献 · 基于 Anthropic Zero Trust for AI Agents 并交叉引用多方公开研究</sub>
</div>
