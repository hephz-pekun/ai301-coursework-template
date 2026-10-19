# Procedure: how this tool grades a PR package

## Read order

1. Read the issue context.
2. Read the accepted plan and deviation notes.
3. Read the PR title and description.
4. Read the branch diff.
5. Read the test evidence.
6. Read repository standards and template requirements.

The plan is read before the diff so the implementation can be checked
against the intended scope.

## Evidence gathering

Plan fidelity
- Record scope boundaries.
- Record deviation notes.
- Record changed files and claimed outcomes.

Evidence supports the change
- Record planned validation steps.
- Record executed validation steps.
- Record before and after evidence.

Reviewable diff
- Record changed files.
- Record unrelated modifications.
- Record temporary or debugging artifacts.

Standards and disclosure
- Record required PR-template sections.
- Record disclosure requirements.
- Record repository-specific instructions.

Honest delivery
- Record limitations.
- Record deviations.
- Record disclosed failures or deferred work.

## Check execution

Execute checks in rubric order.

If required evidence for a check is unavailable, grade the check
unclear.

A check may be graded using gathered evidence without rereading the
entire package.

Report procedure gaps instead of inventing missing steps.

## Verdict assembly

Apply the rubric's verdict rule exactly.

Accept when every required check passes.

Reject when any required check fails or is unclear.

When multiple required checks fail, report the first failing required
check in rubric order as the deciding failure.