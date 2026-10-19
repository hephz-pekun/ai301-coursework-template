# Rubric: is this pull request ready to submit?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Plan fidelity | Branch diff, plan scope, deviation notes, PR description | Pass if every change in the diff is inside the plan's scope or explicitly explained by a deviation note. Fail if the diff silently adds work, omits planned work without explanation, or the PR description claims behavior the diff does not deliver. | required |
| Evidence supports the change | Test evidence, plan test plan, repro evidence, repo checks | Pass if the PR provides observable evidence for the behavior being changed and describes how validation was performed. Evidence may include before/after behavior, reproduced results, automated test output, or explicitly reported execution of planned tests. Fail only when testing is absent, unrelated to the planned behavior, or provides no reasonable basis for the claimed result. | required |
| Reviewable diff | Unified diff and commit list | Pass if the change is focused on the planned fix and contains no unrelated edits, temporary files, debug code, commented-out blocks, or drive-by refactors. | required |
| Standards and disclosure | PR description, PR template, CONTRIBUTING guidance, disclosure requirements | Pass if all required template sections are completed with real content and all stated disclosure requirements are satisfied. Fail if required sections are missing, boilerplate, or omitted. | required |
| Honest delivery | Diff, test evidence, PR description, deviation notes | Pass if limitations, deviations, deferred work, or failed checks are disclosed when present. Fail if evidence contradicts claims of completeness or if a known deviation is hidden. | required |

## Verdict rule

Accept if every required check passes.

Reject if any required check grades fail or unclear.

Preferred checks never change the verdict.

Unclear counts as fail because a pull request that cannot be verified is not ready to submit.