# Evidence guide: where proof lives in a reproduction package

## Environment

### Where it lives

Eval mode:
- Repro report environment section.
- Issue context.
- Repo-facts block.

Live mode:
- Reproduction comment draft.
- Repository setup instructions.
- Issue requirements.

### What good looks like

The report identifies the environment that produced the observation.
The environment information is sufficient for another contributor to
understand where the behavior was observed and how it relates to the
issue's target setup.

## Steps

### Where it lives

Eval mode:
- Repro report steps section.

Live mode:
- Reproduction draft.
- Issue description.
- Repository documentation.

### What good looks like

A newcomer could repeat the actions and reach the same state without
guessing missing actions. The report describes the path from setup to
observation.

## Behavior shown

### Where it lives

Eval mode:
- Output excerpts.
- Logs.
- Screenshots.
- Test results.

Live mode:
- Reproduction draft artifacts.

### What good looks like

The artifacts clearly demonstrate the behavior described by the issue.
The evidence should show the reported problem itself rather than a
different failure.

## Honesty

### Where it lives

Eval mode:
- Repro conclusion.
- Supporting artifacts.

Live mode:
- Claim comment.
- Reproduction draft.
- Attached evidence.

### What good looks like

The conclusions match the evidence. A successful reproduction shows the
problem. A cannot-reproduce report accurately records the attempts made
and the observed outcome without overstating certainty.

## Comms

### Where it lives

Eval mode:
- Claim comment.
- Repro report.
- Repo-facts policy section.

Live mode:
- Issue thread.
- Draft comments.
- CONTRIBUTING.md.
- Issue and PR templates.
- Disclosure requirements.

### What good looks like

Comments are specific to the issue, follow repository conventions, and
satisfy any disclosure or reporting requirements. The contributor
describes what they did, what they observed, and what they plan to do
next without making unsupported promises.