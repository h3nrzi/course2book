# Choose independent code example generation and verification

Type: grilling
Labels: wayfinder:grilling
Mode: HITL
Blocked by: 06, 07
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P12, P17, P19; C2–C3; AC-M01-03–AC-M01-04, AC-M01-06

## Question

What makes an independently authored code example acceptable, and what verification evidence must accompany it before lesson review?

Compare executable checks, compilation or type checks, static inspection, and documented manual review according to the example and available environment. Investigate practical verification capabilities before recommending a minimum policy. Address version/dependency context, intended behavior, incomplete illustrative snippets, unsafe or unavailable execution environments, and explicit distinction between verified behavior and unresolved limitations.

Preserve the PRD's permission to teach from transcripts without instructor source code; independent examples must never be represented as recovered instructor code. Resolve ownership, verification claims, and escalation when checks cannot run.

Do not preselect one language, require a universal execution service, install production dependencies, or implement examples and test runners during discovery.

## Dependency rationale

- [Choose educational authorship and approved course context](06-educational-authorship-continuity.md): The authoring contract defines the role and scope of independent examples.
- [Choose technical research, version evidence, and enrichment provenance](07-technical-research-policy.md): The research policy supplies the version and external-claim evidence contract used to assess examples.

Runtime evidence is already a prerequisite of the research policy; it also constrains feasible example verification.
