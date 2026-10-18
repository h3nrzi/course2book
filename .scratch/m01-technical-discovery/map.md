# Technical Discovery for M01 — Content Production

Labels: wayfinder:map

## Destination

Resolve and record all technical decisions necessary to write an implementable M01 specification, with no known blocking technical uncertainties remaining. Completion ends at readiness for specification; writing the specification and implementation tickets requires separate user approval.

## Notes

- **Authority and scope:** The user approved this destination on 2026-10-18 and confirmed no additional fixed technical constraints in the breadth check. The [approved PRD](../../docs/product/PRD.md) is authoritative for product behavior, especially M01 P01–P26, AC-M01-01–AC-M01-09, and applicable cross-cutting invariants. Reopen a product decision only by identifying a genuine conflict and proposing a PRD change for user approval.
- **Planning boundary:** This effort resolves architectural and cross-cutting questions. Prefer the simplest design that satisfies the PRD; defer reversible details that can safely be settled during specification or implementation. Candidate tools, input formats, artifact forms, role groupings, and workflow mechanisms mentioned in questions are alternatives, never approved choices.
- **Initial charting:** The destination and scope are approved; no technical decision has been resolved. Per the user's explicit instruction, leave every child ticket open, including research tickets. This overrides Wayfinder's usual automatic research dispatch during charting. No research subagents, research branches, prototypes, or production assets are started in this session.
- **Session instructions:** Use [Wayfinder](../../.agents/skills/wayfinder/SKILL.md), [Grilling](../../.agents/skills/grilling/SKILL.md), and [Domain Modeling](../../.agents/skills/domain-modeling/SKILL.md); consult [Research](../../.agents/skills/research/SKILL.md) for research tickets and [Prototype](../../.agents/skills/prototype/SKILL.md) only if a later question warrants a throwaway artifact. Read the [tracker conventions](../../docs/agents/issue-tracker.md) and [domain instructions](../../docs/agents/domain.md). Use PRD §16 vocabulary until resolved domain terms warrant a root glossary.
- **Evidence before judgment:** Investigate discoverable facts and meaningful alternatives before requesting a human choice. Present a recommended answer with rationale and trade-offs. HITL tickets require the user's actual response; do not supply it on their behalf. For library/API documentation, follow AGENTS.md's Context7-first lookup procedure. Verify runtime claims against official documentation and the installed environment.
- **Tracker operation:** Child files in `issues/` are the authoritative open-question list; this map does not duplicate them. `Type:` and matching `wayfinder:` labels select the workflow; no triage labels apply. A child without `Status:` is open and unclaimed. Claim by saving `Status: claimed` before investigation; resolve with `## Answer` and `Status: resolved`. `Blocked by:` contains local ticket numbers; all listed blockers must be resolved. Scan open, unblocked, unclaimed children in filename-number order to find the frontier.
- **Resolution records:** The child's Answer is the canonical discovery resolution and records the chosen answer, evidence, meaningful alternatives, rationale, trade-offs, human decision where required, and intentionally deferred details. Link larger evidence assets rather than pasting them. Record resolved domain meanings in `GLOSSARY.md`; use `docs/adr/` sparingly under Domain Modeling's criteria. If an ADR owns enduring rationale, link it from the Answer instead of duplicating that rationale. Add only a one-line gist and named ticket link to Decisions so far.
- **Maintain the map:** Resolve at most one non-research ticket per later session. Reassess dependencies and fog after each resolution, create newly precise questions before wiring links, and remove graduated fog. Any implementation-shaped work must remain outside this decision map. Before declaring readiness, verify every M01 requirement has an accepted technical treatment or an explicit safe deferral, and no in-scope blocking uncertainty remains.
- **Privacy:** Keep charting and research records free of proprietary transcript excerpts, generated private book text, credentials, and private material locations. The PRD's public-repository constraint applies to discovery assets as well as production.

## Decisions so far

- [Establish Agent Skill runtime capabilities and constraints](issues/01-agent-skill-runtime-evidence.md): Documented and observed runtime capabilities support repository-local skills; domain contracts, approval preservation, and recovery guarantees remain project decisions.
- [Establish transcript format and preservation constraints](issues/02-transcript-format-evidence.md): Compared plain text, SRT, and WebVTT preservation limits; initial support remains undecided and actual corpus behavior is unobserved.

## Not yet specified

- Corpus-specific exceptions beyond the generic intake and fidelity questions: actual material may expose recurring course conventions or transcript defects whose kind and scope cannot yet be characterized. Revisit when rights-safe representative material becomes available; a complete course is never required.
- Compatibility exceptions revealed by runtime evidence or a later contract walkthrough: there is not yet evidence of a particular unsupported handoff or capability requiring its own decision. Revisit concrete failures rather than preselecting workarounds or infrastructure.

## Out of scope

- Writing the implementation specification, invoking to-spec or to-tickets, producing implementation tickets, or building production code, Agent Skills, fixtures, and test runners.
- M02 publishing mechanics: packaging, publication triggers, transport, distribution, hosting, and operational publishing/version rollout. Only M01's approved-output responsibilities are in scope.
- M03 Reader & Sync: application architecture, rendering implementation, search, offline storage, authentication, reading-progress sync, conflict policy, and position relocation.
- Reconsidering approved product behavior, requiring video or instructor code, demanding a whole-course corpus, changing course order into a new curriculum, and other exclusions in PRD §12.
- Low-level details that do not block specification: exact names and paths, field spelling, parser internals, prompt wording, retry counts, thresholds, and equivalent reversible choices. Escalate only a demonstrated architectural consequence.
