I reproduced the top-level JSON array failure described in issue #69.

The cause is in `rag/generator/output_parser.py`: `parse_review_output()` passes decoded JSON directly to `_parse_json_output()`, which assumes the result is a dictionary and calls `.items()`. A top-level JSON array instead produces a list, causing an AttributeError.

My proposed fix is to preserve dictionary-based JSON parsing while routing top-level arrays through the existing plaintext fallback. I will handle both raw and fenced JSON arrays, update the existing expected-failure regression test, and add a fenced-array test.

I will verify the change by running `tests/unit/test_output_parser.py` and checking that existing JSON-object and plaintext behavior remains unchanged.

One uncertainty is whether maintainers prefer structured handling of array elements. I am proposing the smaller plaintext fallback first to avoid expanding the issue's scope.

This plan was developed with assistance from ChatGPT and reviewed by me before posting.
