# Domain Docs

## Before exploring

This repo uses a single-context layout:

- Read `GLOSSARY.md` at the repo root for domain vocabulary.
- Read ADRs in `docs/adr/` that touch the area you are about to work in.

If these files or directories do not exist, proceed silently. The `/domain-modeling` skill creates them lazily when terms or decisions are resolved.

## Use the glossary's vocabulary

When naming a domain concept in an issue title, refactor proposal, hypothesis, or test name, use the term defined in `GLOSSARY.md`.

If a concept is missing, reconsider whether it belongs to the project's domain or note the gap for `/domain-modeling`.

## Flag ADR conflicts

If a proposal contradicts an existing ADR, identify the ADR and explain why its decision should be reconsidered.
