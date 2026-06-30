# 变更日志

所有对 agent-security-skill 的显著更改将被记录在此文件中。

格式遵循 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.0.0/)，
和此项目采用 [Semantic Versioning](https://semver.org/zh-CN/spec/v2.0.0.html)。

## [1.0.0] - 2026-06-26

### Added
- 初始版本发布
- Zero Trust for AI Agents 企业级框架
- 三层安全架构（Foundation, Advanced, Optimized）
- 八阶段实现工作流
- 完整的威胁景观分析
  - 提示词注入攻击
  - 工具中毒
  - 身份和权限滥用
  - 内存中毒
  - 供应链攻击
- Agentic SOAR 自动化防御机制
- 合规性对齐指南
  - HIPAA
  - PCI-DSS
  - SOX
  - FedRAMP
  - FISMA
- 项目基础文件
  - README.md
  - CONTRIBUTING.md
  - LICENSE (MIT)
  - SKILL.md

### Documentation
- 创建详细的实施指南
- 添加快速开始指南
- 创建贡献者指南
- GitHub 设置文档

## [Unreleased]

### Added
- **ISO/IEC 42001:2023 支持**：新增对全球首个 AI 管理体系（AIMS）标准的对齐 —— 作为横切的**治理/管理体系层**（policy、风险处置、持续改进），区别于 HIPAA/PCI 等行业合规。已接入核心框架的合规章节、references 标准清单、双语 README 合规表、`project.json`、威胁建模模板的合规勾选项，以及 SKILL.md 触发描述
- **README 双语化**：`README.md` 改为英文（默认，符合国际开放研究项目惯例），新增 `README.zh-CN.md` 中文版；两者顶部提供 `English · 中文` 语言切换链接，内容保持同步
- **可执行 Skill 化**：为 `SKILL.md` 添加标准 YAML frontmatter（`name` / `description`），使其可作为 Claude Skill 被正确识别与触发；重写为操作性指令而非营销文案
- **templates/**：四份可直接套用的安全产出模板 —— 代理威胁建模、致命三要素快速评估、MCP 服务器审查清单、默认拒绝的出站白名单样例（egress allowlist）
- **vendor-security-sources.md**：LLM 厂商与科技大厂第一方安全来源清单（Anthropic / OpenAI / Google / Meta / Microsoft / AWS / NVIDIA / IBM / Cisco / CSA 等），含开源红队工具（PyRIT、garak、NeMo Guardrails 等）；所有链接于 2026-06-30 核验
- **references-and-frameworks.md**：厂商中立的外部框架交叉引用（OpenAI、Google SAIF、Microsoft、NIST、MITRE ATLAS、OWASP），含威胁→框架映射；所有链接于 2026-06-26 核验
- 威胁景观新增 **MCP 与工具供应链威胁**（工具投毒、rug pull、confused deputy、令牌窃取）
- 新增 **"提示词注入的架构性防御"** 章节：致命三要素、Dual-LLM、CaMeL、egress 控制、人在环
- 项目 **Logo 与图标**（assets/logo.svg、assets/icon.svg）

### Changed
- 修正提示词注入的定性：从"可检测/可过滤"改为架构性防御为主、检测为辅（间接注入无可靠检测解）
- Agentic SOAR 重新定位为前瞻性方向，并标注其自身风险（防御 Agent 亦可被注入、自动响应可能误杀）
- **重写 README**：加入 Logo 与徽章、修正失效的「项目结构」列表与 `yourusername` 占位链接、对齐已更新内容与多方来源
- **项目归属标注**：明确为香港大学（HKU）硕士生的自我研究项目 —— 独立、非商业、不隶属任何厂商，欢迎开放贡献（README、SKILL.md、vendor-security-sources.md 统一）
- **重建 `agent-security-skill.skill` 打包文件**：纳入新的 SKILL.md（含 frontmatter）、templates/、vendor-security-sources.md、references-and-frameworks.md 及 assets，使包内相对链接均可解析（此前打包内容已严重滞后）
- 修正 `project.json` 仓库地址占位符（`yourusername` → `arthurpanhku`）

### Removed
- 精简重复的元文档：删除 **PROJECT_SUMMARY.md**、**INDEX.md**、**GITHUB_SETUP.md**（三者与 README 大量重复，且 GitHub 设置指南不应入库）；导航统一回归 README，并同步清理其内部链接

### Planned
- [ ] 添加供应链安全详细分析
- [ ] 创建合规检查清单（HIPAA / PCI-DSS / FedRAMP 逐条）
- [ ] 添加实现案例研究
- [x] ~~开发自动化安全评估工具~~ → 已提供 templates/ 模板套件（威胁建模、致命三要素、MCP 审查、egress 白名单）
- [ ] 提供可复现的 AgentDojo 评测脚本（验证防御有效性）
- [ ] 加入 CI 链接核验 + markdown lint（守住「可核验」招牌）
- [ ] 建立社区讨论论坛

---

## 版本说明

### v1.0.0
**发布日期**: 2026-06-26
- 首次公开发布
- 基于 Anthropic 的零信任 AI 代理框架
- 完整的安全实施指南

---

## 如何贡献

请遵循 [CONTRIBUTING.md](CONTRIBUTING.md) 中的指南。

对于重大更改，请先开立 Issue 讨论你的建议。

## 许可证

本项目采用 MIT 许可证 - 详见 [LICENSE](LICENSE) 文件
