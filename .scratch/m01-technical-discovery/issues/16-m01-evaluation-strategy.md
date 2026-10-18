# Choose representative M01 evaluation and acceptance evidence

Type: grilling
Labels: wayfinder:grilling
Mode: HITL
Blocked by: 14, 15
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P24–P26; AC-M01-01–AC-M01-09; C1–C8 as applicable to M01

## Question

What representative evidence will let an implementer and the user evaluate each agreed skill responsibility and the complete transcript-to-approval path against M01's PRD acceptance criteria?

Choose a small, rights-safe set of case categories and evaluation seams covering a single transcript, ambiguous visual references, long or noisy input, version discrepancies, independent examples, focused manual/AI revision, stale QA or approval, interrupted reruns, and progressive course continuity. Determine which outcomes can be checked mechanically and which require Persian educational review or other human judgment. Address how absent representative private material affects confidence without requiring a complete course.

Resolve the evaluation strategy, practical evidence needs, and limits of automated confidence. Do not author production fixtures, tests, a full implementation specification, or implementation tickets. A prepared evaluation guide or automated pass does not establish human acceptance.

## Dependency rationale

- [Choose recovery, stale evidence detection, and repeatability](14-recovery-reproducibility.md): Evaluation cases must exercise the actual execution, invalidation, and recovery contract.
- [Choose the approved M01 output boundary with M02](15-approved-output-boundary.md): End-to-end evaluation needs a defined approved-output boundary; publishing itself remains outside the test path.
