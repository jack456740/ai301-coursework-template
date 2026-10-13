# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

Where it lives: In evaluation mode, compare the candidate plan's diagnosis and approach with the issue context and reproduction-evidence block, especially the triggering input, observed result, and traceback. In live mode, use the GitHub issue, posted reproduction comment, and draft plan.

What good looks like: The diagnosis explains the reproduced failure and identifies the implicated code path. A proposed change must address the cause demonstrated by the evidence, not simply suppress the exception or contradict the observed behavior.

## Scope

Where it lives: Read the plan's in-scope and out-of-scope statements, named files, and proposed changes against the issue's requested behavior.

What good looks like: The work is one coherent change addressing the issue. Regression tests are appropriate; unrelated features, broad refactoring, and unsupported expansions are not.

## Executability

Where it lives: Examine the plan's files, functions, implementation steps, and repository facts. In live mode, inspect the affected source code and tests.

What good looks like: Another contributor can identify where to begin, what behavior to change, and what existing behavior to preserve without inventing a major missing decision.

## Test plan

Where it lives: Compare the plan's test commands, inputs, and expected results with the reproduction-evidence block. In live mode, use the posted reproduction and relevant repository tests.

What good looks like: Tests exercise the original failure path, specify observable expected behavior, and distinguish the broken implementation from the proposed fix. Include regression checks for previously supported behavior.

## Honesty

Where it lives: Compare the plan's assumptions, risks, unknowns, and deviations with the issue, reproduction evidence, and repository facts.

What good looks like: Verified observations are separated from hypotheses. Material unknowns have investigation or validation steps. Deviations are reported accurately, including an explicit statement when none occurred.

## Comms

Where it lives: Compare the draft plan comment with issue thread highlights, maintainer guidance, repo facts, contribution policies, and the voice guide. In live mode, inspect the GitHub issue and repository documentation.

What good looks like: The comment explains the specific proposed approach and verification, respects relevant maintainer direction, and follows explicit repository requirements, including AI-use disclosure when actually required. It does not piggyback another plan or guarantee unverified results.
