# Agent Security Skill

汇集公开研究报告，关于如何保护和加固AI代理系统的安全框架和最佳实践。

## 项目目标

本项目收集、整理和分享关于AI代理安全的企业级研究、框架和指南，帮助组织和开发者：

- 理解AI代理面临的安全威胁
- 实施Zero Trust架构保护代理系统
- 满足合规性要求（HIPAA、PCI-DSS、FedRAMP等）
- 建立自动化安全运营能力

## 核心内容

### 📄 研究报告

#### [Zero Trust for AI Agents](./zero-trust-for-ai-agents.md)
**来源**: Anthropic - Claude Security  
**发布**: May 27, 2026

企业级Zero Trust框架，涵盖：
- AI代理特有的安全考虑
- 当前威胁景观分析
- 三层Zero Trust架构
- 八阶段实现工作流
- Agentic SOAR（代理安全运营中心）
- 合规性对齐指南

**关键要点**:
- 信任零信任 (Trust Nothing)
- 验证一切 (Verify Everything)  
- 假设已被攻破 (Assume Breach)
- 按代理速度响应 (Respond at Agent Speed)
- 持续改进 (Improve Continuously)

## 快速开始

### Foundation Tier (2-4周)
```
基础代理身份和认证
工具访问日志
提示词注入检测
简单访问控制列表
```

### Advanced Tier (2-3个月)
```
密码学代理身份 (mTLS)
任务范围权限
内存隔离和验证
行为异常检测
```

### Optimized Tier (3-6个月)
```
连续验证的密码学身份
细粒度、上下文感知的权限
内存完整性和中毒检测
自动威胁检测和响应
代理SOAR
```

## 项目结构

```
agent-security-skill/
├── README.md                          # 项目说明
├── LICENSE                           # MIT许可证
├── zero-trust-for-ai-agents.md       # Claude Zero Trust框架
├── THREAT_LANDSCAPE.md               # 威胁分析详细版
├── IMPLEMENTATION_GUIDE.md           # 实施指南
└── research/                         # 研究报告目录
    ├── prompt-injection-attacks.md
    ├── memory-poisoning.md
    ├── supply-chain-security.md
    └── ...
```

## 贡献指南

欢迎贡献公开的安全研究报告！

### 贡献流程

1. Fork 本仓库
2. 创建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交你的更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

### 贡献指南

- 只添加**公开发布**的研究或框架
- 提供完整的来源和引用
- 保持内容的客观性和准确性
- 遵循现有的Markdown格式

## 关键资源

### 官方文档
- [Anthropic - Zero Trust for AI Agents](https://claude.com/blog/zero-trust-for-ai-agents)
- [Claude Security](https://www.anthropic.com/product/security)

### 相关标准
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [Zero Trust Architecture](https://en.wikipedia.org/wiki/Zero_trust_architecture)
- [OWASP Top 10 for LLM Applications](https://owasp.org/www-project-top-10-for-large-language-model-applications/)

## 核心威胁

1. **提示词注入 (Prompt Injection)**
   - 攻击者在输入中插入恶意指令覆盖预期行为

2. **工具中毒 (Tool Poisoning)**
   - 外部工具受损返回恶意数据

3. **身份和权限滥用 (Identity & Privilege Abuse)**
   - 被盗或泄露的代理凭证

4. **内存中毒 (Memory Poisoning)**
   - 虚假信息注入代理内存

5. **供应链攻击 (Supply Chain Attacks)**
   - 代理依赖链中的组件被攻破

## Zero Trust 核心原则

| 原则 | 含义 | 实施 |
|------|------|------|
| Trust Nothing | 信任零信任 | 密码学验证所有身份 |
| Verify Everything | 验证一切 | 可观测日志，审计跟踪 |
| Assume Breach | 假设已被攻破 | 工程化防御和隔离 |
| Agent Speed | 代理速度 | 自动化威胁检测和响应 |
| Continuous Improvement | 持续改进 | 渗透测试和红队演练 |

## 合规性

本框架涵盖以下法规：

- **HIPAA**: 医疗保健数据保护
- **PCI-DSS**: 支付卡数据安全
- **SOX**: 财务报告完整性
- **FedRAMP**: 政府云安全
- **FISMA**: 联邦信息系统

## 许可证

本项目采用MIT许可证 - 详见 [LICENSE](LICENSE) 文件

## 联系和支持

- 📧 提出问题和建议: [Issues](https://github.com/yourusername/agent-security-skill/issues)
- 💬 讨论和社区: [Discussions](https://github.com/yourusername/agent-security-skill/discussions)
- 🔗 参考: [Anthropic Security Resources](https://www.anthropic.com/product/security)

---

**最后更新**: 2026年6月26日  
**版本**: 1.0  
**维护者**: agent-security-skill 社区
