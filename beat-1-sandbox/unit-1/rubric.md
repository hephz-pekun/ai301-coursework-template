# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer alive | Repo-facts block: date of the last merged PR and the last maintainer comment (anywhere in the repo, not just this issue) | A maintainer merged a PR or commented anywhere in the repo within the last 60 days | required |
| Repo in use | Repo-facts block: date of the most recent release/tag, and open-issue vs. closed-issue count if given | Most recent release/tag is within the last 12 months, OR the issue thread itself shows a maintainer engaging with it within 60 days | required |
| Newcomer scope | Issue body and comment thread | Issue body names a specific file, function, or component AND describes an expected before/after behavior, with no more than one component touched | required |
| Unclaimed | Comment thread and issue metadata (assignee field) | No assignee is set, AND no comment links an open PR that closes this issue, AND no claim comment in the last 14 days (house rule: in live-mode Path Review, other students' claim comments never fail this check regardless of age) | required |
| AI contribution policy | `CONTRIBUTING.md`, `.github/` contributor docs, any `AI_POLICY.md`/`AI_USAGE_POLICY.md`, and PR/issue templates (references/evidence-guide.md, Family 5); "contribution policy" line under Repo facts in eval mode | Pass unless the policy states an outright ban on AI-generated or AI-assisted contributions. Conditions (disclosure, human review, testing, personal understanding) still pass — they are terms to follow, not reasons to reject. Silence on AI use passes. | required |

## Verdict rule

Accept only if all five required checks grade `pass`. Any required check
graded `fail` or `unclear` rejects the issue — unclear is treated as fail,
because a first issue you cannot verify is not one you should take. There
are no preferred checks in this rubric: personal fit is handled entirely
by the fit profile in `scope.md`, which ranks accepted issues but never
gates the verdict.
