# Evidence guide: where evidence lives in a plan package

## Diagnosis and grounding

### Where it lives

Eval:
- Repro-evidence block
- Diagnosis section

Live:
- Posted reproduction comment
- plan.md diagnosis section

### What good looks like

The diagnosis attempts to explain behavior actually shown in the
reproduction evidence. A diagnosis should not assume a root cause that
the evidence has not yet established.

## Scope

### Where it lives

Eval:
- Scope section
- Files/areas section

Live:
- plan.md scope statements
- plan comment

### What good looks like

The plan identifies a single bounded change and clearly identifies what
is not part of the change. The files or areas affected are named.

## Executability

### Where it lives

Eval:
- Files/areas section
- Approach section

Live:
- plan.md implementation approach

### What good looks like

A contributor unfamiliar with the issue could begin execution without
needing further clarification from the author.

## Test plan

### Where it lives

Eval:
- Test plan section
- Repro-evidence block

Live:
- plan.md test plan
- posted repro evidence

### What good looks like

The plan specifies exactly what evidence will demonstrate success and
relates that evidence to the original reproduction.

## Honesty

### Where it lives

Eval:
- Risks section
- Unknowns section
- Deviations section

Live:
- plan.md
- plan comment

### What good looks like

Known uncertainties are acknowledged. Assumptions are identified as
assumptions rather than established facts.

## Comms

### Where it lives

Eval:
- Plan comment
- Repo-facts block

Live:
- Issue thread
- CONTRIBUTING documentation
- Plan comment

### What good looks like

The comment reflects the actual plan, responds appropriately to thread
context, and follows any repository requirements.