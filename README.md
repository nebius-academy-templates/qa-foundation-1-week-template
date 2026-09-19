# Task 1.10: Prepare a failure brief

Turn the 166-line failed run in `task/case.log` into one small, evidence-backed failure brief. Submit the completed brief in the lesson 1.10 LMS answer box.

## Deliverable

Submit one completed five-field failure brief. `task/case.log` is reference evidence; do not modify or submit it. No file creation, commit, or push is required.

The [answer template](task/log_slice.md.template) is optional. You can copy its text into the answer box and replace every placeholder, or use a local copy while drafting.

Include all five fields:

1. **Failed test** — exactly as the runner printed it.
2. **First meaningful error** — one complete assertion or exception line, not `FAILED` or `BUILD FAILED`.
3. **Where to investigate first** — the first complete stack-trace line pointing to a project file when reading the trace top to bottom.
4. **Relevant evidence** — 3–5 complete lines from test output, logcat, or inspected artifacts that support the verdict.
5. **Suspected layer and justification** — `app`, `tests`, `environment`, or `unknown`, plus one evidence-based sentence.

The checker evaluates these five fields, not their order or exact Markdown formatting. Clear equivalent headings, bullets, code fences, and plain text are accepted.

## Workflow

1. Read `task/case.log` yourself and form a verdict before asking an agent.
2. Ask an agent to challenge your verdict using `task/case.log` and identify evidence that would distinguish alternative explanations.
3. Compare its reasoning with your verdict and resolve disagreements against specific lines in the log.
4. Verify every quoted line with `grep -F` or PowerShell `Select-String -SimpleMatch`; recopy any missing or partial line from the log.
5. Paste the completed brief into the lesson 1.10 LMS answer box and run the AI check. Use its feedback to correct any incomplete or unsupported field.

## Rules and submission check

- Every quoted log or artifact line must be one complete verbatim line from `task/case.log`; edge whitespace doesn't matter.
- Identical errors and first project frames across tests may represent one shared cause; don't duplicate the same slice.
- Don't change a test expectation merely to match the observed value; confirm the product contract first.
- Keep the brief at no more than 45 lines and 4000 characters, with at most 12 consecutive and 25 total copied log lines.
- Fill all five fields and remove every unfinished placeholder.
- Submit the brief in the LMS answer box; the complete `case.log` remains reference evidence.
