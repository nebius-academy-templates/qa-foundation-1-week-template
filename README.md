# QA Foundation, Week 1: Prepare a failure brief

Turn the 166-line failed run in `task/case.log` into one small, evidence-backed `log_slice.md`. The goal is to isolate the causal story, not retell or dump the log.

## Deliverable

Copy the template to the repository root:

```bash
cp task/log_slice.md.template log_slice.md
```

PowerShell: `Copy-Item task\log_slice.md.template log_slice.md`. Don't modify `task/case.log`.

Fill all five sections:

1. **Failed test name** — exactly as the runner printed it.
2. **First meaningful error** — one complete assertion or exception line, not `FAILED` or `BUILD FAILED`.
3. **Stack trace root frame** — the first frame from project code when reading the trace top to bottom, not JUnit, Allure, or JDK plumbing.
4. **Relevant evidence** — 3–5 complete lines from test output, logcat, or inspected artifacts that support the verdict.
5. **Suspected layer** — `app`, `tests`, `environment`, or `unknown`, plus one evidence-based sentence.

## Workflow

1. Read `task/case.log` yourself and form a verdict before asking an agent.
2. Ask the agent to fill `log_slice.md` from the template without paraphrasing, shortening, or reformatting quoted lines.
3. Compare its draft with your verdict. If you disagree, the log decides.
4. Verify every quoted line with `grep -F` or PowerShell `Select-String -SimpleMatch`; recopy any missing or partial line from the log.
5. Commit and push `log_slice.md`, then paste its complete contents into the AI checker on the platform.

## Rules and submission check

- Every non-empty line inside a code fence must be one complete verbatim line from `case.log`; edge whitespace doesn't matter.
- Identical errors and first project frames across tests may represent one shared cause; don't duplicate the same slice.
- Don't change a test expectation merely to match the observed value; confirm the product contract first.
- Keep `log_slice.md` at no more than 45 lines and 4000 characters, with at most 12 consecutive and 25 total copied log lines.
- Remove every TODO/TBD marker, close every code fence, and keep all five section headings.
- Paste only `log_slice.md` into the AI checker, not the full `case.log`.
