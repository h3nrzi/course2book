# Choose recovery, stale evidence detection, and repeatability

Type: grilling
Labels: wayfinder:grilling
Mode: HITL
Blocked by: 12, 13
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P03, P13, P18, P22–P23, P26; C5; AC-M01-08–AC-M01-09; PRD §13

## Question

How can interrupted or repeated work resume from a corrected intermediate outcome without losing manual edits, misusing stale evidence, or replacing Approved Lessons?

Decide how upstream changes affect downstream drafts, research, code checks, QA, course-context aids, and approval evidence. Address interrupted writes, partial outputs, duplicate invocation, changed source or skill instructions, unavailable dependencies, and recovery to a known valid state. Identify the minimum retained source/artifact revisions, execution context, and verification context needed to explain and repeat the work.

Distinguish reproducible checks and traceable reruns from a promise of identical generated prose. Compare lightweight revision records and checkpoints with more elaborate machinery. Resolve invalidation, preservation, and recovery semantics; defer storage primitives, hashing choices, retry algorithms, and exact log formats where safe.

## Dependency rationale

- [Choose workflow invocation, handoffs, and execution controls](12-workflow-execution-controls.md): Recovery needs the invocation model and execution boundaries it must resume.
- [Choose review, focused revision, and explicit approval semantics](13-review-revision-approval.md): Invalidation and reruns must preserve the agreed review states and exact approval authority.
