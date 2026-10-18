# Establish transcript format and preservation constraints

Type: research
Status: resolved
Labels: wayfinder:research
Mode: AFK
Blocked by: None
Parent: [Technical Discovery for M01 — Content Production](../map.md)
Requirements: P01, P03–P05; C1–C2; AC-M01-01, AC-M01-03

## Question

What technical facts about plausible plain-text and subtitle inputs must be known before selecting the initial intake contract?

Examine authoritative format documentation for candidate timestamped inputs such as SRT and WebVTT, noting differences in specification authority, and local representative material if available. Identify encoding, cue ordering, overlapping or repeated captions, speaker/text markup, missing timestamps, and source-location limitations that affect faithful preparation and comparison. Do not assume these candidate formats are already selected.

The result is cited evidence and a comparison of support implications, not a parser, fixture implementation, or format-support decision. If the repository has no representative transcripts, record that limitation; do not require a complete course, obtain restricted course material, or invent evidence about the user's corpus.

## Answer

Resolved on 2026-10-18 through AFK primary-source research and repository inspection. The canonical factual record is [Transcript format and preservation evidence](https://github.com/h3nrzi/course2book/blob/989629e567d84ffdae2e5026d1d0239c0b4d87a9/.scratch/m01-technical-discovery/research/transcript-format-evidence.md), published on the throwaway `research/transcript-format-evidence` branch at commit `989629e567d84ffdae2e5026d1d0239c0b4d87a9`. No PR was opened and the research branch was not merged.

### Findings and limits

- The evidence compares plain text, SRT, and WebVTT for encoding, cue order and identity, timing, overlap/repetition, speaker/text markup, malformed input, and source-location limits. Documented facts and support implications are distinguished; no input variant or parser is selected.
- WebVTT has a dated W3C draft specification. SRT guidance has weaker authority: the record distinguishes institutional assessment and secondhand assertions from a particular consumer's documented contract, without inventing universal SRT rules.
- Cleanup can lose substantive evidence through decoding, markup removal, repeated-text deletion, or tolerant parsing that skips material. Future intake and preparation decisions must account for those risks under P03–P05 and C1–C2; storage and locator representation remain undecided.
- Repository inspection, including ignored/hidden files outside Git/dependency trees, found no representative lesson transcripts. Actual corpus conventions and failure frequencies remain unknown. No private material, complete course, or external private paths were accessed or required.

### Consequences for the map

[Choose transcript intake, lesson identity, and course ordering](04-transcript-intake-identity.md) now has its factual prerequisite and is unblocked. It owns initial support and intake semantics; [Choose source preparation and instructional coverage traceability](05-source-processing-coverage.md) owns the preservation/coverage contract after intake is decided. Research does not supply the user's decisions on either question.

Reviewed the complete evidence record for question coverage, source authority, citations and section links, privacy, and separation of facts from policy. Independently checked material W3C, Library of Congress, RFC, Unicode, and first-party caption guidance; verified tracker links and dependencies. No parser or end-to-end M01 workflow was exercised, so this is research completion, not implementation validation or human acceptance.

The findings fit existing intake, preparation, provenance, and evaluation questions. No newly precise question requires another ticket; corpus-specific exceptions remain in Not yet specified. Dependencies and scope are unchanged, and the broader discovery map remains open. No product/domain meaning or architectural choice was resolved, so no glossary or ADR was introduced.
