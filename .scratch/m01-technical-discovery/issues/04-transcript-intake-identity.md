# Choose transcript intake, lesson identity, and course ordering

Type: grilling
Labels: wayfinder:grilling
Mode: HITL
Blocked by: 02
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P01–P04, P13; C3–C4; AC-M01-01, AC-M01-08

## Question

What minimum intake contract associates an input path with an original course and lesson, preserves course order as material arrives, and selects the first supported input variants?

Decide what must be explicit versus safely inferred, how ambiguous associations and unreadable or unsupported inputs are exposed, and what identifies a lesson independently of display title or source filename. Consider a single available lesson, lessons received out of sequence, duplicate intake, corrected transcripts, and renamed files. No whole-course inventory, videos, or instructor code may become prerequisites.

Use format evidence to compare the costs of a narrow initial support set with broader support. Resolve identity and ordering semantics and the intake failure contract; defer parser selection, field spelling, and exact path layouts unless they carry a blocking architectural consequence.

## Dependency rationale

- [Establish transcript format and preservation constraints](02-transcript-format-evidence.md): Format evidence is needed to compare initial input support and its limits.
