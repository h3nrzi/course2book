# Establish Agent Skill runtime capabilities and constraints

Type: research
Labels: wayfinder:research
Status: resolved
Mode: AFK
Blocked by: None
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P18, P24–P26; C7; AC-M01-09

## Question

What do current official documentation and the installed environment actually support for repository-local Agent Skills in the initial Codex workflow?

Establish facts about discovery and invocation, input/output handling, context and long-running work, tool permissions, delegation and isolation, manual intervention, and recording enough execution context to resume. Distinguish documented guarantees, locally observed behavior, and unsupported assumptions; identify versions or dates where material. Inspect the installed engineering skills as discovery tools, without treating them as the production architecture.

The result is a cited evidence record with implications and limitations, not a choice of orchestration framework, skill count, or production implementation. Use official sources and inspect local capabilities; do not ask the user to supply discoverable facts. No private course content is needed.

## Answer

Resolved on 2026-10-18 through AFK primary-source research and safe local inspection. The canonical factual record is [Agent Skill runtime evidence for M01](https://github.com/h3nrzi/course2book/blob/d81881334e270c389b36b71652b497eb3be8bfc3/.scratch/m01-technical-discovery/research/agent-skill-runtime-evidence.md), published on the throwaway `research/agent-skill-runtime-evidence` branch at commit `d81881334e270c389b36b71652b497eb3be8bfc3`. No PR was opened and the research branch was not merged.

### Findings and limits

- Official documentation supports repository-local skills, explicit and implicit invocation, progressive instruction loading, optional scripts/references, native session continuation, and optional structured CLI output. The evidence distinguishes current documentation from installed-client observations and untested assumptions.
- Safe probes observed `codex-cli 0.163.0`. This session exposes usable Context7/web retrieval and shared-filesystem collaboration with four total agent slots. Those observations are specific to this environment; the installed CLI is not assumed to be the active chat runtime.
- Skill instructions do not establish enforced domain input/output contracts, immutable Approved Lessons, persisted human approval, stale-evidence detection, rollback, exactly-once execution, or identical regenerated prose. Native continuation, tool approval, structured final output, and explicit filesystem isolation are separate capabilities; none substitutes for those M01 semantics.
- Installed engineering skills were inspected as discovery tools. Their references to a dedicated Skill tool and `disable-model-invocation` frontmatter are not established Codex runtime guarantees. The evidence identifies documented alternatives without selecting a production mechanism.

### Consequences for the map

Repository-local skills remain a supported basis for the PRD's initial coding-agent workflow. The record establishes the factual prerequisites; it does not select orchestration, skill count, artifact contracts, permissions, or recovery policy. Those choices remain with the existing human-in-the-loop tickets. This research required no human product decision and changes no PRD behavior.

Reviewed the complete evidence asset for question coverage, source attribution, privacy, relative links, and the distinction between facts and policy. Documentation retrieval and version/help probes succeeded; no production workflow or end-to-end M01 acceptance was exercised. Runtime updates and changed tools or permissions require rechecking the affected observations.

The newly precise questions fit existing artifact, research, workflow, and recovery tickets. No new blocking capability failure was discovered, so no fog was graduated and no dependency or scope change was needed. The broader discovery map remains open.
