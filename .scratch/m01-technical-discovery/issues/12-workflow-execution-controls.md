# Choose workflow invocation, handoffs, and execution controls

Type: grilling
Labels: wayfinder:grilling
Mode: HITL
Blocked by: 11
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P18, P24–P26; C5, C7–C8; PRD §13

## Question

How should the user and coding agent invoke, sequence, and hand off the agreed specialized responsibilities with the least coordination machinery that satisfies M01?

Compare direct manual invocation, a thin coordinating skill, and additional automation only where evidence warrants it. Decide how prerequisites and incomplete outputs are exposed, where the workflow stops for human input, and how tool and write permissions constrain a run. Address bounded work on one lesson or selected stage and how accidental overlapping work is detected or prevented without assuming a distributed scheduler.

Resolve the execution model and control boundary. Recovery and stale-output policy will build on this answer; detailed commands, prompt routing, retry counts, lock implementation, and orchestration infrastructure are deferred unless a genuine architectural blocker demands them.

## Dependency rationale

- [Choose the minimal specialized Agent Skill responsibilities](11-specialized-skill-boundaries.md): Invocation and coordination require known skill responsibilities and handoffs.

The privacy boundary is already a prerequisite through skill responsibilities and constrains tool access and write controls.
