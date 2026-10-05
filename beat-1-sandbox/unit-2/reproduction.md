
# Unit 2 — Claim and Reproduce

Path: `beat-1-sandbox/unit-2/reproduction.md`

Record of your claim and reproduction on the issue you chose in Unit 1, and of the
evaluation runs that produced `eval-run.txt`. This file is graded at the path above; a copy
kept anywhere else in the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the wrong
label is not graded.

---

## Your identity upstream

**GitHub username**

hephz-pekun

---

## Posted upstream

**Claim comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/53#issuecomment-6001171781

I'd like to work on this issue.

The reported behavior shows that parenthesized US phone numbers such as
(555) 123-4567 are not being detected or redacted by the PII scrubber.

My next step is to reproduce the issue locally using the provided
example and referenced tests, then document the results in a
reproduction report before investigating potential causes.

**Reproduction comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/53#issuecomment-6002425695

Environment

- Windows 11
- Python 3.13.14
- Commit: 99673c7
- Ran from the repository root with the project virtual environment activated

Steps

1. Activated the project's virtual environment.
2. Created and ran the following script:

```python
from safety.pii_scrubber import PIIScrubber

s = PIIScrubber()

print(s.scrub("Call me at (555) 123-4567 or 555-123-4567"))
print(s.detect("Call me at (555) 123-4567"))
```

3. Ran:

```text
pytest tests/unit/test_pii_scrubber.py
```

Observed

Script output:

```text
Call me at (555) 123-4567 or [REDACTED]
[]
```

Additional output:

```text
2026-10-05 16:21:49 [info] pii_detected count=0 types=0
```

The parenthesized phone number remained unredacted while the dashed
phone number was replaced. `detect()` also returned an empty list for
the parenthesized phone number.

Test result:

```text
20 passed, 5 xfailed
```

The 5 xfailed tests are the tests associated with issue #53, including
the tests referenced in the issue description.

Expected

The parenthesized phone number `(555) 123-4567` should be detected and
redacted in the same way as `555-123-4567`.

Conclusion

I successfully reproduced the behavior described in this issue. The
parenthesized format `(555) 123-4567` is not detected or redacted,
while the dashed format `555-123-4567` is handled correctly.

## Eval iterations

Answer all four sections. Quote source text directly; paraphrase does not satisfy these
fields.

**Run history**

19/20

My first and final  rubric focused on the lecture's proof families: environment recording, reproduction steps, behavior shown, honest reporting, claim specificity, repository conventions, and evidence quality.

The final full evaluation achieved 19/20 scored items, exceeded the required passing threshold of 18/20, and satisfied every category requirement. The final score matches the agreement line in eval-run.txt.

**Package analysis**

I analyzed pkg-12.

My rubric rejected the package, while the gold label accepted it.

The package failed the Reproduction steps and Repo conventions checks under my rubric. My interpretation was that the reproduction instructions did not provide enough followable detail and that the package did not fully satisfy the repository's expected reporting conventions.

The gold label accepted the package, suggesting that the benchmark considered the provided evidence sufficient. This disagreement showed that my rubric was slightly stricter than the benchmark regarding the amount of detail needed in a reproduction report.

**Check rationale**


Current rubric wording:

"The conclusion matches the evidence shown. Successful reproductions are supported by artifacts, and cannot-reproduce outcomes clearly state what was tried and what was observed."

I chose this wording because the assignment emphasizes evaluating the
quality of reproduction evidence rather than the formatting of the
report. The check focuses on whether another contributor could verify
the behavior being reported and whether the package provides sufficient
supporting evidence for its conclusion.

**Trade-offs**

This check may allow packages that do not follow a repository's preferred style when that style is not explicitly required. I accepted that trade-off because the goal is to enforce stated contribution rules rather than personal preferences. The revised check reduced false rejections while still protecting against failures to follow mandatory disclosure or reporting requirements.


Related paths: eval-run.txt in this directory; your skill's files in tools/repro-check/.

---
