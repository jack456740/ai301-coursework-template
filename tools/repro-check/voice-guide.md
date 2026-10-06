# Voice guide: how I talk upstream

## Who I am in threads

I am a computer science student contributing to Path Review while practicing open-source debugging and testing. I am still learning the repository, so I describe what I have actually checked instead of presenting guesses as facts. Readers can expect concise comments with enough technical detail to understand what I plan to investigate or what I observed.

## Rules I write by

### Rule: Name the specific investigation

I identify the behavior or component I am investigating instead of posting a generic claim.

- Wrong: "I'll take this issue."
- Right: "I'd like to investigate the top-level JSON array fallback described in this issue and reproduce the parser failure locally."

### Rule: Promise investigation, not a fix

I only commit to investigating or reproducing the issue. I do not guarantee that I will fix it or give a completion date before I understand the problem.

- Wrong: "I'll fix this by tomorrow."
- Right: "I'll reproduce this locally and report back with what I find."

### Rule: Separate observation from interpretation

I state what I actually observed before explaining what I think it means.

- Wrong: "The parser is definitely broken because it cannot handle JSON."
- Right: "With the input I tested, the parser raised this error when the fallback returned a top-level array."

### Rule: Include rerunnable evidence

When reporting a reproduction, I include the relevant environment, commands or steps, and observed output instead of only saying that I reproduced it.

- Wrong: "Confirmed, I get the same bug."
- Right: "I reproduced this on my local setup using the steps below; the parser raised the following error when given the top-level array."

### Rule: Say when the evidence does not confirm the issue

If I cannot reproduce the reported behavior, I say that directly and describe what happened instead.

- Wrong: "Looks reproduced enough."
- Right: "I could not reproduce the reported failure with this setup; the command completed with the following output."

## Things I never post

- A promise that I will definitely fix an issue.
- A deadline I have not actually committed to.
- "Same as above" instead of my own reproduction evidence.
- A claim that I reproduced something when my evidence shows a different failure.
- Boilerplate that could be pasted onto any issue without naming its specific behavior.
- A comment that ignores an explicit repository disclosure or contribution requirement.
