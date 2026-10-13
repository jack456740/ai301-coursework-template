# Implementation Plan — Path Review Issue #69

Issue: https://github.com/codepath/pathreview-ai301-fa26-howard/issues/69
Branch: fix/69-json-array-fallback

## Diagnosis

The reproduction demonstrates that a top-level JSON array causes `AttributeError: 'list' object has no attribute 'items'`.

In `rag/generator/output_parser.py`, `parse_review_output()` decodes JSON and passes the result to `_parse_json_output()`. That helper assumes its input is a dictionary and immediately calls `.items()`. A valid JSON array decodes to a Python list, so this assumption causes the crash.

## Scope

In scope:
- Handle top-level JSON arrays without crashing.
- Preserve existing dictionary-based JSON parsing.
- Turn the existing expected-failure regression test into a normal test.
- Verify both raw JSON and fenced JSON behavior.

Out of scope:
- Redesigning the feedback schema.
- Changing unrelated RAG or LLM generation logic.
- Fixing the separate seeded accumulator defect.

## Implementation

1. Update `rag/generator/output_parser.py` so decoded JSON is passed to `_parse_json_output()` only when it is a dictionary.
2. For decoded JSON arrays, return `_parse_plaintext_output(raw)` so the original feedback remains available.
3. Apply this handling to both the fenced-JSON and raw-JSON paths.
4. Update `tests/unit/test_output_parser.py` by removing `xfail` from `test_json_array_fallback` and asserting that the fallback returns one `general_feedback` section containing the original text.
5. Add coverage for a fenced JSON array.

## Verification

Before: `test_json_array_fallback` fails with an AttributeError when run with `--runxfail`.

After:
- The array regression test passes without `xfail`.
- The fenced-array regression test passes.
- Existing JSON-object and plaintext tests continue to pass.

Command:
`.venv\Scripts\python.exe -m pytest tests/unit/test_output_parser.py -v`

## Risks and Unknowns

The issue demonstrates the array crash but does not establish a required structured mapping for array elements. Preserving the original text through the existing plaintext fallback is the minimal approach; confirm that this matches maintainer expectations before expanding the behavior.

The parser has another seeded defect involving an unused `sections` accumulator. That is unrelated and will remain unchanged.

## Deviations

None at planning time. Record any implementation changes here before completion.
