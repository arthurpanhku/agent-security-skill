# Threat → Control Crosswalk (the "Rosetta Stone")

The agent-security field is fragmented across **6+ overlapping vocabularies** (OWASP LLM Top 10, OWASP Agentic, MITRE ATLAS, CSA MAESTRO, Microsoft's failure-mode taxonomy) **plus** governance standards (ISO/IEC 42001, NIST AI RMF). An engineer's "tool poisoning", an auditor's ISO 42001 Annex A control, and a red-teamer's ATLAS technique are *the same risk in three languages* — and today that translation is done by hand, inconsistently.

This document is a **vendor-neutral translation layer**: for each canonical agent-security threat it maps **across the taxonomies → to governance-standard controls → to a concrete technical control → to how you validate it**.

> **Status: SKELETON / work in progress.** Threats **T1** and **T6** are worked as exemplars; **T2–T5** are scaffolded for completion. Contributions welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

> **Project**: a self-directed research project of a master's student at the University of Hong Kong (HKU) — independent, non-commercial, open to contributions.

---

## How to read this

Every mapping cell carries a **provenance marker** so this stays honest and citable:

| Marker | Meaning |
|:------:|---------|
| ✓ | Established, stable identifier (e.g. OWASP `LLM01`) — verified against the primary source |
| ~ | **Thematic** mapping — no official 1:1 code exists; aligned by concept |
| ⚠ | Exact identifier **to be verified** against the primary source before citing |

Framework definitions and links live in [references-and-frameworks.md](references-and-frameworks.md) and [vendor-security-sources.md](vendor-security-sources.md). Canonical threats follow [zero-trust-for-ai-agents.md](zero-trust-for-ai-agents.md#threat-landscape).

**Verification note**: standard identifiers (ATLAS technique IDs, OWASP `ASI` numbers, ISO 42001 Annex A sub-controls, NIST AI RMF action IDs) drift between revisions. Treat the **framework + theme** as authoritative and re-check exact codes at the primary source. Last structural check: **2026-06-30**.

---

## At-a-glance matrix

| # | Canonical threat | OWASP LLM 2025 | OWASP Agentic 2026 | MITRE ATLAS (theme) | ISO 42001 Annex A (objective) | Primary technical control |
|:--:|------------------|:--------------:|:------------------:|---------------------|-------------------------------|---------------------------|
| **T1** | Prompt Injection (incl. indirect) | `LLM01` ✓ | Goal hijack / prompt injection ⚠ | Prompt injection / LLM-based attack ~ | A.6 Data · A.8 Responsible use ~ | Untrusted-content isolation + egress control |
| **T2** | Tool Poisoning | `LLM01`/`LLM05` ~ | Tool misuse & exploitation ⚠ | Tool / plugin compromise ~ | A.5 Lifecycle · A.9 Third-party ~ | Treat tool I/O as untrusted; output validation |
| **T3** | Identity & Privilege Abuse | excessive-agency ~ | Identity & privilege abuse ⚠ | Privilege escalation / lateral movement ~ | A.3 Internal org · A.8 ~ | Scoped, short-lived creds; mTLS |
| **T4** | Memory Poisoning | data-poisoning ~ | (agentic — memory) ⚠ | Data / model poisoning ~ | A.6 Data ~ | Memory provenance + integrity checks |
| **T5** | Supply Chain | `LLM03`/`LLM05` ~ | (agentic — supply chain) ⚠ | ML supply-chain compromise ~ | A.4 Resources · A.9 Third-party ~ | Pin/vet/SBOM for models, tools, pipelines |
| **T6** | MCP & Tool Supply-Chain | `LLM01`/`LLM05` ~ | Tool misuse / rogue components ⚠ | Supply-chain / tooling ~ | A.5 Lifecycle · A.9 Third-party ~ | MCP vetting + least-privilege tokens + HITL |

> ⚠ The OWASP **Agentic** (`ASIxx:2026`) numbers are intentionally left as themes here pending a line-by-line check against the official list — see [open items](#open-items).

---

## T1 — Prompt Injection (including indirect) — *worked exemplar*

**Definition**: malicious instructions inserted into inputs or external data the agent reads, overriding intended behavior. **Indirect** injection (instructions hidden in fetched web pages, documents, tool output, other agents' messages) has **no reliable detection-based fix** — defense is architectural.

### Standards crosswalk

| Framework | Identifier / label | Prov. | Note |
|-----------|--------------------|:-----:|------|
| OWASP LLM Top 10 (2025) | `LLM01: Prompt Injection` | ✓ | The anchor risk |
| OWASP Agentic (2026) | Agent goal hijack / prompt injection | ⚠ | Confirm exact `ASI` number at source |
| MITRE ATLAS | Prompt injection / LLM-based attack (technique) | ~ | Map to specific `AML.T####` when citing |
| CSA MAESTRO | Cross-layer; esp. *untrusted input* into the reasoning layer | ~ | |
| Microsoft taxonomy | Indirect prompt injection / instruction-following failure | ~ | |
| ISO/IEC 42001 Annex A | A.6 (data for AI) · A.8 (responsible use) · A.5 (lifecycle controls) | ~ | Verify sub-controls; treat as risk-treatment input |
| NIST AI RMF / GenAI Profile | MANAGE + MEASURE functions (GenAI Profile actions) | ~ | Confirm action IDs |

### Technical controls (this skill)

- **Cut the lethal trifecta** — [templates/lethal-trifecta-assessment.md](templates/lethal-trifecta-assessment.md)
- **Egress control** (default-deny outbound) — [templates/egress-allowlist.example.yaml](templates/egress-allowlist.example.yaml)
- **Architectural patterns** — Dual-LLM, CaMeL, provenance labeling — see [zero-trust-for-ai-agents.md](zero-trust-for-ai-agents.md#defending-against-prompt-injection-architecture-over-detection)
- Detection (classifiers, canaries) = **supplementary only**

### Validation

- Run **AgentDojo** against the agent config to measure injection resistance empirically
- Red-team with **garak** / **PyRIT** (see [vendor-security-sources.md](vendor-security-sources.md))
- Confirm: removing any one trifecta leg breaks the exfiltration path

---

## T6 — MCP & Tool Supply-Chain Threats — *worked exemplar*

**Definition**: risks from the tools/servers an agent connects to (increasingly via MCP), where the tool surface itself is attacker-controllable: tool-description poisoning, rug pulls, confused deputy, token/credential theft, cross-server shadowing.

### Standards crosswalk

| Framework | Identifier / label | Prov. | Note |
|-----------|--------------------|:-----:|------|
| OWASP LLM Top 10 (2025) | `LLM01` (poisoned descriptions as input) · `LLM05` (supply chain) | ~ | |
| OWASP Agentic (2026) | Tool misuse & exploitation / rogue components | ⚠ | Confirm exact `ASI` number(s) |
| MITRE ATLAS | Supply-chain / tooling compromise | ~ | |
| CSA MAESTRO | Tooling & ecosystem layer; third-party trust boundary | ~ | |
| Microsoft taxonomy | Tool/skill compromise; confused-deputy failure modes | ~ | |
| ISO/IEC 42001 Annex A | A.9 (third-party & customer relationships) · A.5 (lifecycle) | ~ | Strong fit — vendor/tool governance |
| NIST AI RMF / GenAI Profile | GOVERN (third-party) + MAP functions | ~ | |

### Technical controls (this skill)

- **MCP server vetting before approval** — [templates/mcp-server-vetting-checklist.md](templates/mcp-server-vetting-checklist.md)
- Treat tool **names/descriptions/schemas as untrusted input**
- Pin versions; require re-approval on change (rug-pull defense)
- Least-privilege, short-lived scoped tokens (confused-deputy / token-theft defense)
- Human-in-the-loop for new or changed tools; log every invocation

### Validation

- Re-run the vetting checklist on every tool/description change
- Audit token scope and lifetime per MCP server
- Test cross-server shadowing in a sandbox before production

---

## T2 — Tool Poisoning — *scaffold*

**Definition**: compromised external tools return malicious data or hidden instructions; subtle data corruption.

### Standards crosswalk

| Framework | Identifier / label | Prov. | Note |
|-----------|--------------------|:-----:|------|
| OWASP LLM Top 10 (2025) | `LLM01` / `LLM05` | ~ | TODO: confirm primary mapping |
| OWASP Agentic (2026) | Tool misuse & exploitation | ⚠ | TODO: `ASI` number |
| MITRE ATLAS | _TODO_ | ⚠ | |
| CSA MAESTRO | _TODO (layer)_ | ⚠ | |
| Microsoft taxonomy | _TODO_ | ⚠ | |
| ISO/IEC 42001 Annex A | A.5 · A.9 | ~ | TODO: sub-controls |
| NIST AI RMF / GenAI Profile | _TODO (function)_ | ⚠ | |

### Technical controls
- Output validation / sanitization of tool responses; isolation. _TODO: link template/section._

### Validation
- _TODO: how to test (e.g. inject canary in tool output, confirm it isn't followed)._

---

## T3 — Identity & Privilege Abuse — *scaffold*

**Definition**: stolen/compromised agent credentials, lateral movement, privilege escalation through legitimate paths.

### Standards crosswalk

| Framework | Identifier / label | Prov. | Note |
|-----------|--------------------|:-----:|------|
| OWASP LLM Top 10 (2025) | excessive agency (adjacent) | ~ | TODO confirm |
| OWASP Agentic (2026) | Identity & privilege abuse | ⚠ | TODO: `ASI` number |
| MITRE ATLAS | Privilege escalation / lateral movement | ~ | |
| CSA MAESTRO | _TODO (layer)_ | ⚠ | |
| Microsoft taxonomy | _TODO_ | ⚠ | |
| ISO/IEC 42001 Annex A | A.3 · A.8 | ~ | TODO sub-controls |
| NIST AI RMF / GenAI Profile | _TODO_ | ⚠ | |

### Technical controls
- Scoped, short-lived credentials; mTLS agent identity; ACLs. _TODO: link 8-phase Phase 1/2._

### Validation
- _TODO: credential-scope audit; attempt lateral movement in sandbox._

---

## T4 — Memory Poisoning — *scaffold*

**Definition**: false information injected into agent memory — manipulated history, corrupted persistent state, contradictory memories.

### Standards crosswalk

| Framework | Identifier / label | Prov. | Note |
|-----------|--------------------|:-----:|------|
| OWASP LLM Top 10 (2025) | data poisoning (adjacent) | ~ | TODO |
| OWASP Agentic (2026) | (agentic — memory) | ⚠ | TODO: `ASI` number |
| MITRE ATLAS | Data / model poisoning | ~ | |
| CSA MAESTRO | _TODO (layer)_ | ⚠ | |
| Microsoft taxonomy | _TODO_ | ⚠ | |
| ISO/IEC 42001 Annex A | A.6 (data) | ~ | TODO sub-controls |
| NIST AI RMF / GenAI Profile | _TODO_ | ⚠ | |

### Technical controls
- Memory provenance, integrity checks, isolation. _TODO: link 8-phase Phase 5._

### Validation
- _TODO: integrity check / poisoned-memory detection test._

---

## T5 — Supply Chain Attacks — *scaffold*

**Definition**: compromise of components in the agent dependency chain — models, third-party tools, infra/deployment, dev pipelines.

### Standards crosswalk

| Framework | Identifier / label | Prov. | Note |
|-----------|--------------------|:-----:|------|
| OWASP LLM Top 10 (2025) | `LLM03` / `LLM05` | ~ | TODO confirm |
| OWASP Agentic (2026) | (agentic — supply chain) | ⚠ | TODO: `ASI` number |
| MITRE ATLAS | ML supply-chain compromise | ~ | |
| CSA MAESTRO | _TODO (layer)_ | ⚠ | |
| Microsoft taxonomy | _TODO_ | ⚠ | |
| ISO/IEC 42001 Annex A | A.4 (resources) · A.9 (third-party) | ~ | TODO sub-controls |
| NIST AI RMF / GenAI Profile | GOVERN (third-party) | ~ | |

### Technical controls
- Pin and vet models/tools; SBOM for tools & models; provenance. _TODO: link template/section._

### Validation
- _TODO: dependency inventory + integrity verification._

---

## Open items

- [ ] Verify every OWASP **Agentic `ASIxx:2026`** number against the official list and replace ⚠ with ✓
- [ ] Pin **MITRE ATLAS** technique IDs (`AML.T####`) per threat
- [ ] Map to specific **ISO/IEC 42001 Annex A** sub-controls (38 controls across A.2–A.10), not just objectives
- [ ] Add **NIST AI RMF / GenAI Profile (AI 600-1)** action IDs
- [ ] Add **CSA MAESTRO** layer per threat
- [ ] Complete scaffolds **T2–T5**
- [ ] Optional: add a machine-readable version (`crosswalk.csv` / `.json`) for tooling
- [ ] Optional: empirical column — observed prevalence from a small MCP-server / agent-config study

---

**Last structural check**: 2026-06-30 · Contributions welcome — open an Issue or PR.
