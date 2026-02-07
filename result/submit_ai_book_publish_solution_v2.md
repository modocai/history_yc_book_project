# AI-based Book Publish Solution

Consolidated, chronological summary of the AI-assisted build process, reconstructed from raw transcripts and execution logs.

## Why This Started

- The starting request was explicit: build a practical way to write a full book with AI using markdown, while collaborating in Google Docs. [1][2]
- The first problem statement combined three needs at once: AI-friendly authoring, human review in Docs, and feedback continuity back to structured source files.
- The project was started because manual copy/paste across markdown, Docs, and issue tracking created drift and coordination overhead. [2]

## Core Idea

- Keep Git markdown as source of truth.
- Publish immutable review artifacts to Google Docs (`book publish`), instead of overwriting a single shared doc.
- Pull only actionable review signals from Docs (`book pull`) into GitHub issues for agent execution.
- Reduce synchronization complexity by design, not by adding conflict-resolution layers. [3][4]

## Chronological Timeline (Event Summaries)

### Event 1 — 2026-02-05: Initial framing and constraints

- Kickoff intent: "우리는 책을 쓸거야." ("We're going to write a book."). [1][2]
- Initial requirements set the shape of the system: markdown-first writing, Google Docs collaboration, and section-level continuity.
- The first implementation planning pass captured CLI surface and doc conversion direction. [5]
- Early requirements were concrete enough to begin implementation sequencing immediately.

### Event 2 — 2026-02-05: Architecture pivot to Git-native workflow

- The initial design considered stronger synchronization controls, then was explicitly replaced by a simpler model. [6]
- The user changed direction to Git-native pull/push behavior with `publish` semantics for Docs output.
- The new model removed bidirectional body sync and moved review ingestion to issue creation. [7][32]
- This pivot removed core conflict classes and simplified operation boundaries.

### Event 3 — 2026-02-05: Implementation of Drive import path and auth scope

- OAuth scope was expanded from `drive.file` to `drive` to access user-uploaded files. [8]
- Drive client capabilities were extended to list with `mimeType`, download binary files, and export Google Docs as `.docx`. [9]
- A new `book import` command was added for recursive folder import with Google Docs export support. [9]
- Runtime troubleshooting found folder visibility issues, then fixed shared-drive access flags. [10]
- Import execution finished with three manuscript files downloaded. [11]

### Event 4 — 2026-02-05: Shipping discipline and secrets hygiene

- Before commit/push, secret handling was explicitly reviewed (`client_secret.json` excluded). [12]
- Downloaded binary imports were excluded from commit scope.
- Core feature changes were committed as `ff11b10` with targeted file selection. [13]
- Credentials-related paths were then added to `.gitignore` to harden baseline repo hygiene. [14]

### Event 5 — 2026-02-05: Large-scale issue automation for writing workflow

- A structured issue system was planned: chapter/part/type/language labels and EN/KO issue hierarchy. [15][16]
- Scripted automation created labels, issues, and project field assignments at scale.
- A sub-issue linking failure was debugged by switching from node ID/string usage to numeric DB ID with correct argument typing. [17]
- Final verification confirmed all 16 KO sub-issues linked to EN parent issues and expected counts aligned. [18][33]

### Event 6 — 2026-02-06 00:18~00:22 UTC: Transcript reconstruction and ordering

- A separate transcript task required rebuilding merged logs with correct beginning and narrative continuity. [19]
- Start anchor was explicitly fixed to the sentence containing "우리는 책을 쓸거야.". [19]
- Duplicate file clusters were identified and de-duplicated.
- The merged output was regenerated with block-level overlap removal and sequence validation. [20][21]

### Event 7 — 2026-02-06 00:34~00:51 UTC: Gemini chunked translation pipeline

- Initial attempt blocked on missing API key; prerequisite was made explicit. [22][23]
- After environment setup, translation was executed in chunked mode (27 chunks). [25]
- Sandbox/home-directory permission failures were handled by rerouting runtime home to `/tmp`. [24]
- Progress was monitored as a long-running pipeline with repeated polling.
- Final English artifact was generated from Korean source transcript. [34]

### Event 8 — 2026-02-06 (later): StyleTemplate fidelity loop

- A style-matching loop was planned against a visual template diff matrix (thematic break, paragraph spacing/color, blockquote, code block styling). [26][27]
- Converter and element model were extended to support missing style semantics.
- Test coverage increased through iterative fixes; intermediate and later runs reached 160+ and then 163 passing tests. [28][31]
- A latent table index bug in `_emit_code_block` was identified and corrected (overhead formula corrected to 6). [29][30]
- Manual publish checks remained in the loop, with user feedback driving further visual refinements.

## Key Outcomes

- System architecture converged to a simpler and more robust Git-native publishing model. [7][32]
- Google Drive import capability was implemented and validated against real folder content. [11]
- Issue operations were scaled with automation (labels, parent/child issue structure, project field wiring). [18][33]
- A long transcript was transformed into reusable artifacts (merged/extracted/readable/translated outputs). [21][34]
- Style fidelity work established an iterative engineering pattern: visual diff -> code changes -> automated tests -> publish verification. [28][31]

## Appendix: Source References & Links

- Repository root: https://github.com/modocai/history_yc_book_project
- This submit file: https://github.com/modocai/history_yc_book_project/blob/main/result/submit_ai_book_publish_solution_v2.md
- Core source (EN build transcript): https://github.com/modocai/history_yc_book_project/blob/main/result/2026-02-05-bookbook-gitnative-copilot-en.txt
- Core source (KO build transcript): https://github.com/modocai/history_yc_book_project/blob/main/result/2026-02-05-bookbook-gitnative-copilot.txt.txt
- Core source (Codex readable transcript): https://github.com/modocai/history_yc_book_project/blob/main/result/codex_transcript_2026-02-05T19-05-49_readable.txt
- Core source (StyleTemplate loop): https://github.com/modocai/history_yc_book_project/blob/main/2026-02-06-styletemplate-test.txt

Private repository (reference only):
- https://github.com/modocai/Book_HealthcareAI_for_Consumer (private)

## References

[1]: `result/2026-02-05-bookbook-gitnative-copilot.txt.txt:13`
[2]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:1`
[3]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:107`
[4]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:121`
[5]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:34`
[6]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:94`
[7]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:109`
[8]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:547`
[9]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:643`
[10]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:861`
[11]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:911`
[12]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:937`
[13]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:954`
[14]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:965`
[15]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:1009`
[16]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:1016`
[17]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:1095`
[18]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:1132`
[19]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:137`
[20]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:168`
[21]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:186`
[22]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:232`
[23]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:254`
[24]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:317`
[25]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:446`
[26]: `2026-02-06-styletemplate-test.txt:7`
[27]: `2026-02-06-styletemplate-test.txt:61`
[28]: `2026-02-06-styletemplate-test.txt:718`
[29]: `2026-02-06-styletemplate-test.txt:921`
[30]: `2026-02-06-styletemplate-test.txt:928`
[31]: `2026-02-06-styletemplate-test.txt:1835`
[32]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:120`
[33]: `result/2026-02-05-bookbook-gitnative-copilot-en.txt:1157`
[34]: `result/codex_transcript_2026-02-05T19-05-49_readable.txt:444`
