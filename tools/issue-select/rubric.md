# Rubric: is this a good first issue?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Maintainer alive | Repo-facts block: date of the last merged PR and the last maintainer comment (anywhere in the repo, not just this issue) | A maintainer merged a PR or commented anywhere in the repo within the last 60 days | required |
| Repo in use | Repo-facts block: release history, maintainer activity, issue activity | Evidence suggests the repository is actively maintained. Pass if there is a recent release, maintainer activity, recent merged pull requests, or issue-triage activity. Fail only when the repository appears abandoned, archived, or inactive. | required |
| Newcomer scope | Issue body and comment thread | Pass if a newcomer could make meaningful progress on the issue without being responsible for the final architectural decision. Issues involving investigation, debugging, multiple possible root causes, or several proposed solution directions still pass if the underlying problem is concrete and bounded. Fail only when the primary task is to design new architecture, define project direction, or conduct open-ended research. | required |
| Unclaimed | Comment thread and issue metadata (assignee field) | Pass only when the available evidence positively shows there is no assignee, no linked open PR closing the issue, and no recent claim comment. If the available bundle does not provide enough information to verify claim status, grade unclear. | required |
| AI contribution policy | `CONTRIBUTING.md`, `.github/` contributor docs, any `AI_POLICY.md`/`AI_USAGE_POLICY.md`, and PR/issue templates (references/evidence-guide.md, Family 5); "contribution policy" line under Repo facts in eval mode | Pass unless the policy states an outright ban on AI-generated or AI-assisted contributions. Conditions (disclosure, human review, testing, personal understanding) still pass — they are terms to follow, not reasons to reject. Silence on AI use passes. | required |
| Actionable requirements | Issue body and comments | Pass if a contributor can identify the problem to solve and begin investigation or implementation using the issue description and discussion. Confirmed root causes and detailed implementation instructions are not required. Fail only when the expected outcome remains substantially unclear after considering all available discussion. | required |
| Contribution availability | Issue metadata, linked PRs, and comment history | Pass if the issue appears to be a currently available contribution opportunity with a clear path for a newcomer to begin work. Fail if the issue primarily functions as an ongoing coordination effort, has accumulated many prior contributor attempts or linked PRs, or requires understanding substantial prior work before contributing meaningfully. | required |

## Verdict
Accept only if all required checks grade `pass`. Any required check
graded `fail` or `unclear` rejects the issue — unclear is treated as fail,
because a first issue you cannot verify is not one you should take. There
are no preferred checks in this rubric: personal fit is handled entirely
by the fit profile in `scope.md`, which ranks accepted issues but never
gates the verdict.