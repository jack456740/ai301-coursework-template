# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/69

**Verdict output**

```text
Issue Select — Live Mode

Issue: Output parser crashes on a top-level JSON array fallback (#69)

Maintainer activity: PASS
Repository activity: PASS
Manageable scope: PASS
Unclaimed: PASS
Contribution policy: PASS

Verdict: ACCEPT
```

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/69",
  "checks": [
    {
      "name": "Maintainer activity",
      "grade": "pass",
      "evidence": "Latest default-branch commit was by Aburke225 (collaborator), within 90 days of 2026-10-05; no issue comments yet."
    },
    {
      "name": "Repository activity",
      "grade": "pass",
      "evidence": "All 5 of the last 5 commits (2026-08-24 to 2026-09-16) are within 90 days."
    },
    {
      "name": "Manageable scope",
      "grade": "pass",
      "evidence": "Bounded parser bug with an existing failing test; labels include good first issue and tier-1."
    },
    {
      "name": "Unclaimed",
      "grade": "pass",
      "evidence": "Assignees: none; no comments; no referenced or linked PRs."
    },
    {
      "name": "Contribution policy",
      "grade": "pass",
      "evidence": "docs/CONTRIBUTING.md has no AI ban or restriction; only workflow conditions such as commenting to claim, keeping CI green, and removing the xfail marker."
    }
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

**Run history**

```text
Full run: 15/20
Targeted rerun of issue-03, issue-04, issue-12, issue-13, issue-18: 5/5
Full run after rubric revision: 18/20
Final saved full run: 18/20
```

My first scored full run reached 15/20. I inspected the five disagreements instead of changing the rubric only to match the gold labels. After revising the evidence and pass conditions, I reran those five issues with `--only` and reached 5/5. I then ran the full evaluation again and reached 18/20. The final full run saved to `eval-run.txt` also scored 18/20 and met the category floor.

**Issue analysis**

I analyzed `issue-03`, which my original rubric accepted even though the gold label was reject. The issue contained a maintainer statement saying that they were not looking for contributions other than a specific contributor's PR. My original `Unclaimed` check only considered evidence from the last 30 days, which could allow an explicitly reserved issue to pass after enough time. I changed the check to consider assignments, explicit reservations, contributors already working on an issue, and open linked pull requests. With the revised rubric, `issue-03` was correctly rejected.

**Check rationale**

Current `Unclaimed` check:

> Pass if the issue has no assignee, there is no open linked pull request addressing it, no contributor states that they have started or are currently working on it, and no maintainer explicitly reserves it for another contributor.

I chose this form because the evaluation showed several different ways that an issue can already be taken. `issue-03` was explicitly reserved, `issue-12` had a contributor who had already started working, and `issue-13` and `issue-18` had open linked pull requests. Checking all of these signals is more reliable than using only assignment status or a fixed time window.

**Trade-offs**

The stricter `Unclaimed` check can reject an issue even when an existing contributor or pull request has become inactive. I accepted that trade-off because for a first contribution I would rather avoid duplicating active work than assume an existing claim is stale. I reran `issue-03`, `issue-04`, `issue-12`, `issue-13`, and `issue-18` after making the changes, and all five matched their gold labels. The final full evaluation still passed at 18/20.

---

## Selection rationale

**Selection rationale**

1. Issue #69 fits my interests because it is a small debugging task involving application code rather than only documentation or a test-data adjustment. It is labeled as a good first issue and tier-1, and the existing failing test gives me a clear way to reproduce the problem and check my fix. That makes the scope reasonable for the time I have available.

2. The verdict correctly identified that the repository is active, the issue is bounded, there is no linked pull request or assignee blocking it, and the contribution policy allows the work. I also compared it with the other accepted candidate, issue #63. Although #63 appeared smaller, I chose #69 because debugging the parser gives me more practice with the kind of software debugging and testing I want to improve.

3. I expect claiming the issue to be straightforward but not automatic. The contribution instructions require commenting on the issue before starting, and another student could also choose it. Path Review's house rule says student claim comments do not block an issue, so another student's claim would not necessarily prevent me from working on it. I will still follow the repository's contribution instructions before beginning the implementation.

---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
