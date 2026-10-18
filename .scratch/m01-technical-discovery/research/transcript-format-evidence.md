# Transcript format and preservation evidence

Investigated: 2026-10-18. Context: **Establish transcript format and preservation constraints**, within **Technical Discovery for M01 — Content Production**.

This is evidence for a later intake/preparation decision. It selects no supported format, parser, storage schema, or implementation. Product meanings and obligations come from the approved [PRD](../../../docs/product/PRD.md), especially P01, P03–P05, C1–C3, and AC-M01-01/03. No proprietary source text or private material locations are recorded.

## Documented facts and authority

### Plain text

`text/plain` is unformatted text, without required interpretation of embedded formatting commands. MIME's canonical line break is CRLF; that transport rule is not proof that a local `.txt` file uses CRLF. The standard defines no transcript-specific cue, timestamp, speaker, course, or lesson structure. [RFC 2046 §§4.1, 4.1.1, 4.1.3](https://www.rfc-editor.org/rfc/rfc2046#section-4.1)

The MIME default charset for `text/plain` remains US-ASCII in the update; that does not identify an arbitrary filesystem file's actual encoding. [RFC 6657 §4](https://www.rfc-editor.org/rfc/rfc6657#section-4)

Unicode's UTF-8 BOM is an encoding signature, not an endianness instruction; its bytes are `EF BB BF`. An absent BOM does not establish the encoding. Ill-formed UTF input can trigger errors or replacement during decoding; apparently readable output alone is insufficient proof of preservation. [Unicode Consortium UTF/BOM FAQ](https://www.unicode.org/faq/utf_bom.html)

### WebVTT

The format owner publishes a **Candidate Recommendation Draft, 20 May 2026**, not a final Recommendation. This report pins that dated draft. [W3C status](https://www.w3.org/TR/2026/CRD-webvtt1-20260520/#sotd)

| Concern | Documented behavior |
| --- | --- |
| Bytes/lines | UTF-8; optional initial BOM; `WEBVTT` signature; CRLF, LF, or CR terminators. |
| Cue identity/order | Optional identifiers; supplied identifiers must be unique. Starts are nondecreasing, including ties; ends must exceed starts. |
| Timing | Required cue timings use millisecond dots; hours can be omitted when zero. Caption cues may overlap. |

[W3C §4.1](https://www.w3.org/TR/2026/CRD-webvtt1-20260520/#file-structure)

Payload can include voice/language annotations, emphasis, classes, ruby, internal timestamps, and HTML character references. Plain tag stripping loses information. [W3C §4.2.2](https://www.w3.org/TR/2026/CRD-webvtt1-20260520/#caption-text)

Regions support scrolling rollup display. Metadata/chapter tracks are other uses; chapter timing has different constraints. [W3C §1.4](https://www.w3.org/TR/2026/CRD-webvtt1-20260520/#introduction-other-features), [§§3.5–3.6](https://www.w3.org/TR/2026/CRD-webvtt1-20260520/#chapter-cues)

Parsing normalizes line endings, replaces NULLs, ignores comments, and can discard malformed blocks. Successful playback parsing therefore does not establish complete source retention. [W3C §6.1](https://www.w3.org/TR/2026/CRD-webvtt1-20260520/#file-parsing)

### SRT

The Library of Congress describes a numeric counter, start/end timing, text, and blank-line block separation. It characterizes SRT as poorly standardized, with little formal documentation; its preservation description is authoritative about its assessment, **not a normative creator-owned grammar**. It reports reader-dependent HTML-like styling. Its assertion of no encoding standard and detailed encoding/BOM examples are attributed to Wikipedia, and alternative counter/newline conventions to another tool's manual: these are explicitly weaker evidence. This research does not treat those details as universal conformance rules. Universal overlap, counter-uniqueness/order, entity handling, and speaker-markup rules were not established from a format-owner specification. [Library of Congress SRT description, Disclosure, Transparency, Quality, Notes](https://www.loc.gov/preservation/digital/formats/fdd/fdd000569.shtml)

As first-party evidence of one consumer's contract, YouTube requires UTF-8 basic SRT and recognizes no styling markup. Its example uses numeric counters, comma milliseconds, multiline text, and speaker labels inside text. Those are YouTube's documented expectations/examples, not universal SRT law or evidence about this project's inputs. [YouTube supported caption files](https://support.google.com/youtube/answer/2734698?hl=en)

The historical creator site linked by the preservation record could not be retrieved in this investigation. No equivalent normative SRT specification was verified. No library/API documentation was needed; format specifications and first-party format guidance were fetched directly.

### Source-location limits

Plain-text fragment references can use character/line positions or ranges, supplemented by integrity checks. Character and byte offsets differ; counting requires the encoding, and RFC line-ending sequences count as one character. Local LF/CR/CRLF conventions require explicit handling. These are locator semantics, not a requirement to adopt that URI scheme. [RFC 5147 §§2, 3, 4.1](https://www.rfc-editor.org/rfc/rfc5147#section-2)

## Support implications — inference, not selected policy

These deductions apply the evidence to the PRD's fidelity and visible-uncertainty obligations. They do not approve a support matrix.

| Candidate | Consequence for a future contract |
| --- | --- |
| Plain transcript text | Avoids subtitle grammar, but interpretation of handwritten times/headings/speaker labels needs a declared boundary. If untimed text is accepted, review locations cannot depend on invented timing. |
| SRT | A named accepted dialect and explicit handling of deviations would be more honest than promising compatibility with every `.srt` file. Consumer-specific UTF-8 restrictions cannot be generalized to all inputs. |
| WebVTT | Has a precise reference grammar and richer semantics to preserve or explicitly exclude. Conformance checking and tolerant reading answer different questions. |

- **Preservation:** P03 requires a comparison source independent of cleaned text. Keeping the original bytes available is one sufficient approach; exact storage and source identity remain later decisions. Re-decoding, newline conversion, cleanup, and entity conversion should not silently replace the comparison reference.
- **Loss accounting:** A process that returns some text may still have skipped material. Missing/invalid times, unexpected blocks, unknown markup, invalid decoding, empty results, or conflicting associations need a visible outcome under P04; silently treating a malformed subtitle as ordinary prose is not evidence of correct recovery.
- **Repetition:** Text equality alone cannot distinguish caption carryover from an instructor deliberately repeating a caveat or correcting a statement. An overlap/duplicate detector can identify review candidates; it cannot establish that deletion preserves meaning. Scrolling presentation also does not prove textual duplication. The original occurrences and any cleanup relationship remain relevant to review.
- **Location:** A cue label, timestamp, line, character range, and byte range identify different things. A time does not reconstruct missing code/video. A locator into cleaned text cannot automatically locate the same passage in the original. Any future comparison scheme needs source-version identity and declared coordinate semantics; the exact representation is deferred.
- **Speaker and technical text:** Missing speaker metadata does not authorize attribution. Cleanup should distinguish caption syntax from literal identifiers, operators, code fragments, speaker labels, and meaning-bearing annotation. The PRD permits removing filler, not silently losing substantive qualifications.

## Local observations and unknown corpus behavior

The coordinating session inspected the repository on 2026-10-18 using `rg --files --hidden --no-ignore`, excluding Git/dependency trees. It reported zero subtitle candidates with extensions `.srt`, `.vtt`, `.sbv`, `.ass`, `.ssa`, `.ttml`, or `.dfxp`, and zero `.txt`/`.text` candidates. The regular inventory contained project documentation, skills, and tracker material, with no representative lesson transcripts identified. No external private paths were searched or material read. This is repository inspection evidence, not proof that the user has no transcripts elsewhere.

Consequently the actual encoding/BOM/newline distribution, durations/sizes, cue ordering defects, duplicate/rolling-caption frequency, speaker conventions, entity/markup usage, missing timestamps, technical transcription errors, and missing visual-context references remain **unknown**. Specification permission is not evidence that any such behavior occurs in the user's corpus. There is no empirical basis here for declaring a candidate format sufficient, a cleanup heuristic safe, or a parser compatible with real inputs.

Rights-safe representative cases may later sharpen these questions; neither a complete course nor restricted material is required. Existing intake and source-processing decisions can select a declared initial boundary and expose unsupported/uncertain cases. Corpus-specific exceptions remain discovery fog until there is evidence.

## Research boundaries

Primary specification evidence: W3C, RFC Editor/IETF, and Unicode Consortium. First-party implementation evidence: YouTube's own import guidance, scoped to YouTube. Institutional assessment: Library of Congress, with its cited secondary assertions distinguished above. No parser execution, fixtures, private transcript processing, or format-support decision occurred. The evidence does not demonstrate implementation correctness or human editorial acceptance.
