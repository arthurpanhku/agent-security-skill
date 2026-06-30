# External Frameworks & References

This document makes the skill **vendor-neutral**. The core [zero-trust-for-ai-agents.md](zero-trust-for-ai-agents.md) is built on Anthropic's framework; the sources below cross-reference it against the major industry, government, and academic work on agent security so the guidance reflects multi-source consensus rather than a single vendor's view.

> **Verification note**: Every link below was status- and title-checked on **2026-06-26**. Sources that could not be independently verified in that pass were **deliberately excluded** to avoid citing material that may not exist (e.g., a specific "CSA MAESTRO" document and a specific standalone Google "AI agent security" paper — verify and add later if confirmed). Treat author/year/title as authoritative; re-check URLs before publishing, as vendor CDN paths change.

---

## 1. Vendor & Industry Frameworks

| Source | Document | Why it matters | Link |
|--------|----------|----------------|------|
| **Anthropic** | Zero Trust for AI Agents | The framework this skill is based on | https://claude.com/blog/zero-trust-for-ai-agents |
| **OpenAI** | Practices for Governing Agentic AI Systems (Shavit, Agarwal, Brundage et al., 2023) | Governance view + the human-confirmation / oversight model for high-impact agent actions | https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf |
| **Google** | Secure AI Framework (SAIF) | Earliest systematic vendor framework; "defense-in-depth, don't rely on the model alone" | https://saif.google/ |
| **Microsoft** | Taxonomy of Failure Modes in Agentic AI Systems (AI Red Team) | The most systematic breakdown of agent-specific failure/abuse modes; engineering-oriented | Microsoft Security Blog / AI Red Team (search by title — CDN deep-link is unstable) |
| **OWASP** | Top 10 for LLM Applications | Community consensus on the core LLM risks (LLM01 = Prompt Injection) | https://genai.owasp.org/llm-top-10/ |
| **OWASP** | Agentic AI – Threats and Mitigations | Agent-specific threat catalog and mitigations | https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/ |
| **OWASP** | Multi-Agentic System Threat Modeling Guide | Threats unique to multi-agent orchestration | https://genai.owasp.org/resource/multi-agentic-system-threat-modeling-guide-v1-0/ |

## 2. Government / Standards

| Source | Document | Why it matters | Link |
|--------|----------|----------------|------|
| **NIST** | AI Risk Management Framework (AI RMF 1.0) | The de-facto governance baseline for US-regulated deployments | https://www.nist.gov/itl/ai-risk-management-framework |
| **NIST** | Generative AI Profile (NIST AI 600-1) | GenAI-specific risk profile layered on the RMF | https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf |
| **ISO/IEC** | 42001:2023 — AI Management System (AIMS) | World's first certifiable AI management-system standard; the governance wrapper (policy, risk treatment, continual improvement) around technical controls | https://www.iso.org/standard/42001 |
| **MITRE** | ATLAS (Adversarial Threat Landscape for AI Systems) | Standardized adversarial TTP vocabulary for AI — use it to label threats | https://atlas.mitre.org/ |

## 3. Academic & Community Work

| Source | Work | Why it matters | Link |
|--------|------|----------------|------|
| **Greshake et al. (2023)** | *Not what you've signed up for: Compromising Real-World LLM-Integrated Applications with Indirect Prompt Injection* | Defined the indirect-injection threat that underpins agent risk | https://arxiv.org/abs/2302.12173 |
| **Debenedetti et al. (2024)** | *AgentDojo: A Dynamic Environment to Evaluate Prompt Injection Attacks and Defenses for LLM Agents* | The benchmark for empirically testing agent defenses | https://arxiv.org/abs/2406.13352 |
| **Debenedetti et al. (2025)** — Google DeepMind / ETH Zürich | *Defeating Prompt Injections by Design* (CaMeL) | Capability-based defense that doesn't rely on detecting the injection | https://arxiv.org/abs/2503.18813 |
| **Simon Willison (2025)** | *The Lethal Trifecta for AI Agents: private data, untrusted content, and external communication* | The most practical mental model for scoping agent risk | https://simonwillison.net/2025/Jun/16/the-lethal-trifecta/ |
| **Simon Willison (2023)** | *The Dual LLM pattern for building AI assistants that can resist prompt injection* | A concrete architecture that contains untrusted content | https://simonwillison.net/2023/Apr/25/dual-llm-pattern/ |

---

## 4. Threat → Framework Cross-Mapping

Use this to translate this skill's threat list into the standard vocabularies above. For the **expanded** crosswalk — adding CSA MAESTRO, Microsoft's taxonomy, ISO/IEC 42001 Annex A, NIST AI RMF, concrete controls, and validation methods per threat — see [threat-control-crosswalk.md](threat-control-crosswalk.md).

| This skill's threat | OWASP LLM Top 10 | MITRE ATLAS (theme) | Primary mitigation reference |
|---------------------|------------------|---------------------|------------------------------|
| Prompt Injection | LLM01: Prompt Injection | Prompt injection / LLM-based attack | CaMeL; Dual-LLM; lethal-trifecta scoping |
| Tool Poisoning / MCP | (OWASP Agentic — tool/MCP) | Supply-chain / tooling | OWASP Agentic; MS Taxonomy |
| Identity & Privilege Abuse | LLM06-adjacent (excessive agency) | Privilege escalation / lateral movement | Least privilege; scoped short-lived creds |
| Memory Poisoning | (OWASP Agentic — memory) | Data poisoning | Memory provenance & integrity checks |
| Supply Chain | LLM03 / LLM05 (supply chain) | ML supply chain compromise | Pinning, vetting, SBOM for tools/models |

---

## 5. How This Complements the Anthropic Base

The Anthropic Zero Trust framework supplies the **operating model** (tiers, phases, assume-breach posture). The sources here supply what a single-vendor framework cannot:

- **Independent threat taxonomies** (OWASP, MITRE ATLAS) for shared vocabulary and audit defensibility.
- **The honest state of prompt-injection defense** (Greshake, Willison, CaMeL, AgentDojo): it is an architecture problem, not a detection problem.
- **Governance & regulatory alignment** (NIST AI RMF / 600-1, OpenAI's governance practices) beyond any one product.

---

**Last verified**: 2026-06-26
