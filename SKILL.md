---
name: agent-security
description: >-
  Security guidance and ready-to-use templates for hardening AI agent and
  MCP-based systems against prompt injection, tool poisoning, identity/privilege
  abuse, memory poisoning, and supply-chain attacks. Use when reviewing or
  designing an AI agent or MCP server configuration, threat-modeling an agentic
  system, assessing the "lethal trifecta" / prompt-injection exposure, applying
  Zero Trust tiers to agents, vetting a new MCP server/tool, or mapping agent
  risks to compliance frameworks (HIPAA, PCI-DSS, SOX, FedRAMP, FISMA).
license: MIT
metadata:
  project: "HKU master's-student self-research project — open to contributions"
  based_on: "Anthropic — Zero Trust for AI Agents"
  version: "1.1"
---

# Agent Security

Apply enterprise Zero Trust principles to AI agent and MCP systems. The core
stance: **prompt injection (especially indirect) has no reliable detection-based
fix — defend with architecture, not filters.** Limit what a compromised agent can
*do*; treat detection as defense-in-depth only.

## When to use this skill

- Reviewing or designing an AI agent / MCP server configuration for security
- Threat-modeling an agentic system or multi-agent workflow
- Checking whether an agent is exposed to the **lethal trifecta** (private data +
  untrusted content + external egress)
- Vetting a new or changed MCP server / tool before approval
- Choosing a Zero Trust tier and implementation phase
- Mapping agent risks to compliance (HIPAA, PCI-DSS, SOX, FedRAMP, FISMA)

## How to use it

1. **Read the framework** in [zero-trust-for-ai-agents.md](zero-trust-for-ai-agents.md)
   — threat landscape, the lethal trifecta, architectural defense patterns
   (Dual-LLM, CaMeL, egress control), 3 tiers, 8-phase workflow, compliance.
2. **Produce an artifact** using the bundled templates — copy and fill in:
   - [templates/threat-model-template.md](templates/threat-model-template.md) — full agent threat model
   - [templates/lethal-trifecta-assessment.md](templates/lethal-trifecta-assessment.md) — fast per-agent exfiltration check
   - [templates/mcp-server-vetting-checklist.md](templates/mcp-server-vetting-checklist.md) — vet an MCP server/tool
   - [templates/egress-allowlist.example.yaml](templates/egress-allowlist.example.yaml) — sample default-deny egress config
3. **Validate empirically** — don't assume coverage. Test defenses with an agent
   benchmark like **AgentDojo**, and red-team with tooling listed in
   [vendor-security-sources.md](vendor-security-sources.md) (PyRIT, garak).
4. **Cross-reference** to standard vocabularies (OWASP LLM Top 10, MITRE ATLAS)
   via [references-and-frameworks.md](references-and-frameworks.md).

## Decision shortcuts

- **"Is this agent dangerous?"** → run the lethal-trifecta assessment. All three
  legs present = exfiltration risk; cut at least one (usually egress or untrusted-
  content isolation).
- **"Can I add this MCP server?"** → run the MCP vetting checklist. Treat tool
  names/descriptions as untrusted; pin versions; require re-approval on change.
- **"Where do I start?"** → Foundation tier (2–4 wks): agent identity, tool-access
  logging, input validation, ACLs. Don't start with Agentic SOAR (forward-looking).

## Threats covered

Prompt injection · Tool poisoning · MCP / tool supply-chain (rug-pull, confused
deputy, token theft, cross-server shadowing) · Identity & privilege abuse ·
Memory poisoning · Supply-chain attacks.

## Core principles

| Principle | Implementation |
|-----------|----------------|
| Trust Nothing | Cryptographically verify every identity |
| Verify Everything | Full operation logging + audit trail |
| Assume Breach | Engineer isolation; limit blast radius |
| Respond at Agent Speed | Automated detection/response (with human gates) |
| Improve Continuously | Pen-testing, red-teaming, benchmark validation |

---

*Part of the agent-security-skill project — a self-directed research project by a
master's student at the University of Hong Kong (HKU). Independent, non-commercial,
open to contributions. Based on Anthropic's Zero Trust for AI Agents.*
