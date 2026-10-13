# Unit 3 — Plan and Build

## Posted upstream

**GitHub username**

hephz-pekun

**Plan comment**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/53#issuecomment-6133196884

Plan for issue #53

Diagnosis:
The behavior documented in my reproduction comment shows that (555) 123-4567 is not detected or redacted, while 555-123-4567 is handled correctly.

Scope:
Update US phone-number matching so parenthesized phone numbers are detected consistently with existing supported formats. This work is limited to the phone-matching logic and related tests.

Files/areas:
- safety/pii_scrubber.py
- tests/unit/test_pii_scrubber.py

Branch: 
fix/53-parenthesized-phone

Validation:
I will rerun the reproduction script from my repro report, verify that the parenthesized format is both detected and redacted after the change, and confirm that the issue #53 xfailed tests pass after the associated xfail markers are removed.

---


## Your branch

**Branch**

fix/53-parenthesized-phone

https://github.com/hephz-pekun/pathreview-ai301-fa26-howard/tree/fix/53-parenthesized-phone

**Evidence**

### Before

Command:

```powershell
python repro.py
```

Output:

```text
Call me at (555) 123-4567 or [REDACTED]
2026-10-05 16:21:49 [info     ] pii_detected count=0 types=0
[]
```

Command:

```powershell
pytest tests/unit/test_pii_scrubber.py
```

Output:

```text
20 passed, 5 xfailed
```

### After

Command:

```powershell
python repro.py
```

Output:

```text
Call me at [REDACTED] or [REDACTED]
2026-10-12 18:23:22 [info     ] pii_detected count=1 types=1
[{'type': 'phone_us', 'value': '(555) 123-4567', 'start': 11, 'end': 25}]
```

Command:

```powershell
pytest tests/unit/test_pii_scrubber.py
```

Output:

```text
25 passed in 0.34s
```

The parenthesized phone number is now detected and redacted correctly.
The issue #53 xfailed tests were removed, and the test suite passes
without XPASS(strict) failures.

---

## Eval iterations

**Run history**

19/20

My first full evaluation run achieved 19/20 scored items, which
exceeded the required passing threshold. I reviewed the one
disagreement (pkg-14) and ran targeted `--only` evaluations to
understand why my rubric and the gold label differed.

The disagreement involved how much evidence a plan needs before a
suspected cause can be discussed. I experimented with small
adjustments to the Diagnosis grounded, Executable by a stranger, and
Honest uncertainty checks and re-ran canary packages from the
wrong-cause category to avoid weakening protections elsewhere.

The targeted runs did not improve agreement without increasing risk to
other categories, so I kept the rubric in its passing state. My final
full evaluation remained 19/20 scored items. This score matches the
agreement line in `eval-run.txt`.

**Package analysis**

I analyzed pkg-14.

My rubric rejected the package, while the gold label accepted it.

The package failed the Diagnosis grounded and Honest uncertainty checks
under my rubric. My interpretation was that the plan stated a
suspected mechanism more confidently than the available reproduction
evidence supported.

The gold label accepted the package, suggesting that the benchmark was
comfortable with a stronger working hypothesis as part of a valid
plan. This disagreement showed that my rubric was stricter than the
benchmark about how much evidence is required before a suspected cause
can appear in a plan.

**Check rationale**

Current rubric wording:

"Pass if the diagnosis follows from behavior shown in the repro evidence or is clearly presented as a working hypothesis to investigate. The diagnosis does not need to prove the root cause before implementation begins. Fail if the diagnosis contradicts the reproduced behavior or presents unsupported assumptions as confirmed facts."

I chose this wording because planning often begins before the exact
root cause has been proven. The check allows investigation-driven
hypotheses while still requiring the diagnosis to remain tied to
observed reproduction evidence. This helps distinguish
evidence-based planning from unsupported speculation.

**Trade-offs**

The Diagnosis grounded check can reject plans that contain plausible
explanations when those explanations are presented as established
facts rather than working hypotheses. I tested revisions against
pkg-14 and wrong-cause canary packages, but they did not improve
overall agreement without risking regressions elsewhere. I therefore
kept the stricter version of the check and accepted the single
disagreement.

---

Related paths: `plan.md` and `eval-run.txt` in this directory; your
skill's files in `tools/plan-check/`.