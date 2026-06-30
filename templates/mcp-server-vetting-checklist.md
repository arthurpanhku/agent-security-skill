# MCP Server Vetting Checklist — `<server name>`

> Treat every MCP server — and its tool **names, descriptions, and schemas** — as **untrusted input** the model will ingest. Run this before approving a new server and re-run on any change.

**Server:** `<name / URL>` · **Maintainer:** `<who>` · **Date:** `<YYYY-MM-DD>` · **Reviewer:** `<name>`

## Provenance & supply chain
- ☐ Source is identified and trusted (first-party, or a vendor you've vetted)
- ☐ Pinned to a specific version / commit / digest (no floating `latest`)
- ☐ Tool definitions reviewed for **hidden instructions** in name/description/schema (tool-poisoning)
- ☐ Change-control in place: re-approval required when tools or descriptions change (rug-pull defense)

## Privilege & credentials
- ☐ Tokens are **least-privilege** and **short-lived** (no long-lived, over-scoped OAuth)
- ☐ Credentials scoped per-task, not shared across agents
- ☐ Server cannot act as a **confused deputy** (it can't use the agent's privileges for a third party's benefit)

## Isolation & blast radius
- ☐ Network egress from the server/tool is allowlisted (cuts exfiltration)
- ☐ One malicious server can't alter how the agent uses **another** server (cross-server shadowing)
- ☐ Consequential / irreversible actions require **human-in-the-loop** approval, preview, or dry-run

## Observability
- ☐ Every tool invocation is logged (inputs, outputs, identity, timestamp)
- ☐ Alerting on anomalous tool use / new tool appearing

## Verdict
☐ **Approved** ☐ **Approved with conditions:** `____` ☐ **Rejected:** `____`

*Refs: OWASP Agentic AI – Threats and Mitigations; Microsoft Taxonomy of Failure Modes in Agentic AI Systems. See [../vendor-security-sources.md](../vendor-security-sources.md).*
