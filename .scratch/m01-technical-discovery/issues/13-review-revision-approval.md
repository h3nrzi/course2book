# Choose review, focused revision, and explicit approval semantics

Type: grilling
Labels: wayfinder:grilling
Mode: HITL
Blocked by: 10
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P20–P23, P26; C5–C6; AC-M01-07–AC-M01-08

## Question

What review and lesson-state semantics preserve the user's editorial authority while supporting manual edits, focused AI proposals, and explicit approval of the exact content reviewed?

Determine how a proposed revision is compared with existing text, how its scope protects unrelated material, and what binds approval to a specific lesson revision and relevant QA evidence. Address manual edits after QA or approval, unresolved material findings, rejection or requested changes, and production of later lessons. Decide how current progress and review outcomes remain inspectable outside the Reader.

Compare the lightest durable approval evidence and change-review approaches. Resolve state transitions and authority, not a UI or a production approval command. Approval must remain distinct from publication, and no agent or QA pass may stand in for the user's explicit decision.

## Dependency rationale

- [Choose quality assurance evidence and finding semantics](10-quality-assurance-evidence.md): Finding semantics establish what the user must be shown before approving.

Artifact authority is already a prerequisite through QA; review and approval must bind to its authoritative content revision and associated evidence.
