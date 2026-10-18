# Choose quality assurance evidence and finding semantics

Type: grilling
Labels: wayfinder:grilling
Mode: HITL
Blocked by: 09
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P19; C1–C3; AC-M01-02–AC-M01-06

## Question

What evidence should QA produce, and how should findings distinguish acceptable teaching, required correction, and an unresolved limitation that needs human judgment?

Cover instructional completeness, factual and version correctness, independent code examples, terminology, source attribution, Persian clarity, contradictions, and unseen source context. Compare mechanical checks, agent review, and human evaluation, including what meaningful reviewer independence is feasible and which errors each can miss. Decide how QA records the exact material assessed and exposes its own limitations; an automated pass cannot imply approval.

Resolve finding categories, materiality and review implications, and the responsibility for producing evidence. Do not introduce new product acceptance rules without identifying a genuine PRD conflict. Approval mechanics, skill packaging, and the eventual evaluation fixture suite are separate decisions.

## Dependency rationale

- [Choose intermediate artifact authority and data flow](09-intermediate-artifact-contracts.md): QA needs the agreed authoritative artifacts and provenance links to say precisely what it assessed.
