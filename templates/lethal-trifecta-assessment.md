# Lethal Trifecta Assessment — `<agent name>`

> The single most useful agent-security heuristic (Willison, 2025): data theft requires **all three** legs at once. Remove any one leg and the exfiltration path breaks. Fill this in per agent / per tool-configuration.

**Agent:** `<name>` · **Owner:** `<team>` · **Date:** `<YYYY-MM-DD>` · **Reviewer:** `<name>`

## The three legs

| Leg | Present? | Where it comes from | Notes |
|-----|----------|---------------------|-------|
| **1. Access to private / sensitive data** | ☐ Yes ☐ No | e.g. user PII, internal DB, secrets, prior-turn context | |
| **2. Exposure to untrusted content** | ☐ Yes ☐ No | e.g. web fetch, email/docs, tool outputs, other agents, RAG corpus | |
| **3. Channel to communicate externally** | ☐ Yes ☐ No | e.g. outbound HTTP, fetched URLs, rendered images, email/send, webhooks | |

**Verdict:** All three present → **EXPOSED to exfiltration.** Two or fewer → trifecta broken (still threat-model the rest).

## Which leg to cut (pick at least one)

- ☐ **Cut leg 2 (untrusted content):** isolate / quarantine untrusted input in a separate context (see Dual-LLM pattern); never feed attacker-influenceable text into the privileged, tool-wielding agent.
- ☐ **Cut leg 3 (egress):** sandbox execution + outbound network allowlist (see [egress-allowlist.example.yaml](egress-allowlist.example.yaml)); strip auto-fetched URLs / remote images.
- ☐ **Cut leg 1 (sensitive data):** scope the agent so it never holds the sensitive data while also touching untrusted content; short-lived, task-scoped credentials.

## Residual-risk sign-off

- Chosen mitigation: `____`
- Verified empirically (e.g. AgentDojo run / manual injection test)? ☐ Yes ☐ No — link: `____`
- Accepted by: `____` Date: `____`
