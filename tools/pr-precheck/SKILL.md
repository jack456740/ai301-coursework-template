---
name: pr-precheck
description: Check whether one Path Review pull request package is ready to submit using its issue, plan, diff, test evidence, and repository standards.
---

# PR Precheck

## Purpose

Answer exactly one question about one PR package: is it ready to submit?

Use the checks in `rubric.md`, the evidence locations in
`references/evidence-guide.md`, and the steps in `procedure.md`.
Do not invent checks or change the rubric during a run.

## Required files

- `CONTRACT.md`: fixed interface and output requirements
- `rubric.md`: checks, pass conditions, and verdict rule
- `procedure.md`: evaluation sequence
- `references/evidence-guide.md`: evidence sources
- `scope.md`: permitted repository and house rules
- `voice-guide.md`: student communication rules

Read the required files before evaluating.

If `rubric.md` or `procedure.md` has no substantive student-authored
content, refuse to grade. Never improvise a replacement rubric.

## Modes

### Live mode

Use this mode for a student's real pull request draft.

1. Read `scope.md` first.
2. Stop without grading if the Repo line contains a placeholder.
3. Refuse packages targeting repositories outside the stated scope.
4. Read `voice-guide.md`.
5. Gather the actual issue, issue discussion, posted plan, recorded
   deviations, branch diff, commits, test results, repository policies,
   and pull request template.
6. Evaluate the draft PR title and description against the actual
   repository requirements and voice guide.
7. Apply every rubric check using the procedure.

A voice-guide violation must be reported but changes the verdict
only if a rubric check explicitly makes it a failure.

### Eval mode

Use this mode when given a frozen PR package bundle.

The bundle is the entire evidence universe. Do not fetch GitHub,
browse external sources, read local repository files, or use scope.md
or voice-guide.md to supplement the bundle.

Evaluate the complete package using every rubric check and the
full verdict rule. Do not infer missing evidence.

## Evidence discipline

For each check, assign `pass`, `fail`, or `unclear` based on its
written conditions. Cite one decisive fact, quote, or absence
from the permitted evidence.

Do not equate a polished description with a correct implementation.
Compare actual diff behavior with the issue and plan. Respect
explicitly documented plan deviations and honestly disclosed limits.

Do not assume a repository policy exists unless the permitted
evidence establishes it.

## Verdict

Use the exact aggregation rule in `rubric.md`.

Return only `accept` or `reject`. There is no third verdict.
Unverifiable required claims must not be treated as passing.

## Output format

A readable per-check summary may precede the machine-readable output.

End every completed evaluation with exactly one fenced JSON block,
with no text after it. Preserve the exact schema and field order:

```json
{
  "item": "<PR URL or bundle id>",
  "checks": [
    {
      "name": "<check name>",
      "grade": "pass|fail|unclear",
      "evidence": "<one line: decisive fact or quote>"
    }
  ],
  "verdict": "accept|reject"
}
```
