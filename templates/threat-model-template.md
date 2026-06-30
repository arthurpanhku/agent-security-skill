# Agent Threat Model — `<system name>`

**System:** `<name>` · **Owner:** `<team>` · **Date:** `<YYYY-MM-DD>` · **Tier target:** ☐ Foundation ☐ Advanced ☐ Optimized

## 1. Scope & data-flow
- Agents in scope: `____`
- Tools / MCP servers reachable: `____`
- Sensitive data the agent can touch: `____`
- Untrusted-content sources: `____`
- External egress channels: `____`

> Then complete [lethal-trifecta-assessment.md](lethal-trifecta-assessment.md) for each agent.

## 2. Threat walkthrough

For each threat: is it applicable, what's the current control, what's the gap?

| Threat | Applicable? | Current control | Gap / action | Std ref |
|--------|-------------|-----------------|--------------|---------|
| **Prompt injection** (esp. indirect) | ☐ | | architectural — least-priv, isolation, egress control | OWASP LLM01; CaMeL; Dual-LLM |
| **Tool poisoning / MCP** | ☐ | | vet & pin; treat tool descs as untrusted | OWASP Agentic |
| **Identity & privilege abuse** | ☐ | | scoped, short-lived creds; mTLS | MITRE ATLAS |
| **Memory poisoning** | ☐ | | provenance + integrity checks | OWASP Agentic |
| **Supply chain** | ☐ | | pin/vet models, tools, pipelines; SBOM | OWASP LLM03/05 |

> Reminder: indirect prompt injection has **no reliable detection-based fix** — rely on architecture, treat detection as defense-in-depth only.

## 3. Controls by tier (check what's in place)

**Foundation:** ☐ agent identity/auth ☐ tool-access logging ☐ input validation ☐ ACLs
**Advanced:** ☐ mTLS identity ☐ task-scoped + time-limited perms ☐ memory isolation ☐ behavioral anomaly detection
**Optimized:** ☐ continuous verification ☐ context-aware perms ☐ memory-integrity detection ☐ supply-chain verification ☐ Agentic SOAR (forward-looking)

## 4. Validation
- ☐ Defenses tested empirically (AgentDojo / red-team) — link: `____`
- ☐ High-impact actions gated by human-in-the-loop
- ☐ Logging + alerting verified end-to-end

## 5. Compliance overlay (if applicable)
☐ HIPAA (PHI isolation, 6yr audit) ☐ PCI-DSS / SOX (cardholder isolation, txn verification) ☐ FedRAMP / FISMA (FIPS 199, ATO)

## 6. Sign-off
Residual risks accepted by: `____` Date: `____`

*Framework: [../zero-trust-for-ai-agents.md](../zero-trust-for-ai-agents.md)*
