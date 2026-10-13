# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Evidence-grounded diagnosis | Plan's stated cause compared with issue context and reproduction evidence, especially triggering input, observed output, and traceback. | Pass if the cause is supported by reproduced behavior and the change addresses the demonstrated failure mechanism. Fail if it contradicts evidence, assumes an unsupported cause, or treats only the symptom. | required |
| Bounded change | Plan's in-scope and out-of-scope statements compared with the issue's requested behavior and proposed implementation. | Pass if the work is one coherent, bounded change needed for the issue. Fail if it introduces unrelated functionality, broad refactoring, or unjustified changes. | required |
| Executable implementation | Plan's named files, code paths, and steps compared with repository facts and the reproduction's starting state. | Pass if another contributor could begin implementation without inventing a material decision and the steps target the implicated code path. Fail if the steps are vague or target unrelated code. | required |
| Observable verification | Plan's test inputs, commands, and expected results compared with the reproduced failure and expected behavior. | Pass if tests exercise the original failure path, distinguish failing from corrected behavior, and check previously supported behavior. Fail if they cannot demonstrate the proposed fix. | required |
| Honest uncertainty | Plan's assumptions, risks, unknowns, and deviations compared with reproduction evidence and repository facts. | Pass if consequential unknowns are acknowledged with validation steps and facts are distinguished from hypotheses. Fail if unsupported assumptions are presented as certain or material unknowns are ignored. | required |
| Thread and repository conventions | Draft plan comment compared with issue thread highlights, maintainer guidance, repo-facts contribution policies, and explicit AI-use requirements. | Pass only if the comment follows relevant maintainer direction and every applicable explicit repository requirement. If repository policy requires disclosure of AI assistance in issues or comments, the candidate comment itself must state the AI tool used and the extent of assistance; a disclosure elsewhere or silence is insufficient. Fail if the required disclosure is missing, even when the technical plan is sound. Do not invent disclosure requirements for repositories without such a policy. | required |

## Verdict rule

Accept only if every required check passes. Reject if any required check fails or is unclear. Unclear counts as fail for the final verdict. Preferred checks, if any, never override required checks.

