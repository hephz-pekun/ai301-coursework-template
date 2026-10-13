# Plan for Issue #53: PII scrubber fails to redact parenthesized US phone numbers

## Diagnosis

The reproduction shows that the PII scrubber correctly handles the
dashed format `555-123-4567` but fails to handle the parenthesized
format `(555) 123-4567`.

Observed during reproduction:

```text
Call me at (555) 123-4567 or [REDACTED]
[]
```

The dashed number is detected and redacted.

The parenthesized number is not.

This suggests the issue is likely related to how the current US phone pattern handles parenthesized formats. Further inspection of the implementation is required to confirm the exact cause.

## Scope
In scope
Update US phone number detection so parenthesized phone numbers such as
(555) 123-4567 are detected and redacted consistently with existing
supported US phone formats.

Out of scope
Changes to email detection.
Changes to international phone detection.
Changes to unrelated PII patterns.
Broader refactoring of the PII scrubber.

## Files / Areas
safety/pii_scrubber.py
tests/unit/test_pii_scrubber.py
pyproject.toml (if any issue #53-related test configuration exists)

## Branch

fix/53-parenthesized-phone


## Approach
Inspect the phone_us regular expression in safety/pii_scrubber.py.

Compare the regex behavior between:

- 555-123-4567
- (555) 123-4567

Modify the pattern so parenthesized formats are matched while existing
supported formats continue to pass.

Remove the issue #53 `@pytest.mark.xfail` markers from the affected
   tests once the behavior is fixed.

Verify that previously xfailed tests now pass without producing
   `XPASS(strict)` failures.

## Test Plan

### Before

Observed during reproduction:

```text
Call me at (555) 123-4567 or [REDACTED]
[]
```

Test result:

```text
20 passed, 5 xfailed
```

### Expected after

Expected output:

```text
Call me at [REDACTED] or [REDACTED]
```

`detect()` should return at least one phone-related PII match instead of:

```text
[]
```

Expected test result:

```text
25 passed
```

with the issue #53 xfail markers removed and no `XPASS(strict)` failures.

The reproduction script from Unit 2 will be rerun after the change and
the results compared against the expected output above.

## Risks and Unknowns
Updating the phone regex could affect existing phone-number matching
behavior.

The current diagnosis is based on observed behavior and inspection of
the existing pattern. Additional investigation may reveal a more
specific cause.

## Deviation Notes

During implementation, an additional issue was discovered in the
`street_address` pattern. After updating the phone-number matching
logic, the test suite exposed a false positive that incorrectly
redacted non-PII text.

To restore the expected behavior and achieve a passing test suite,
the `street_address` regex was narrowed so that ordinary prose would
not be treated as an address.

This change was not anticipated in the original plan but was required
to satisfy the existing tests after the phone-number fix was completed.