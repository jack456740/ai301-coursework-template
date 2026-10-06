# Rubric: is this reproduction package ready to post?

<!--
THIS IS THE PART YOU WRITE. The skill in SKILL.md executes whatever
checks you define here. It ships empty on purpose: the judgment is your
work.

A filled rubric must contain:

1. At least one row in the checks table. Each row needs all four
   columns:
   - Check: a short name (used in the output JSON).
   - Evidence: exactly what to look at, and where in the package. Name
     the part (the claim comment, the repro report's environment
     record, the artifacts read against the issue's description, the
     repo-facts block) or a location from your
     references/evidence-guide.md. "The report" is not a source; "the
     output excerpt read against the error the issue describes" is.
   - Pass condition: a decision rule about the OUTCOME that someone
     else could apply and get your answer. Judge the thing itself (does
     the artifact show the issue's behavior?), never the write-up's
     shape (how many steps it has, how long it is, whether it uses a
     template's headings). Structure-shaped checks are what make
     graders disagree with themselves.
   - Weight: `required` (a fail here holds the package) or `preferred`
     (never changes the verdict).

2. A verdict rule below the table: how the check grades combine into
   accept (ready) or reject (hold), including how `unclear` is
   treated. The verdict space is binary. If you write no rule for
   `unclear`, the skill treats it as fail.

Cover what actually gets bad packages posted. The lecture named the
proof families: the environment is recorded, the steps are complete
and followable, the behavior shown matches the issue (not an adjacent
one), the outcome is stated honestly (an evidenced cannot-reproduce is
a pass, a confident wrong-target is not), and the words respect the
repo's conventions. A rubric that ignores a family will fail eval
packages designed around that family.
-->

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment recorded | Repro report's environment record, read against the issue context and repo-facts block; use the Environment section of `references/evidence-guide.md` to locate and interpret the evidence. | Pass if the report records the environment details needed to interpret and repeat the attempted reproduction, and relevant differences from the issue's target environment are identified. Fail if a missing environment detail makes the result materially ambiguous or prevents a stranger from determining what was tested. | required |
| Steps reproducible | Repro report's reproduction steps and required setup, read against the issue description; use the Steps section of `references/evidence-guide.md`. | Pass if a stranger can follow the described setup and actions from a stated or reasonably identifiable starting state through the trigger without having to invent a material command, input, file, or configuration. | required |
| Target behavior evidenced | Repro report's output excerpts, logs, screenshots, or other artifacts read against the behavior described in the issue; use the Behavior shown section of `references/evidence-guide.md`. | Pass if the artifacts show the issue's target behavior when the report says it reproduced, or show the attempted trigger and different observed behavior when the report says it could not reproduce. Fail if the evidence demonstrates only an adjacent failure or does not support the reported target behavior. | required |
| Outcome honest | Repro report's stated conclusion read against its steps and artifacts; claim comment read against the work it promises; use the Honesty section of `references/evidence-guide.md`. | Pass if the stated outcome does not claim more than the evidence supports. An evidenced cannot-reproduce or inconclusive result passes; a claim of successful reproduction without evidence of the target behavior fails. | required |
| Repository conventions | Claim comment and repro comment read against the issue context, repo-facts contribution-policy information, and any applicable repository instructions; use the Comms section of `references/evidence-guide.md`. | Pass only if the comments comply with every explicit repository requirement that applies to issue comments. If the repository requires disclosure of AI assistance in comments, the submitted comments must contain that disclosure, including any required tool or extent information; absence of a required disclosure fails this check. If the repository explicitly says disclosure is not required for issue comments, do not require it. The claim must also identify the specific investigation without promising a guaranteed fix or completion date. | required |

## Verdict rule

Accept the package only if every required check passes. Reject the package if any required check fails or is unclear. Preferred checks, if added later, do not change the accept/reject verdict.