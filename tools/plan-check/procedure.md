# Procedure: how this skill grades a plan package

<!--
THIS IS THE PART YOU WRITE, and it is a new kind of part. Weeks 1 and
2, SKILL.md carried a numbered workflow and you only wrote judgment
files. This week the workflow is gone from the frame: SKILL.md says
"execute procedure.md", and these are the operating steps you author.
The machinery is in your hands now.

Your operator swap is the design brief. When your executor stalled
because your rubric said WHAT to decide but not HOW to find the
evidence, that was a procedure gap. This file is where those gaps get
closed: a complete procedure lets someone who has never seen a plan
package before (a groupmate, or the skill itself) grade one exactly the
way you would.

Under each stage heading below, write the concrete steps for that
stage. The one-line note under each heading says what a complete
procedure must decide there. Write steps, not intentions: "read the
repro evidence before the plan, and note what behavior it pins down"
is a step; "understand the context" is a wish.
-->

## Read order

<!-- What gets read, in what order, before any check is graded, and
what to note down from each part while reading. A complete procedure
decides the order (issue first? repro evidence first?) and says why
the order matters for the checks that come later. -->

## Evidence gathering

1. Read `rubric.md` to identify every check, its evidence source, pass condition, and weight.
2. Read `references/evidence-guide.md` to locate the evidence for each check.
3. Read `voice-guide.md` and `scope.md` for communication rules and repository boundaries.
4. Read the issue context first. Record the reported failure, expected behavior, and any maintainer instructions.
5. Read the reproduction evidence. Record the triggering input, exact observed failure, traceback, environment, and reproduction command. Do not assume that the issue description alone proves the cause.
6. Read the candidate plan. Extract its diagnosis, in-scope and out-of-scope work, affected files, implementation steps, test plan, risks, unknowns, and deviations.
7. Read the draft plan comment. Record its proposed approach, test commitments, and any claims about existing evidence.
8. Read the repository facts and thread highlights. Record applicable contribution requirements, explicit AI-use disclosure policies, existing conventions, and maintainer guidance.
9. In live mode, use the corresponding GitHub issue, reproduction comment, repository files, and local drafts instead of evaluation-package blocks.
10. Record missing evidence as missing. Do not invent repository policies, maintainer decisions, test results, or implementation details.

## Check execution

Run the checks in the following order. Grade each check as `pass`, `fail`, or `unclear` using its exact rubric pass condition.

1. **Evidence-grounded diagnosis:** Compare the proposed cause with the observed reproduction. Confirm that the proposed change addresses the demonstrated failure mechanism, not merely the visible exception.
2. **Bounded change:** Compare the proposed in-scope and out-of-scope work with the issue's requested behavior. Reject unrelated features or unjustified broad refactoring.
3. **Executable implementation:** Check that the named files, code paths, and steps provide enough information for another contributor to begin implementing the change.
4. **Observable verification:** Compare the proposed tests with the original failing reproduction. Determine whether the tests would detect both the original failure and the expected corrected behavior.
5. **Honest uncertainty:** Compare assumptions and risks against established evidence. Check that material unknowns have a way to be investigated and that deviations are reported accurately when applicable.
6. **Thread and repository conventions:** Compare the draft comment with the thread highlights, repository facts, and voice guide. Apply explicit contribution and disclosure requirements, but never invent requirements not established by the evidence.

For each check:

- Assign `pass` only when the available evidence establishes the pass condition.
- Assign `fail` when evidence demonstrates a violation of the pass condition.
- Assign `unclear` when essential evidence is missing or ambiguous and the check cannot be decided.
- Cite the specific supporting or conflicting evidence in the check's rationale.
- Do not use the existence of headings, word counts, or document formatting as substitutes for evaluating the actual proposed outcome.
- Reuse the evidence gathered above instead of rereading the entire package for every check.
- If a check depends on information not provided, record that limitation rather than assuming success or failure.

## Verdict assembly

1. Collect the grades for all checks defined in `rubric.md`.
2. Return `accept` only if every required check has grade `pass`.
3. Return `reject` if any required check has grade `fail` or `unclear`. An `unclear` required check therefore holds the package.
4. Preferred checks, if present, may inform feedback but never change the verdict.
5. Identify the decisive required check or checks responsible for rejection. Quote the specific plan claim, reproduction fact, thread instruction, or missing evidence that explains the decision.
6. For an accepted package, identify the evidence demonstrating that the proposed change is bounded, executable, and verifiable.
7. Use the output format required by `SKILL.md`, including per-check grades, evidence-based rationales, and the final binary verdict.
8. Recommend concrete corrections for failed or unclear checks without rewriting the author's plan or inventing facts.