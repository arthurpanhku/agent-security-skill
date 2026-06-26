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
- **references-and-frameworks.md**：厂商中立的外部框架交叉引用（OpenAI、Google SAIF、Microsoft、NIST、MITRE ATLAS、OWASP），含威胁→框架映射；所有链接于 2026-06-26 核验
- 威胁景观新增 **MCP 与工具供应链威胁**（工具投毒、rug pull、confused deputy、令牌窃取）
- 新增 **"提示词注入的架构性防御"** 章节：致命三要素、Dual-LLM、CaMeL、egress 控制、人在环
- 项目 **Logo 与图标**（assets/logo.svg、assets/icon.svg）

### Changed
- 修正提示词注入的定性：从"可检测/可过滤"改为架构性防御为主、检测为辅（间接注入无可靠检测解）
- Agentic SOAR 重新定位为前瞻性方向，并标注其自身风险（防御 Agent 亦可被注入、自动响应可能误杀）
- **重写 README**：加入 Logo 与徽章、修正失效的「项目结构」列表与 `yourusername` 占位链接、对齐已更新内容与多方来源

### Planned
- [ ] 添加供应链安全详细分析
- [ ] 创建合规检查清单
- [ ] 添加实现案例研究
- [ ] 开发自动化安全评估工具
- [ ] 创建视频教程
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
