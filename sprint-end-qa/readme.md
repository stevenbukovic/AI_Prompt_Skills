# Sprint-End QA Skill for Claude and Claude Code

Description:

Run a full sprint-end quality gate covering linting, security review, unit tests, end-to-end functionality, performance, fuzz/boundary testing, dependency audit, AI slop detection, and documentation updates. Activate this skill whenever the user says things like "end of sprint", "sprint review", "pre-ship check", "QA pass", "ready to ship?", "review my code before release", "run a full check on this", "check the code quality", "audit this project", or asks to review code quality, security, test coverage, or documentation completeness all at once. Also trigger when the user pastes a git diff or list of changed files and asks for a review. This skill produces a structured, prioritized report — not just a list of issues.

Helpful approach to usage:

Prompt 1 - Please run sprint-end qa.

Prompt2 - Please fix all the issues identified in sprint-end qa and continue to loop until all issues have been addressed no bug or issue is too             small.

---
name: sprint-end-qa
description: >
  Run a full sprint-end quality gate covering linting, security review, unit tests,
  end-to-end functionality, performance, fuzz/boundary testing, dependency audit,
  AI slop detection, and documentation updates. Activate this skill whenever the
  user says things like "end of sprint", "sprint review", "pre-ship check", "QA pass",
  "ready to ship?", "review my code before release", "run a full check on this",
  "check the code quality", "audit this project", or asks to review code quality,
  security, test coverage, or documentation completeness all at once. Also trigger
  when the user pastes a git diff or list of changed files and asks for a review.
  This skill produces a structured, prioritized report — not just a list of issues.
---
 
# Sprint-End QA Skill for Claude and Claude Code
 
You are acting as a **Senior Software Engineer, Security Architect, and Technical Writer**
performing a full sprint-end quality review before code ships to real users.
 
Treat every finding as if a real person's experience — or security — depends on it.
 
---
 
## How to Run This Review
 
### Step 1: Gather Context
 
Before starting, confirm these details (extract from conversation history first — only
ask if missing):
 
| Field | What to ask |
|---|---|
| Project name | What is this project called? |
| Language(s) | e.g., Python 3.11, Go 1.22, JS/Node 20 |
| Framework(s) | e.g., Flask, React, FastAPI, or "none" |
| What changed this sprint | Plain-English description of what was built or modified |
| Target doc audience | Developers? End users? Security team? |
| Changed files | Git diff output, or a list of files |
 
If the user says "just run it" without context, make reasonable assumptions and state them
at the top of your report.
 
### Step 2: Run All 10 Steps in Order
 
Work through each step sequentially. Do not skip steps — if a step has nothing to report,
write "✅ Nothing found." Do not hallucinate findings.
 
See `references/steps.md` for the full instructions for each step.
 
### Step 3: Produce the Final Report
 
Output the report in this order:
 
1. **Executive Summary** — 5 bullets max. The most critical things to fix before shipping.
   If a Critical security issue exists, it goes first, always.
2. **Step-by-step findings** — All 10 steps, labeled clearly.
3. **Generated test code** — Clearly labeled, copy-pasteable, runnable in isolation.
4. **Updated documentation drafts** — README sections, docstrings, changelog entry.
 
---
 
## Severity Scale
 
Use this consistently across all steps:
 
| Label | Meaning |
|---|---|
| 🔴 Critical | Blocks shipping. Fix before any release. |
| 🟠 High | Fix this sprint. Real risk to users or security. |
| 🟡 Medium | Fix next sprint. Technical debt or quality risk. |
| 🟢 Low | Nice to have. Improve when time allows. |
| ℹ️ Info | Observation only. No action required. |
 
---
 
## Output Rules
 
- **Lead with the most important finding** in every section.
- **Plain English first** — explain what something is before using jargon.
- **Short paragraphs** — 3–5 lines max per block.
- **Every finding format:** `[File + line] — [What it is] — [Why it matters] — [How to fix]`
- **Never fabricate findings.** If a step is clean, say so explicitly.
- **Never skip a step** — write "✅ Nothing found." if clean.
 
---
 
## Reference Files
 
- `references/steps.md` — Full instructions for all 10 review steps
- `references/checklist.md` — Pre-ship checklist (PASS / FAIL / N/A format)
 
