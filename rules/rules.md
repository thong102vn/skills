*** CRITICAL: You have to keep these persistent rules in your context memory. Always follow these rules as checklist to do your task. Re-evaluate rules again at the end of each task for improvement***

# Sumarize your understanding about these CRITICAL RULEs for confirmation before you start processing user prompt:

## Core — these bind every lap, whatever the task

- Always fix bug at root cause logic, not workaround.
- Use GitLab as default
- DON’T create OS-specific scripts like .sh files but use cross-platform script follow industry SDLC standards
- Never re-invent the wheel. Search FIRST — the working folders for logic to reuse/improve/replace, then free/self-host opensource — before writing anything. Never create duplicate, fragment or temporary files/documents/code
- The front-end (user interface) is decoupled from the back-end (data and logic), allowing the same content and services to be used across multiple channels (web, mobile, kiosks, etc.)
- DECOUPLE TEST — apply before writing any predicate, computation or default the backend also owns: would a second channel (mobile app, kiosk, partner API) have to reimplement this to behave correctly? If yes it belongs in the backend. MONEY RULES AND ACCESS RULES ARE NEVER MIRRORED — a mirrored money rule is a wrong price, a mirrored access rule is a leak
- Convention-over-configuration — the tenant should never have to touch configuration
- Always use venv for Python scripts. Check existing venv before creating new
- Use Helm for 3rd-party service/package and Kustomize for our internal service. Docker build must have Tagging: Every build gets a unique tag (e.g., v1.0.1)
- Always keep your working directory structure to follow industry SDLC structure (CLEAN architecture) with Agile management, put your new created files in proper directory 
- When you debug using the browser, always try to use your previous tabs or close old tabs``
- Always aware the task is for production level or not
- Never claim task done before finish all tests and review
- Always search only folders you are managing
- Organize big tasks to do in parallel
- Never auto git commit the changes by yourself
- The implementation must follow canonical design, never diverge. Ask user for any gaps canonical design
- Before asking the user a question, reporting a finding, or escalating a gap: prove the answer is not already in canon, the task ledger, or the codebase, and cite what was searched. A question the repo already answers is a defect, not a clarification
- For every data binding, data parsing, data rendering: avoid hand-curated names/fields list but DYNAMIC-FIRST, follow pattern **medallion**
- For a SPECIFICATION the split axis is artifact TYPE — schema, prose, DDL, wireframe, seed — so N greps of one type are one reading: search by the spec's own join key, its reference ID, never by a noun.
- Always include reference IDs from user stories or wireframe documents when you claim a task done
- Structural review enumerates nodes. Every defect lives in an edge.
- Amendments rewrite the body; they never accrete beneath it
- Presence isn't integrity; a title/decision is a pointer, not proof; and every fact you write lives in more than one place in this doc.
- Your design has to support multiple languages. The backend has to support base-path. Database design must be in industry enterprise-grade.
- A degraded string fails loud — a missing key, label or copy renders as a visible failure, never as plausible text that reads like a real answer
- An edit matches the file's existing bytes (EOL, indent, trailing newline); a size delta larger than the edit is a defect, not formatting
- Final output: lead with the verdict in one line. Then group every unfinished item under a `##<user-facing issue>` and `### <owner>` heading as `- [ ]` todos, each naming the blocking evidence and what it unblocks. Never mix owners in one list; never state a todo without the probe that proves it.
- For Android device, DON'T pipe 'adb logcat' outputs directly but through head/grep/python -c instead

## For database design: 
- Schema-as-Code / Migrations, not in planning document file. 
- Database schema design: DYNAMIC-FIRST, not a hand-curated column set follow pattern = **medallion + document-relational hybrid**

## For code implementation:
- Firstly, understand source code structure for where are reusable core/foundation and shared packages
- Always follow the given plan or design documents: for anything you implement differ from the plan, think if your solution is better otherwise change back to plan's. Any implementation is differ from the plan, you have to summarize those at the end for user to review.
- Don’t hardcode but dynamic first, generalize and standardize code and API implementation first and convention-over-configuration
- Add short code comment todo if your code need to improve later: hardcoding, hand-curated list, deduplication,...etc

## For design and planning

- Decompose to vertical-agnostic primitives reusable by different projects. A new exported primitive names the consumers outside its own package; none ⇒ it is app code, not a primitive — generalize from general to specific, in Clean Architecture separation. Design and implementation must stay flexible against requirement changes and extensions
- Separate test plan to separate file
- No vendor lock-in. Architecture must be easy to re-point at the best of multiple providers/opensources, since each has a weakness (price, performance, accuracy, time-to-build)
- The artifact is the DESIGN/PLAN document — never code comments. Explain key or hard parts, cite reference IDs, and name the bug-class rule that prevents a fix recurring, IN the plan, the task/ledger row or the report to the user. There is no explanation obligation that a source file satisfies. Detailed enough for a junior to follow in one go to production release — in that document, not in the code.
- Hardware scalable: Your solution should be flexibile to scale from standalone service on PC/on-premise to large scale distributed infrastructure on GCP
- Re-evaluate twice against side effects, limitations, gaps and KISS/SOLID/DRY/CLEAN — then improve


## For UI/UX design  *(read when the lap touches a UI surface)*
- Mobile-first
- Always choose the best font to support multiple languages
- Create  World-class UX usability protocol (5–8 users per persona per wave) + visual design-language requirements
- Design Checklist follow industry modern UI/UX best practices: UI design, Responsiveness, Typography, Icons, Interactive Elements, Centralized Theme, Color Scheme Generation, Component Themes, Custom Fonts
UI/UX audit needs:
1. Intent grouping (edge 5) — group every element by the user question it answers. Two surfaces answering one question, differing only by a classification the system could compute,
  are one surface with branches. This is the only item that would have caught the four-section page.
  2. Shared canvas (edge 5) — any repeated heavy widget (map, camera, scanner) is one instance the fields write into, never one per field.
  3. Input economics (edge 6) — count keystrokes, taps and screen-switches to the goal, and set a budget. "Works" and "is usable one-handed in rain" are different tests.
  4. Every promise has a receipt (edges 1, 2) — after any action a user waits on: acknowledgement, expected time, and an honest re-promise if it slips. Silence is a defect, not a
  neutral state.
  5. Two-actor surfaces need two screens (edge 2) — every handover, approval and reconciliation is drawn from both sides. The wrq_ finding is exactly this.
  6. Recovery and undo (edge 6) — for every destructive or time-pressured action, what does a mis-tap cost and how is it reversed?
  
For every visible widget on a screen (Nielsen heuristic #1, "match between system and real
  world"):
    a. List the user's primary task on this screen ("see today's run")
    b. For each visible widget, ask: does it answer that task RIGHT NOW? Is it overlaped?
    c. If a map → does its bounds include the answer? (driver pos + active order)
    d. If a counter → does its value reflect the relevant scope?
    e. If a placeholder → does its visual weight match its sibling's filled state?

  For every async placeholder (loading / null state):
    a. Render at the SAME font size and weight as the eventual filled state
    b. Mute only via colour, never via size shrink
    c. Reason: weight asymmetry vs filled siblings reads as "card broken"

  Per-screen checklist
  **Keep explicit user goal in mind, ask of each widget "does this answer the goal NOW?" Combine renderings measurement and screenshot-eyeball methodologies**
  1. Take screenshot at multiple device sizes (320, 360, 414, 768)
  2. Verify 8pt grid: every margin/padding is a multiple of 8 (or 4 with reason)
  3. Measure tap targets — every interactive element ≥44x44pt
  4. Run WCAG contrast checker on all text/bg color pairs
  5. Verify visual hierarchy — squint test: what stands out?
  6. Identify primary action — is it the most prominent element?
  7. Check baseline alignment — text in adjacent containers shares baselines
  8. Check optical alignment — icons may need 1-2px nudges to look centered
  9. Check edge alignment — content edges across sections should snap to a vertical line
  10. Check safe areas — does content respect notch/home indicator?
  11. Identify empty/loading/error states for every async surface
  12. Verify motion — every transition is purposeful and ≤300ms
  Cross-screen checklist:
  - Navigation pattern consistency
  - Color semantic consistency (red = destructive everywhere)
  - Typography scale (display / title / body / caption shouldn't drift)
  - Card/shape language (radii, shadows match across screens)
- For Flutter project, analyze the live running app: widget trees, visual layout, runtime state by using Flutter Agent Gateway MCP or Official Dart and Flutter MCP server

## For implementing the tests:
- Tests exactly what the human user see and interacts with. Always navigating via UI/Sidebar and using user-facing attributes as the first priority
- Always use User-First Locators. Avoid nth=-1 nor .last
- Dynamically discover all elements, links for each page and map each with know feature to run tests and catch unknown features in final report. Perform deep element reconnaissance on each result page
- Never implement mock response, mock data, fallback or never skip for what the test is expected to test

- If a test creates data, ensure it's either cleaned up or the environment is reset between runs (though idempotent data creation is preferred).

## Code quality:
- Use proper industry standard tools for checking code quality. Setup those tools if it not exists
- COMMENTS ARE DEFAULT-DENY. Do not add a code comment unless the reader cannot recover the fact from the code, the type names or the test. Self-evident, restating, section-header and narrative comments are defects — delete them; better naming and a smaller function are the fix.
  - If a comment could be a test, it MUST be a test. An invariant asserted in prose is unenforced; the same invariant in a test fails when violated.
## POST-task phase
- Always re-evaluate your work for remain limitations, issues, tasks
- Improve your work again if there is no need to ask user


