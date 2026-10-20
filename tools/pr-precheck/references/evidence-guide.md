# Evidence Guide: PR Precheck

This guide identifies the evidence sources used to evaluate one pull request package. Apply the checks defined in `rubric.md`; this guide does not introduce new grading criteria.

## 1. Plan Fidelity — Silent Drift

**Evidence sources:**
- Original issue requirements and acceptance criteria
- Posted implementation plan and test plan
- Explicitly recorded deviations from the plan
- PR branch diff, changed files, and commits
- PR title and description

**How to evaluate:**

Compare each meaningful changed behavior against the issue and planned scope. Identify changes outside the plan, planned requirements that are missing, and contradictions between the description and actual implementation.

A documented deviation is not automatically a failure. Determine whether the change remains consistent with the plan as amended.

**Decisive evidence:** Specific changed files, diff hunks, plan statements, or recorded deviations.

## 2. Test Evidence — Not Tested

**Evidence sources:**
- Issue reproduction steps
- Before-fix observations and failures
- After-fix test results
- Planned test cases
- Repository-documented testing commands
- Test output, logs, and disclosed testing limitations

**How to evaluate:**

Check whether the evidence demonstrates observable behavior rather than merely claiming success.

Compare the tests actually performed against the plan's test expectations. Verify that relevant repository checks were executed and their outcomes are visible.

If a check could not run, examine the documented reason and alternative verification. Do not automatically reject an honestly disclosed obstacle when meaningful evidence still establishes the intended behavior.

**Decisive evidence:** Commands, output, failure messages, passing test results, or explicit limitations.

## 3. Diff Quality — Unreviewable

**Evidence sources:**
- Complete changed-file list
- Actual diff hunks
- Commit history
- Issue scope and planned implementation boundaries
- Generated files, debug statements, unrelated formatting changes, and temporary artifacts

**How to evaluate:**

Determine whether a reviewer can identify the intended fix without unrelated changes obscuring it.

Reject unrelated code changes, unexplained scope expansion, or debris that materially reduces reviewability.

Do not reject a change solely because it has multiple commits, is short, or uses a different but understandable implementation style.

**Decisive evidence:** File paths, unrelated hunks, accidental artifacts, or focused changes.

## 4. Standards and Communication — Standards Wall

**Evidence sources:**
- Repository facts and contribution instructions
- Repository pull request template
- Explicit AI-use disclosure requirements
- Draft PR title and description
- Actual diff and test evidence
- In live mode only: repository policies, `scope.md`, and `voice-guide.md`

**How to evaluate:**

Identify the requirements the repository actually states. Check that required template sections are meaningfully completed and any mandatory disclosure is present.

Compare the PR description's claims with the implementation and evidence.

Do not invent policies, require unnecessary verbosity, or fail a PR for missing disclosure when the permitted evidence establishes no disclosure requirement.

In live mode, report voice-guide violations separately unless a rubric check makes them decisive.

**Decisive evidence:** Specific template requirements, policy text, disclosure language, and corresponding description content.

## Evidence Boundaries

### Live mode

Use the actual issue, posted plan, branch diff, commits, repository standards, PR template, and test evidence. Read `scope.md` first and use `voice-guide.md` for communication review.

### Eval mode

Use only the supplied package bundle. Never fetch missing information from GitHub, local files, or other external sources.

When evidence is missing or contradictory, assign `unclear` or `fail` according to the rubric. Never invent a successful test, a repository rule, or an undocumented plan deviation.