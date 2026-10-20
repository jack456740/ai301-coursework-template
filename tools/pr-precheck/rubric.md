# Rubric: Is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity | Issue requirements, posted plan including recorded deviations, diff's changed files and behavior | The diff implements the planned change within its stated boundaries, including explicitly recorded deviations. No unrecorded scope expansion, missing essential behavior, or contradiction between implementation and plan. An honestly disclosed limitation is acceptable when the implemented outcome remains within the plan and its recorded deviations. | required |
| Description accuracy | PR title and description compared with actual diff, issue, and plan | The description accurately identifies the change and its observable behavior. Claims about fixes, coverage, limitations, and deviations do not contradict the diff. No unsupported claims of completed work. | required |
| Reproduction evidence | Issue reproduction steps, before/after results, and the plan's test expectations | Evidence shows the original behavior and the changed behavior through observable commands, results, or test output. A documented inability to reproduce is acceptable when its reason is explicit and alternative verification credibly establishes the intended change. Unsupported statements such as "tested successfully" do not pass. | required |
| Repository checks | Repo-facts block, repository-prescribed commands, PR test evidence, and reported outcomes | Applicable repository-prescribed checks have identifiable execution outcomes, including specific test counts, named commands with results, or concrete before/after observations. A credible, specific report such as `cargo test -p nu-protocol` passing 312 tests is sufficient; raw terminal logs are not mandatory. A generic claim such as "all tests pass" without identifiable checks or results is insufficient. A specific inability to run a check may be acceptable when honestly explained and supported by meaningful alternative verification. | required |
| Diff reviewability | Changed-file list, diff hunks, commits, and issue scope | Changes are focused on the issue and understandable to a reviewer. No unrelated refactors, generated debris, temporary debugging, accidental files, or unexplained changes that obscure the implementation. The number of commits alone is not a failure. | required |
| Template compliance | Repo-facts PR template and required sections compared with the draft description | Every section explicitly required by the repository's PR template contains substantive, truthful information or an appropriate explanation that it does not apply. Do not invent requirements absent from the repository facts. | required |
| AI-use disclosure | Repository AI policy, PR template disclosure requirements, and PR description | Any disclosure explicitly required by the repository is present and truthful. If no disclosure requirement is established by the available evidence, absence of an AI disclosure alone does not fail the check. | required |
| Communication quality | PR title, description, issue context, and applicable repository communication rules | The title identifies the change, the description gives reviewers sufficient context to understand what changed, why, and how it was verified, and the text does not materially mislead reviewers. Conciseness is acceptable; length and polish alone do not determine readiness. | preferred |

## Verdict rule

Grade every check as `pass`, `fail`, or `unclear`.

- **pass:** The specified evidence satisfies the check's pass condition.
- **fail:** The evidence demonstrates a violation of the pass condition.
- **unclear:** The package lacks enough evidence to establish the pass condition or its outcome cannot be verified.

Return **`accept`** only when every `required` check passes.

Return **`reject`** when any `required` check fails or is unclear.

Preferred checks never change the verdict, but their results must still be reported.

An honestly disclosed limitation, test obstacle, or plan deviation is not automatically a failure. Evaluate whether the actual evidence meets the check's stated condition.

Do not invent missing repository standards. Apply template and disclosure requirements only when established by the permitted repository evidence.

In eval mode, use only the supplied package bundle. In live mode, use the actual repository evidence allowed by `scope.md` and `procedure.md`.

Every check must have one concise evidence line in the final JSON output. The final JSON must follow `CONTRACT.md` exactly.