# Course2Book — Product Requirements Document

**Version:** 1.0  
**Status:** Product discovery baseline; technical discovery pending  
**Date:** 2026-10-18  
**Product:** Course2Book  
**Audience:** Product owner, coding agents, and engineers  
**Scope:** Product requirements across M01 Content Production, M02 Content Publishing, and M03 Reader & Sync

> **Boundary:** This is a product-level PRD, not a technical specification. It defines user outcomes, externally observable behavior, constraints, invariants, and acceptance criteria. It does not select frameworks, services, storage engines, agent orchestration mechanisms, application architecture, data schemas, APIs, or file formats. Those decisions belong to subsequent technical discovery. Matt Pocock's installed engineering skills are tools for that process, not a predetermined production architecture.

## 1. Problem and opportunity

English-language programming courses convey valuable technical knowledge, but turning dozens of hours of instruction into reusable Persian study material takes substantial manual effort. A transcript is available for many lessons, yet raw transcripts are spoken-language artifacts: they contain repetition, transcription defects, implicit references to on-screen code, and little textbook structure.

The user wants to learn incrementally from programming courses and end up with a durable, high-quality Persian technical textbook for each course, without personally writing each chapter. Straight translation and summarization are insufficient. The resulting text should preserve the important original teaching while adding useful explanations, independently written examples, and carefully sourced advanced context.

The user also wants a dedicated private reading experience on a laptop/desktop, locally and via the web, without turning the reader into a content authoring tool.

## 2. Product vision and outcomes

**Vision:** Transform a growing collection of English programming-course transcripts into a coherent, progressively authored, course-ordered, Persian technical book that the user can review, approve, publish, and read privately.

Desired outcomes:

1. A lesson's transcript can be processed without requiring the rest of the course, its videos, slides, or original source code.
2. Each approved lesson is a substantial educational chapter/section, not a condensed transcript or machine translation.
3. The authoring workflow remains inspectable and controllable in the project repository through dedicated agent skills.
4. The reader displays only published material and offers a polished study experience without any AI authoring or editing tools.
5. Published books and reading position stay consistent across a local offline-capable reader and a private web reader.

**Success is measured by fidelity, technical correctness, educational usefulness, controlled publication, and reliable reading continuity—not by total generated word count.**

## 3. Intended user and assumptions

- **Primary user:** One technically literate person studying English programming courses and preferring Persian educational prose with predominantly English technical terms.
- **Use:** Personal learning and reference, not public redistribution or commercial publishing.
- **Input availability:** Transcripts or subtitles are generally available one lesson at a time as the user studies.
- **Primary device:** Desktop/laptop. Web access is private; a dedicated mobile app is not a first-release goal.
- **Operating model:** The user uses a repository and coding agent (initially Codex) for content creation and approval; the app is a reader only.
- **Privacy and rights:** Course transcripts and derivative book content may have third-party rights restrictions. Product documentation and general-purpose code may be public, but private source material and generated books must not be exposed publicly by default.

## 4. Confirmed product decisions

| Area | Requirement / decision |
| --- | --- |
| Course material | English programming-course transcripts or subtitles |
| Minimum input | Transcript alone is sufficient; video, slides, and instructor source code are not prerequisites |
| Intake | Progressive, lesson by lesson; no whole-course upload requirement |
| Book structure | Follow the original course's lesson sequence and organization; do not reorder lessons into a new topic-based curriculum |
| Writing strategy | **Expanded educational authorship**: preserve essential source content and provide deeper teaching |
| Language | Fluent Persian prose with technical terms, identifiers, APIs, and code predominantly in English |
| Enrichment | Verified external technical material appears in clearly labeled **«بیشتر بدانید»** sections, with references and version context when relevant |
| Production | Dedicated repository-local agent skills operating on transcript file paths; AI operations take place outside the reader |
| Editorial control | Draft, inspect, manually revise or request AI revisions through the repository/agent workflow; explicitly approve each lesson |
| Publication | Only approved content becomes a published artifact consumable by the reader |
| Reader | App-native book library and read-only reading experience; no transcript ingestion, AI authoring, editing, or approval in the app |
| Availability | Local desktop/laptop use, including offline reading, and private browser-based web access |
| Sync | Published book content and progress (last-read lesson and position within that lesson) synchronize across Local and Web readers |

The requirements above override any earlier proposals for an in-app Book Studio or topic-reordered books.

## 5. Product boundaries and lifecycle

Course2Book comprises three **product responsibilities**, not a prescribed deployable-service breakdown:

### M01 — Content Production

Turns an input transcript into a reviewed, user-approved educational lesson by means of specialized agent workflows in the repository. This includes preparation, analysis, drafting, technical research, independent code examples, QA, human-directed revision, and explicit approval.

### M02 — Content Publishing

Makes approved educational artifacts available for consumption, maintains recognizable course/book/lesson structure, and conveys approved updates to the reader environments. Publishing is a distinct act from drafting or approving.

### M03 — Reader & Sync

Presents published books for private reading in local and web settings, saves reading position, supports offline local study, and synchronizes published content and reading progress without ever modifying authored book content.

**Authoring → approval → publication → reading** is the product boundary. Saving personal reading position is allowed in an otherwise read-only reader.

## 6. Cross-cutting invariants

**C1 — Source fidelity.** Every important instructional concept or qualification from an available transcript must be represented accurately in the lesson or explicitly identified as uncertain/unresolved. Spoken filler may be removed. No silently discarded substantive teaching.

**C2 — No fabricated instructor evidence.** Missing video context, on-screen actions, or instructor code must not be invented or attributed to the instructor. Agent-written examples are visibly independent. When the transcript alone is ambiguous, the uncertainty remains visible for editorial review.

**C3 — Clear provenance.** A reviewed lesson can be traced back to its source course and original lesson; supplemental research is distinguishable from source-derived instruction, and citations identify supporting references. No particular provenance encoding is prescribed here.

**C4 — Stable course order.** A published book follows the course's original sequence. Additional transcript lessons may extend it over time without silently reordering already published lessons.

**C5 — Human editorial authority.** Agent suggestions and revisions remain proposals until the user approves the lesson. Previously approved content is not silently rewritten by later skill runs.

**C6 — Publish gate.** A reader must not show drafts, failed QA outputs, unapproved revisions, or private transcripts as published book lessons.

**C7 — Production/reader separation.** Transcript inputs, AI operations, manual content editing, review, approval, and publishing all happen outside the reader. The reader only reads published authoring output and manages its own reading state.

**C8 — Personal privacy.** Private transcripts and derivative books are not made public unintentionally. The web reader controls access to private reading content; an unguessable URL is not sufficient access control.

**C9 — Offline continuity.** Existing local content can be read without network availability; offline reading position is retained and synchronized after reconnection.

**C10 — No silent progress loss.** Concurrent or delayed progress changes and published-content updates cannot silently destroy the user's saved last-read position. The exact conflict policy is a technical discovery decision.

## 7. M01 — Content Production requirements

### 7.1 Intake and organization

**P01.** The user can supply the path to a transcript or subtitle file located in the working environment and associate it with a specific course and original lesson. The user does not need to upload it to the reader.

**P02.** A course can start with a single available transcript and grow as later transcripts are added. The system must not demand a complete course corpus before the first lesson is produced.

**P03.** The workflow preserves the source transcript for comparison and editorial traceability, even when generating a cleaned working version. The accepted input variants and storage conventions are to be decided during technical discovery.

**P04.** The workflow exposes missing, unreadable, improperly associated, or clearly ambiguous inputs instead of guessing their content.

### 7.2 Transcript preparation and understanding

**P05.** Text preparation improves punctuation, spacing, transcription noise, and spoken-language organization without silently changing intended technical meaning.

**P06.** Lesson analysis identifies instructional concepts, significant statements, example descriptions, prerequisites, caveats, and incomplete references that warrant author attention.

**P07.** There is an inspectable relationship between substantive source points and their treatment in the resulting educational lesson, sufficient for a human to review coverage.

### 7.3 Educational authorship

**P08.** Each lesson is rewritten into polished, formal-but-readable Persian textbook prose. It is not a literal line-by-line translation, a short summary, or a chat-style paraphrase.

**P09.** Important teaching from the original transcript remains covered even when the lesson is expanded. The expansion should be purposeful, avoiding repetitive filler and artificial length targets.

**P10.** Explanations are pedagogically structured as relevant: what problem is solved, conceptual mechanics, meaningful examples, common misconceptions, practical application, limitations, and trade-offs. Not every lesson must follow a rigid template.

**P11.** Technical vocabulary is predominantly English inside readable RTL Persian prose. Code, identifier names, API names, and conventional terms remain recognizable to developers consulting English-language documentation.

**P12.** The author may create original code examples when transcript-only material lacks visible code; generated examples are clearly represented as independent educational examples, not reproduced instructor code.

**P13.** The authoring flow respects established terminology and concepts from already approved earlier lessons. Later lessons may reference earlier approved lessons without silently modifying them.

### 7.4 Supplemental research: «بیشتر بدانید»

**P14.** The workflow may research relevant technical concepts against official or otherwise credible primary technical documentation to improve accuracy and depth.

**P15.** External-source enrichment is labeled **«بیشتر بدانید»**, visibly separate from the main teaching derived from the transcript; it contains meaningful references and notes about relevant versions or time-sensitive behavior where applicable.

**P16.** Discrepancies between the instructor's described behavior and current technical documentation are flagged with context rather than silently rewriting what the course taught.

**P17.** If a material external claim cannot be verified, the workflow exposes uncertainty and does not present it as established fact.

### 7.5 Review, revision, and approval

**P18.** Production is organized into independently inspectable stages or responsibilities, such that a specialized skill can be run for one task without forcing a complete book regeneration. The exact number and composition of skills remain undecided.

**P19.** QA checks evaluate source-content coverage, factual and technical correctness, code examples, terminology, provenance, clarity, contradictions, and source limitations. Findings are visible to the user; a QA pass is evidence, not a guarantee of perfection.

**P20.** The user can review and manually edit drafts in the repository and ask the coding agent to revise a selected passage or lesson. AI-proposed changes are inspectable before acceptance and should preserve unrelated content.

**P21.** A lesson becomes approved only by an explicit user decision, not merely because generation or automated checking completed.

**P22.** Repeated runs or later lesson production must not silently replace a user-approved lesson. Any substantive change to approved content goes through renewed review and approval.

**P23.** It must be possible to identify lesson progress (e.g. not started, draft, awaiting review, approved) and the relevant QA/review outcome without depending on the Reader application.

### 7.6 Agent skills as product deliverables

**P24.** Agent skills are first-class product artifacts with defined intent, inputs, outputs, responsibilities, and observable completion/acceptance conditions.

**P25.** The workflow can be run using repository context and a coding agent without depending on embedded AI inside the reader. Its correctness and completeness can be evaluated with representative transcript cases.

**P26.** It is possible to correct an intermediate outcome and continue work without losing earlier approved results. Implementation-specific execution, orchestration, tool permissions, artifact contracts, and failure-recovery mechanisms are deferred to technical discovery.

## 8. M02 — Content Publishing requirements

**PUB01.** Publishing makes only explicitly approved lessons available as reader-consumable book content.

**PUB02.** Published content communicates a book's identity, course-derived order, lesson identity, title, body, relevant code examples, «بیشتر بدانید» sections, references, and any information necessary to maintain reader continuity.

**PUB03.** A newly approved lesson can be added to an existing book without having to republish every other lesson manually.

**PUB04.** The local and web reader can obtain the same approved content as it is published, without treating the source transcript or unreviewed drafts as distributable material.

**PUB05.** When approved lessons are revised and republished, the new published version is distinguishable from the previous one, and readers can adapt or recover previously saved reading positions.

**PUB06.** Publication failures must not expose partial, corrupt, unapproved, or inconsistent lesson content as a successful published state.

**PUB07.** The publication/distribution path protects private book content, especially because the code repository may be public.

**PUB08.** Publication can be carried out as part of the repository-driven workflow, independently of AI running in the reader. Its exact trigger, transport, versioning, and packaging design are technical discovery topics.

## 9. M03 — Reader & Sync requirements

### 9.1 Reading and navigation

**R01.** The user can browse a personal library of multiple published books and open a chosen book.

**R02.** A book presents the course's lesson sequence with navigable table of contents, clear titles, and next/previous lesson movement.

**R03.** Lessons render Persian RTL prose and embedded English LTR text reliably, including lists, headings, technical notation, links, and code blocks.

**R04.** Code examples retain readable formatting and appropriate syntax presentation; reference links and clearly distinguished «بیشتر بدانید» sections are accessible within the lesson.

**R05.** The reader supports search through available published book content and navigation to relevant results.

**R06.** The reading interface is primarily designed for desktop/laptop and is comfortable for sustained technical study.

**R07.** The reader presents approved, published book content as read-only. It does not display transcript upload, AI authoring, lesson-editing, editorial-approval, or publication controls.

### 9.2 Local and web availability

**R08.** The user can run/use the reader locally on their own computer and access the private reader over the web.

**R09.** Once published content is available locally, it remains readable without an internet connection.

**R10.** New or updated published content can reach both local and web environments, and the experience clearly distinguishes available content from content not yet downloaded or synchronized.

**R11.** The web reader restricts unauthorized access to the user's private book collection.

### 9.3 Study position synchronization

**R12.** The reader saves at least the last-read lesson and the position within that lesson for each book. This is reading state, not authorship.

**R13.** After reading in the local reader and then using the web reader (or vice versa), the user can continue from the synchronized lesson and position when connectivity permits.

**R14.** Local reading progress is captured offline and resumes synchronization on reconnection.

**R15.** Interleaving reads on two devices, delayed synchronization, and updated published content are handled without silently losing the user's study position. The specific conflict and relocation behaviors must be designed and verified.

**R16.** The reader gives understandable recovery feedback when synchronization is unavailable or temporarily fails, without blocking offline reading of available content.

**R17.** The initial synchronization scope is limited to published content and reading progress. Bookmarks, highlights, personal notes, and separate annotation sync are not implied.

## 10. Representative user journeys

**J1 — First lesson.** User creates or identifies a course in repository context, supplies a transcript file path, runs the appropriate agent workflow, reviews the Persian lesson against important source points, requests targeted revisions, explicitly approves it, publishes it, and reads it in the app.

**J2 — Incomplete visual information.** Transcript mentions "this function" without containing the on-screen code. The generated lesson acknowledges source limits, uses an original illustrative example where useful, and never claims to reproduce the instructor's code.

**J3 — Official documentation enrichment.** Transcript introduces an API behavior; research finds important version-specific differences. The original teaching is preserved, relevant context appears separately in «بیشتر بدانید» with citations, and uncertainty is surfaced where applicable.

**J4 — Progressive course.** After approving lessons 1–3, user provides lesson 4. Production uses prior vocabulary and necessary context but does not silently regenerate the first three approved lessons.

**J5 — Revision.** User rejects a paragraph and requests a clearer example. Revised text and its scope are reviewable; unrelated accepted material stays unchanged. Approval is explicit.

**J6 — Publication gate.** Lesson 5 exists in draft form; the reader shows published lessons 1–4 only. Once approved and successfully published, lesson 5 becomes available in the appropriate position.

**J7 — Offline-to-web continuity.** User studies locally offline midway through lesson 8, later reconnects, then opens the web reader and continues from the synchronized position.

**J8 — Conflicting progress.** User reads a book in both readers before synchronization completes. Their study location must not be silently discarded; the chosen conflict policy and user-visible recovery behavior are validated during technical discovery.

**J9 — Book revision.** An approved lesson receives a new published revision while the user has a saved reading position. The reader offers reliable continuation or explicit recovery instead of silently placing the user at an unrelated paragraph.

## 11. Acceptance criteria and release gates

These criteria define acceptable product behavior, not a predetermined testing framework.

### M01 acceptance

- **AC-M01-01:** A transcript for a single programming lesson can be processed without video, instructor source code, or the rest of the course.
- **AC-M01-02:** A human can compare source material with the drafted lesson and locate coverage of substantive instructional points; unresolved omissions are explicitly identified.
- **AC-M01-03:** Ambiguous references to unseen video/code are not silently invented or misattributed.
- **AC-M01-04:** The output is readable extended Persian instructional prose using predominantly English technical terms and useful independent examples.
- **AC-M01-05:** External enrichment is visibly separated as «بیشتر بدانید», references its evidence, and distinguishes relevant version differences.
- **AC-M01-06:** Technical and educational QA findings are recorded and reviewable before approval.
- **AC-M01-07:** The user can request a focused correction, inspect the change, and explicitly approve the revised lesson.
- **AC-M01-08:** A subsequent lesson can be produced using earlier course context without silently modifying already approved lessons.
- **AC-M01-09:** Each delivered skill can be tested against declared responsibilities and representative success/failure cases.

### M02 acceptance

- **AC-M02-01:** A draft or rejected lesson does not appear as published content; an explicitly approved and published lesson does.
- **AC-M02-02:** Publishing a new lesson preserves original ordering and does not corrupt existing published lessons.
- **AC-M02-03:** Both reader environments can receive the same published book content and identify updated published revisions.
- **AC-M02-04:** Failed publication does not expose partial or inconsistent output.
- **AC-M02-05:** Private transcripts or book materials are not unintentionally disclosed from a public code repository or public web endpoint.

### M03 acceptance

- **AC-M03-01:** Desktop reader can browse books, navigate lessons, search, and display mixed RTL text, LTR technical terms, code, and «بیشتر بدانید».
- **AC-M03-02:** Published lessons previously made available locally remain readable while offline.
- **AC-M03-03:** The private web reader restricts unauthorized access.
- **AC-M03-04:** Last-read lesson and in-lesson position synchronize between local and web after connectivity returns.
- **AC-M03-05:** Conflicting offline progress and content updates have observable, recoverable outcomes without silent loss.
- **AC-M03-06:** No transcript ingestion, AI authoring, editing, or lesson-approval functionality exists in the reader.

## 12. Out of scope for the initial release

- Video download, speech recognition, transcript extraction from video, and video playback/editing.
- Mandatory access to instructor source repositories, slides, or screenshots.
- Reordering courses into newly invented topic-oriented curricula.
- Publishing or selling translated books publicly, licensing/catalog marketplaces, or multi-author collaboration.
- A dedicated native mobile application or mobile-first authoring experience.
- In-app AI chat, prompts, generation, transcript editing, manual book editing, review, or approval.
- Quizzes, automatic skill assessment, spaced repetition, and learning gamification.
- Automatic sync of highlights, bookmarks, notes, or annotations.
- Mandatory PDF/EPUB export, GitHub-as-reader, or a specific authoring file format.
- Any preselected framework, hosted provider, database, agent framework, or orchestration model.

## 13. Product risks and constraints

- **Transcript incompleteness:** On-screen code and visual context may be absent. Use transparent limitations and independent examples.
- **False confidence:** LLM output can be polished but wrong or incomplete. Require source coverage checks, technical review, and human approval.
- **Long lessons and course continuity:** Lesson context may exceed practical processing limits; design must preserve instructional coverage and accepted prior work.
- **Research drift:** New documentation may describe behavior differing from the course's version. Label enrichment and version context rather than overwriting original claims.
- **Copyright/privacy:** The project repository is currently public. Keep proprietary transcripts, excerpts, derivative textbooks, credentials, and private artifacts outside public visibility unless appropriately permitted.
- **Sync correctness:** Offline edits to reading state, cross-device conflict, and changed book text require a defensible, observable policy.
- **Time and cost:** Skills should permit bounded, inspectable, repeatable progress rather than requiring full-course reruns for every correction.

## 14. Open questions for technical discovery (not PRD decisions)

The product requirements above are stable inputs. Discovery must investigate and decide, with the user, how to implement them:

### M01-first questions

- What is the minimal set of specialized skills and what responsibility boundary does each own?
- How should a file path identify its course/lesson and how is incremental lesson ordering maintained?
- Which transcript/subtitle formats are supported first, and how should incomplete/timestamped transcripts be handled?
- How can substantive source-point coverage, uncertainty, original examples, and externally researched claims be made auditable?
- What artifacts and states permit selective reruns, precise diff review, reproducible QA, and human approval without overwriting accepted work?
- How will code example verification and external primary-source/version checks work in practice?
- What workflow and test fixtures will prove educational quality, fidelity, and error handling?
- How should private source/book artifacts be separated from the public Git repository?
- What output boundary should M01 establish with M02 while leaving M02 publishing mechanics open?

### Later-module questions

- How are approved versions packaged/published and safely distributed to both Reader modes (M02)?
- How are private web access, offline content, synchronized progress, conflict handling, and position relocation implemented (M03)?
- What minimum capability should be shared between local and web without duplicating reader behavior?

## 15. Delivery sequence and phase gates

1. **Product requirements:** Maintain this PRD as the source of truth for product scope and invariants.
2. **M01 technical discovery:** Inspect repository and installed Matt Pocock skills; use the relevant discovery interview/decision workflow with the user. Record technical decisions and glossary/ADRs when warranted. **Do not implement before discovery and an agreed spec.**
3. **M01 specification and tickets:** Translate accepted technical decisions and PRD acceptance criteria into a buildable spec and ordered, testable tickets using the repository's local issue-tracker conventions.
4. **M01 implementation and evaluation:** Implement skill workflows and check them against representative transcript cases and the M01 release gate.
5. **M02 discovery → spec → implementation:** Establish publishing, versioning, privacy, and approved content delivery.
6. **M03 discovery → spec → implementation:** Deliver the read-only local/web reader and content/progress synchronization.

**Phase boundary rule:** Do not embed assumed technical choices into this PRD to speed up a later phase. If discovery changes product behavior or scope, explicitly propose a PRD revision for user approval before treating that change as settled.

## 16. Glossary for discussion (product meanings only)

- **Course:** Original sequence of programming instruction from which transcripts are progressively supplied.
- **Transcript:** Text/subtitle source for one original lesson; may omit video-only information.
- **Lesson:** A course-ordered unit of instruction that becomes a corresponding Persian book unit.
- **Draft:** Generated or edited lesson awaiting explicit user approval.
- **Approved Lesson:** Lesson content the user has explicitly accepted; not necessarily yet published.
- **Published Artifact:** Approved book content exposed by the publishing workflow to readers.
- **Expanded Educational Authorship:** Faithful preservation of substantive instruction plus deeper pedagogy and independent, clearly identified examples.
- **«بیشتر بدانید»:** Separately labeled, referenced supplemental technical information researched outside the source transcript.
- **Agent Skill:** A repository-local, independently evaluable capability used by the coding agent in the production workflow.
- **Reader:** Read-only application for published book content; storing reading state does not make it a content editor.
- **Reading Progress:** Last-read lesson and a position within it, synchronized across reader environments.
