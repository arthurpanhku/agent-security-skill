# Agent Security Skill

## Overview

Agent Security Skill 是一个全面的资源库，汇集关于如何保护和加固 AI 代理系统的企业级安全框架、研究报告和最佳实践。

## What This Skill Does

### 核心功能

1. **Zero Trust Framework Reference**
   - 三层安全架构（Foundation, Advanced, Optimized）
   - 八阶段实现工作流
   - Agentic SOAR 自动化防御机制

2. **Threat Intelligence**
   - 提示词注入攻击分析
   - 工具中毒检测和防护
   - 身份和权限滥用预防
   - 内存安全保护
   - 供应链风险管理

3. **Compliance Guidance**
   - HIPAA（医疗保健）
   - PCI-DSS（支付卡）
   - SOX（财务报告）
   - FedRAMP 和 FISMA（政府）

4. **Implementation Roadmap**
   - 快速实施指南
   - 分阶段部署策略
   - 成功指标和检查清单

## Key Features

✅ **企业级框架** - 基于 Anthropic 官方安全研究  
✅ **可实施的指导** - 具体的实现步骤和时间表  
✅ **威胁分析** - 深入的攻击向量和防御机制  
✅ **合规对齐** - 针对不同行业的规制要求  
✅ **最佳实践** - 来自安全专家的建议  
✅ **持续更新** - 随着威胁景观演变而更新  

## Use Cases

### For Security Leaders
- 制定企业 AI 代理安全政策
- 评估当前安全姿态
- 规划安全投资
- 实现合规性框架

### For Technical Teams
- 设计安全的代理架构
- 实施访问控制和隔离
- 部署监控和检测
- 建立事件响应流程

### For Organizations
- 理解 AI 代理风险
- 建立安全文化
- 培训团队
- 评估第三方工具

## Key Resources

### 主要内容

- **zero-trust-for-ai-agents.md** - 核心 Zero Trust 框架（268 行）
  - 安全考虑
  - 威胁景观
  - 三层架构
  - 实施工作流
  - Agentic SOAR
  - 合规指南

### 相关标准

- NIST Cybersecurity Framework
- Zero Trust Architecture 原则
- OWASP Top 10 for LLM Applications

## Quick Implementation Timeline

### Week 1-4: Foundation Tier
- 代理身份和认证
- 工具访问日志
- 提示词注入检测

### Month 2-3: Advanced Tier
- 密码学身份
- 任务范围权限
- 行为检测

### Month 3-6: Optimized Tier
- 自动威胁响应
- Agentic SOAR
- 供应链验证

## Zero Trust Core Principles

| 原则 | 实施 |
|------|------|
| Trust Nothing | 密码学验证所有身份 |
| Verify Everything | 完整的操作日志和审计 |
| Assume Breach | 隔离和防御机制 |
| Agent Speed | 自动化响应系统 |
| Continuous Improvement | 定期评估和更新 |

## Threat Landscape Coverage

1. **Prompt Injection Attacks** - 输入验证和检测
2. **Tool Poisoning** - 数据验证和隔离
3. **Identity & Privilege Abuse** - 密码学身份
4. **Memory Poisoning** - 内存保护
5. **Supply Chain Attacks** - 依赖链验证

## Compliance Frameworks

### Healthcare (HIPAA)
- PHI 隔离
- 审计跟踪（6+ 年）
- 同意管理

### Financial Services (PCI-DSS, SOX)
- 卡数据隔离
- 交易验证
- 访问控制

### Government (FedRAMP, FISMA)
- FIPS 199 分类
- ATO 对齐
- 供应链管理

## How to Use This Skill

### Step 1: Understand Your Current State
- Review current agent deployments
- Identify security gaps
- Assess compliance requirements

### Step 2: Choose Your Tier
- **Foundation**: 基本保护，2-4 周
- **Advanced**: 生产级别，2-3 个月
- **Optimized**: 企业级别，3-6 个月

### Step 3: Follow Implementation Workflow
1. Identity & Cryptographic Verification
2. Tool Access Scoping
3. Sandboxing & Isolation
4. Input/Output Controls
5. Memory Safeguards
6. Logging & Monitoring
7. Threat Detection & Response
8. Continuous Improvement

### Step 4: Implement and Monitor
- Deploy controls progressively
- Monitor effectiveness
- Adjust based on findings
- Update regularly

## Integration Points

This skill complements:
- Claude Security products
- Enterprise security frameworks
- Compliance management systems
- Threat intelligence platforms
- SIEM/SOC solutions

## Updates and Maintenance

This skill is maintained as the threat landscape evolves:
- Regular security research integration
- Emerging threat updates
- Best practice enhancements
- Compliance standard updates

## Support and Community

- 📚 Documentation: Full guides and references
- 💬 Community: Share implementations and learn
- 🔗 Resources: Links to official frameworks
- 📖 References: Research citations

## Version History

- **v1.0** (June 26, 2026) - Initial release
  - Zero Trust framework
  - Implementation guide
  - Compliance mapping

## License

MIT License - See LICENSE file for details

---

**Last Updated**: June 26, 2026  
**Maintained by**: agent-security-skill Community  
**Based on**: Anthropic's Zero Trust for AI Agents Enterprise Framework
