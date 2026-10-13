# Unit 3 — Plan and Build

Path: `beat-1-sandbox/unit-3/plan-and-implement.md`

Record of your plan, the branch you built it on, and the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in the
repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Posted upstream

jack456740

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/69#issuecomment-6137988097

I reproduced the top-level JSON array failure described in issue #69.

The cause is in `rag/generator/output_parser.py`: `parse_review_output()` passes decoded JSON directly to `_parse_json_output()`, which assumes the result is a dictionary and calls `.items()`. A top-level JSON array instead produces a list, causing an AttributeError.

My proposed fix is to preserve dictionary-based JSON parsing while routing top-level arrays through the existing plaintext fallback. I will handle both raw and fenced JSON arrays, update the existing expected-failure regression test, and add a fenced-array test.

I will verify the change by running `tests/unit/test_output_parser.py` and checking that existing JSON-object and plaintext behavior remains unchanged.

One uncertainty is whether maintainers prefer structured handling of array elements. I am proposing the smaller plaintext fallback first to avoid expanding the issue's scope.

This plan was developed with assistance from ChatGPT and reviewed by me before posting.

---

## Your branch

**Branch**

`fix/69-json-array-fallback`

GitHub fork: https://github.com/jack456740/pathreview-ai301-fa26-howard

Commit: https://github.com/jack456740/pathreview-ai301-fa26-howard/commit/45f2748

**Evidence**

**Before implementation**

I reproduced issue #69 using the existing `test_json_array_fallback` regression test with pytest's `--runxfail` option:

` .venv\Scripts\python.exe -m pytest tests/unit/test_output_parser.py -k test_json_array_fallback --runxfail -v `

The test failed with an `AttributeError` because `_parse_json_output()` attempted to call `.items()` on a Python list produced by `json.loads()`.

The original parser assumed that all successfully decoded JSON values were dictionaries.

**After implementation**

I updated `rag/generator/output_parser.py` to check the decoded JSON type. Dictionaries continue through `_parse_json_output()`, while arrays and other non-dictionary values use `_parse_plaintext_output(raw)`.

I also removed the existing test's `xfail` marker, added assertions verifying the `general_feedback` section and preserved input, and added `test_fenced_json_array_fallback`.

I ran:

` .venv\Scripts\python.exe -m pytest tests/unit/test_output_parser.py -v `

The output included:

`tests/unit/test_output_parser.py::TestOutputParser::test_json_array_fallback PASSED`

`tests/unit/test_output_parser.py::TestOutputParser::test_fenced_json_array_fallback PASSED`

`20 passed in 0.11s`

I also ran `git diff --check`, which reported no whitespace errors.

The fix was committed as `45f2748` and pushed to my fork. No pull request was opened during Unit 7.
I also reproduced the failure directly using the original parser from Git history, without modifying my fixed working files.

Command run from the Path Review repository:

```powershell
@'
import subprocess
import types

source = subprocess.check_output(
    ["git", "show", "45f2748^:rag/generator/output_parser.py"],
    text=True
)

parser = types.ModuleType("original_output_parser")
exec(compile(source, "original_output_parser.py", "exec"), parser.__dict__)

print("BEFORE FIX: Original parser with a top-level JSON array")
result = parser.parse_review_output('[{"section_name": "general_feedback", "content": "Test"}]')
print(result)
'@ | .\.venv\Scripts\python.exe -
```

Actual terminal output:

```text
BEFORE FIX: Original parser with a top-level JSON array
Traceback (most recent call last):
  File "<stdin>", line 13, in <module>
  File "original_output_parser.py", line 48, in parse_review_output
  File "original_output_parser.py", line 68, in _parse_json_output
AttributeError: 'list' object has no attribute 'items'
```

This confirms that the original parser crashes when given a top-level JSON array.

## Eval iterations

**Run history**

I completed one full scored evaluation run using the `plan-check` skill and the Sonnet model.

The final result recorded in `eval-run.txt` was:

`agreement: 19/20 scored items  (bar: 18/20: PASS)`

This represents 95% agreement, exceeding the required 90% threshold.

The category results were:

- Clear-accept: 6/7
- Scope-creep: 4/4
- Thread-convention: 2/2
- Unbuildable: 3/3
- Wrong-cause: 4/4

**Package analysis**

I selected `pkg-14`, which was the only disagreement in the final evaluation.

The recorded results were:

- Package: `pkg-14`
- Category: `clear-accept`
- Gold label: `accept`
- My rubric's verdict: `reject`
- Agreement: `NO`

The evaluator reported:

`failed: Evidence-grounded diagnosis, Executable implementation, Honest uncertainty`

My rubric rejected the plan because it judged the diagnosis, implementation steps, and uncertainty handling insufficient under those three required checks.

However, the gold label was `accept`, so this was a false rejection. The result suggests that the rubric can apply its evidence and implementation requirements too strictly to an otherwise acceptable plan.

**Check rationale**

I selected the following check from `tools/plan-check/rubric.md`:

> Thread and repository conventions | Draft plan comment compared with issue thread highlights, maintainer guidance, repo-facts contribution policies, and explicit AI-use requirements. | Pass only if the comment follows relevant maintainer direction and every applicable explicit repository requirement. If repository policy requires disclosure of AI assistance in issues or comments, the candidate comment itself must state the AI tool used and the extent of assistance; a disclosure elsewhere or silence is insufficient. Fail if the required disclosure is missing, even when the technical plan is sound. Do not invent disclosure requirements for repositories without such a policy. | required |

I revised this check to distinguish explicit repository policies from requirements that the evaluator might otherwise assume.

The final wording requires AI-use disclosure in the candidate comment when the repository explicitly requires it. It also prevents the evaluator from inventing disclosure requirements for repositories without such a policy.

This makes the check more closely aligned with actual repository contribution rules.

**Trade-offs**

The revised check prioritizes documented repository requirements over imposing a universal AI-disclosure rule.

A plan comment that does not disclose AI assistance will not automatically fail this check if the repository has no explicit disclosure requirement.

This is an intentional trade-off because the skill should evaluate compliance with the repository's actual policies rather than introduce additional requirements.

The final evaluation achieved 19/20 agreement, including correct decisions for both thread-convention packages (`pkg-04` and `pkg-20`).

The remaining false rejection on `pkg-14` shows a separate limitation: the rubric may be too strict when judging evidence, implementation detail, and uncertainty in otherwise acceptable plans.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your skill's files in
`tools/plan-check/`.
