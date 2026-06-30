# LLM Providers & Tech-Giant Agent-Security Sources

A curated catalog of **first-party** AI-agent security material from the major LLM providers and technology companies — their frameworks, guardrail products, and open red-team tooling. It complements [references-and-frameworks.md](references-and-frameworks.md) (standards + academic work) by focusing on what each vendor publishes and ships.

> **About this project**: This is the **self-directed research project of a master's student at the University of Hong Kong (HKU)** — independent, non-commercial, and not officially affiliated with any vendor below. It is **open to contributions** from academia, industry, and the wider community. Corrections, additions, and verified new sources are welcome via [Issues](https://github.com/arthurpanhku/agent-security-skill/issues) and Pull Requests — see [CONTRIBUTING.md](CONTRIBUTING.md).

> **Verification note**: Every link below was searched and title-/scope-checked on **2026-06-30**. These are vendor properties whose CDN/doc paths drift over time — treat the **vendor + document title** as authoritative and re-check URLs before relying on them. Listing a vendor's tooling here is *cataloguing*, not endorsement.

---

## 1. Frontier-model / LLM providers

| Provider | Resource | What it is / why it matters | Link |
|----------|----------|------------------------------|------|
| **Anthropic** | Zero Trust for AI Agents | The enterprise framework this project is built on | https://claude.com/blog/zero-trust-for-ai-agents |
| **Anthropic** | Claude Security (product) | Vendor view of agent security tooling & posture | https://www.anthropic.com/product/security |
| **OpenAI** | Practices for Governing Agentic AI Systems (2023) | Governance + human-confirmation model for high-impact agent actions | https://cdn.openai.com/papers/practices-for-governing-agentic-ai-systems.pdf |
| **OpenAI** | Safety best practices (API docs) | Moderation, adversarial testing, human oversight, prompt hardening | https://developers.openai.com/api/docs/guides/safety-best-practices |
| **OpenAI** | Safety in building agents (Agent Builder) | Agent-/MCP-specific risks + tool-approval guidance | https://developers.openai.com/api/docs/guides/agent-builder-safety/ |
| **Google** | Secure AI Framework (SAIF / SAIF 2.0) | Earliest systematic vendor framework; 2.0 adds agent-specific risks & controls | https://saif.google/ |
| **Google DeepMind** | Frontier Safety Framework | Protocols for severe-harm capabilities, incl. autonomous LLM agents | https://deepmind.google/blog/introducing-the-frontier-safety-framework/ |
| **Google DeepMind** | Updating the Frontier Safety Framework | Latest revision (risk domains incl. cybersecurity, deceptive alignment) | https://deepmind.google/blog/updating-the-frontier-safety-framework/ |
| **Google** | How we're securing the AI frontier | Cross-org security strategy + tooling overview | https://blog.google/innovation-and-ai/technology/safety-security/ai-security-frontier-strategy-tools/ |
| **Meta** | Purple Llama (announcement) | Umbrella open trust-&-safety project | https://ai.meta.com/blog/purple-llama-open-trust-safety-generative-ai/ |
| **Meta** | Llama Protections (Llama Guard / Prompt Guard) | Input/output safeguard + prompt-injection classifier models | https://www.llama.com/llama-protections/ |
| **Meta** | CyberSecEval | Benchmark suite for insecure-code / prompt-injection / cyber-capability | https://meta-llama.github.io/PurpleLlama/CyberSecEval/ |
| **Microsoft** | Taxonomy of Failure Modes in Agentic AI Systems (AI Red Team) | The most systematic engineering breakdown of agent failure/abuse modes | https://www.microsoft.com/en-us/security/blog/ (search title — AI Red Team) |

## 2. Cloud & infrastructure platforms (guardrails + tooling)

| Provider | Resource | What it is / why it matters | Link |
|----------|----------|------------------------------|------|
| **AWS** | Bedrock Guardrails | Configurable safeguards: prompt-attack, PII, denied topics, grounding | https://aws.amazon.com/bedrock/guardrails/ |
| **AWS** | Guardrails for agentic AI (`InvokeGuardrailChecks`) | Per-step, resourceless safeguard checks inside an agent loop | https://aws.amazon.com/blogs/machine-learning/safeguard-your-agentic-ai-applications-with-the-amazon-bedrock-guardrails-invokeguardrailchecks-api/ |
| **AWS** | Prescriptive Guidance: Agentic AI Security | Input validation & defense-in-depth patterns for agents on AWS | https://docs.aws.amazon.com/prescriptive-guidance/latest/agentic-ai-security/ |
| **NVIDIA** | NeMo Guardrails | Open-source programmable rails between app code and the LLM | https://github.com/NVIDIA-NeMo/Guardrails |
| **NVIDIA** | Safeguard Agentic AI (NVIDIA Safety Recipe) | Reference recipe combining guardrails + eval for agents | https://developer.nvidia.com/blog/safeguard-agentic-ai-systems-with-the-nvidia-safety-recipe/ |
| **IBM** | Granite Guardian | Risk-detection models incl. jailbreak + agentic function-call checks | https://www.ibm.com/granite/docs/models/guardian |
| **Microsoft** | Azure / Copilot security guidance | Platform guardrails + responsible-AI controls (see PyRIT below for tooling) | https://www.microsoft.com/en-us/security/blog/ |

## 3. Open-source red-team & guardrail tooling

| Tool | Owner | What it does | Link |
|------|-------|--------------|------|
| **PyRIT** | Microsoft AI Red Team | Python Risk Identification Tool — automated red-teaming of GenAI/agents | https://github.com/microsoft/PyRIT |
| **garak** | NVIDIA | LLM vulnerability scanner (prompt injection, jailbreak, leakage probes) | https://github.com/NVIDIA/garak |
| **NeMo Guardrails** | NVIDIA | Programmable runtime guardrails toolkit | https://github.com/NVIDIA-NeMo/Guardrails |
| **Purple Llama / CyberSecEval** | Meta | Safety/security evals + Llama Guard / Prompt Guard models | https://github.com/meta-llama/PurpleLlama |
| **Granite Guardian** | IBM | Open guardian models (Apache-2.0) for prompt/response/tool-call risk | https://github.com/ibm-granite/granite-guardian |
| **AgentDojo** | Debenedetti et al. | Benchmark to empirically test agent prompt-injection defenses | https://arxiv.org/abs/2406.13352 |

## 4. Dedicated AI-security vendors (agent runtime)

| Vendor | Resource | What it is / why it matters | Link |
|--------|----------|------------------------------|------|
| **Cisco** | AI Defense | Runtime inspection of LLM/MCP traffic; agent-threat detection (memory poisoning, tool misuse, intent hijacking) | https://www.cisco.com/site/us/en/products/security/ai-defense/index.html |
| **Cisco** | Securing AI Agents with AI Defense (blog) | MCP scanning + runtime guardrails + adaptive red-teaming | https://blogs.cisco.com/ai/securing-ai-agents-with-cisco-ai-defense |

## 5. Standards & community bodies

These overlap with [references-and-frameworks.md](references-and-frameworks.md) — included here for completeness of the "where the guidance comes from" map.

| Body | Resource | Link |
|------|----------|------|
| **NIST** | AI Risk Management Framework (AI RMF 1.0) | https://www.nist.gov/itl/ai-risk-management-framework |
| **NIST** | Generative AI Profile (AI 600-1) | https://nvlpubs.nist.gov/nistpubs/ai/NIST.AI.600-1.pdf |
| **MITRE** | ATLAS (adversarial threat landscape for AI) | https://atlas.mitre.org/ |
| **OWASP** | Top 10 for LLM Applications | https://genai.owasp.org/llm-top-10/ |
| **OWASP** | Agentic AI – Threats and Mitigations | https://genai.owasp.org/resource/agentic-ai-threats-and-mitigations/ |
| **Cloud Security Alliance** | MAESTRO – Agentic AI threat-modeling framework | https://cloudsecurityalliance.org/blog/2025/02/06/agentic-ai-threat-modeling-framework-maestro |
| **Cloud Security Alliance** | MAESTRO (repo) | https://github.com/CloudSecurityAlliance/MAESTRO |

---

## How to use this catalog

- **Building an agent?** Start with your platform's row in §1–2 (Anthropic / OpenAI / Google / AWS / Azure) for the controls you already have access to, then layer the architectural defenses in [zero-trust-for-ai-agents.md](zero-trust-for-ai-agents.md).
- **Testing defenses?** Use §3 — `garak` + `PyRIT` for probing, **AgentDojo** for measuring injection resistance. Detection tooling (Llama Guard, Prompt Guard, Granite Guardian, NeMo Guardrails) is a *supplementary* layer, never the primary control.
- **Mapping to standards?** Use §5 to translate findings into NIST / MITRE ATLAS / OWASP vocabulary for audit defensibility.

---

**Last verified**: 2026-06-30 · Contributions welcome — open an Issue or PR.
