# Procedure: PR Precheck

## 1. Determine the mode

Use **eval mode** when evaluating a supplied frozen PR package bundle. Otherwise, use **live mode** for the student's real pull request draft.

Evaluate exactly one package per run.

## 2. Load the required instructions

Read `SKILL.md`, `rubric.md`, and `references/evidence-guide.md`.

If the rubric or procedure contains no substantive student-authored instructions, refuse to grade. Do not invent missing checks.

### Live mode

1. Read `scope.md` before gathering any other evidence.
2. Verify that the `Repo:` line contains an actual repository.
3. Stop if the scope is unfilled or the PR targets another repository.
4. Read `voice-guide.md`.
5. Gather the actual issue, discussion, posted plan, recorded deviations, branch diff, commit history, PR template, repository policies, and available test evidence.

### Eval mode

1. Read the supplied package bundle.
2. Treat the bundle as the complete evidence universe.
3. Ignore `scope.md` and `voice-guide.md`.
4. Do not fetch external evidence or inspect unrelated local files.

## 3. Establish the intended change

Identify the issue's requested behavior, the posted plan's implementation boundaries, and any explicitly recorded deviations.

Identify the candidate PR's title, description, changed files, and observable implementation behavior.

Do not treat the PR description as proof that the implementation matches the plan.

## 4. Check plan fidelity

Compare each meaningful diff hunk with the plan and issue.

Identify missing planned behavior, unrecorded changes, and contradictions between the implementation and description.

Accept documented deviations when they are consistent with the stated scope and honestly represented.

Record the specific plan statement or diff evidence that determines the check.

## 5. Check testing evidence

Compare the original reproduction steps with the before-fix observations and after-fix results.

Identify which planned tests were run and whether their outcomes are observable.

Inspect applicable repository-prescribed checks and their reported results.

Distinguish actual execution evidence from unsupported claims. Evaluate disclosed obstacles and alternative verification under the rubric.

## 6. Check diff reviewability

Inspect the changed-file list and meaningful hunks.

Identify unrelated refactors, generated debris, temporary debug code, and unexplained changes.

Determine whether a reviewer can understand the intended fix without unrelated work obscuring it.

Do not penalize commit count or formatting preferences alone.

## 7. Check repository standards

Read the repository's stated PR template and disclosure policy from the permitted evidence.

Verify that required template sections are substantively answered.

Check any explicitly required AI-use disclosure.

Do not invent missing standards or treat optional guidance as mandatory.

In live mode, separately report any applicable voice-guide violations.

## 8. Apply every rubric check

For every row in `rubric.md`:

1. Read the specified evidence.
2. Apply the written pass condition.
3. Assign `pass`, `fail`, or `unclear`.
4. Record one concise line of decisive evidence.

Do not change checks or their weights during the evaluation.

Missing evidence that prevents verification is `unclear`. Evidence demonstrating a violation is `fail`.

## 9. Determine the verdict

Return `accept` only when all required checks pass.

Return `reject` if any required check fails or is unclear.

Preferred checks must be reported but never change the verdict.

Do not automatically reject honestly disclosed limitations or documented deviations. Apply the actual rubric conditions.

## 10. Produce the output

Optionally provide a short readable summary identifying failures, uncertainties, and next actions.

End with exactly one fenced JSON block containing these fields in this order:

1. `item`
2. `checks`
3. `verdict`

Each check object must contain `name`, `grade`, and `evidence`, in that order.

Use the exact check names from `rubric.md`.

The verdict must be exactly `accept` or `reject`.

Do not add scores, extra fields, additional verdicts, or any text after the closing JSON code fence.