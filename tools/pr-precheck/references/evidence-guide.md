# Evidence guide: where evidence lives in a PR package
# Evidence guide: where evidence lives in a PR package

## Plan fidelity (harness category: silent-drift)

### Where it lives

Eval mode:
- Plan-context scope section
- Plan-context deviation notes
- Candidate PR diff
- Candidate PR description

Live mode:
- plan.md
- Deviation Notes section in plan.md
- git diff main...HEAD
- pr_draft.md

### What good looks like

Every changed file falls within the plan's stated scope or an explicit
deviation note. The description accurately describes what the diff
actually implements.

## Test evidence (harness category: not-tested)

### Where it lives

Eval mode:
- Test-evidence section
- Plan-context test plan
- Reproduction evidence

Live mode:
- test_evidence.md
- plan.md test plan
- Repository test output

### What good looks like

The before state, after state, and validation commands are observable.
Success is demonstrated rather than simply claimed.

## Diff quality (harness category: unreviewable)

### Where it lives

Eval mode:
- Commit list
- Unified diff

Live mode:
- git diff main...HEAD
- Commit history

### What good looks like

The intended fix is easy to review. No unrelated files, temporary
artifacts, debugging output, commented code, or formatting churn hide
the change.

## Standards and comms (harness category: standards-wall)

### Where it lives

Eval mode:
- Repo-facts block
- Candidate PR title
- Candidate PR description

Live mode:
- PR template
- CONTRIBUTING.md
- pr_draft.md
- Issue thread guidance

### What good looks like

Every required template section contains meaningful content. Disclosure
requirements are satisfied. Repository-specific instructions are
followed.