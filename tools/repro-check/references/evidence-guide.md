# Evidence guide: where proof lives in a reproduction package

## Environment

Where it lives: In an eval bundle, look at the reproduction report's environment record and compare it with the issue context and repo-facts block. In live mode, look at the draft reproduction comment, the issue, and repository documentation for relevant setup or version requirements.

What good looks like: The report identifies the environment details needed to interpret or repeat the reproduction, such as operating system, relevant runtime/tool versions, dependency or project revision when applicable. Those details should match the issue's target environment, or any meaningful difference should be stated.

## Steps

Where it lives: In an eval bundle, look at the reproduction report's steps and any setup information required before them. In live mode, read the draft reproduction comment together with the repository's setup instructions and issue description.

What good looks like: A stranger can follow the steps from a stated or reasonably identifiable starting state through the action that triggers the behavior. Required commands, inputs, files, or configuration that materially affect the reproduction are included rather than assumed.

## Behavior shown

Where it lives: In an eval bundle, inspect the reproduction report's artifacts such as command output, error excerpts, logs, screenshots, or other recorded observations, and read them against the behavior described by the issue. In live mode, compare the draft's evidence with the issue's expected and actual behavior.

What good looks like: The evidence demonstrates the same behavior the issue describes, not merely a nearby failure or an unsupported conclusion. For a successful reproduction, the observed artifact should contain the relevant symptom. For a cannot-reproduce result, the evidence should show the attempted trigger and the different behavior actually observed.

## Honesty

Where it lives: Compare the reproduction report's stated outcome with its steps and artifacts. Also compare the claim comment with what the student actually commits to doing.

What good looks like: The conclusion says no more than the evidence supports. A successful reproduction is reported as reproduced only when the artifacts show the target behavior, while an evidenced unsuccessful attempt is reported as cannot reproduce or inconclusive rather than being presented as confirmation.

## Comms

Where it lives: In an eval bundle, inspect the claim comment and reproduction comment against the issue context, repo-facts block, and any stated contribution policy, comment template, or disclosure requirement. In live mode, inspect the GitHub issue thread and repository contribution documentation alongside the draft comments.

What good looks like: The claim identifies the specific issue and promises investigation rather than a guaranteed fix or deadline. The reproduction comment is specific to the work performed and follows applicable repository conventions. Explicit repository requirements are binding: if AI assistance must be disclosed in issue comments, the comments must contain the required disclosure, including the tool or extent when the policy asks for it. If the policy explicitly limits disclosure to another surface such as pull requests, do not require disclosure in issue comments.