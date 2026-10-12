# Procedure: how this skill grades a plan package

## Read order

1. Read the issue context.
2. Read the reproduction evidence.
3. Record the observed behavior established by the evidence.
4. Read the full plan.
5. Read the plan comment.
6. Read repository conventions and thread guidance.

The repro evidence is read before the plan so that diagnosis and test
claims can be checked against the established observations.

## Evidence gathering

Diagnosis grounded:
- Record observed behavior from repro evidence.
- Record the diagnosis stated by the plan.

Bounded scope:
- Record the in-scope, out-of-scope, and files/areas statements.

Executable by a stranger:
- Record implementation steps, approach, and named files.

Test-decisive:
- Record test plan actions and expected-after behavior.

Honest uncertainty:
- Record stated risks, assumptions, and unknowns.

Comment faithful:
- Record promises, scope, and claims from the plan comment and compare
  them to the written plan.

Repo conventions:
- Record thread guidance, repo policy, and contribution requirements.

## Check execution

1. Execute Diagnosis grounded.
2. Execute Bounded scope.
3. Execute Executable by a stranger.
4. Execute Test-decisive.
5. Execute Honest uncertainty.
6. Execute Comment faithful.
7. Execute Repo conventions.

If required evidence is genuinely missing, grade the check `unclear`.

Each check should be graded using only the evidence gathered for that
check and the stated rubric condition.

## Verdict assembly

Apply the rubric's verdict rule.

If every required check passes, return `accept`.

If any required check is graded `fail` or `unclear`, return `reject`.

For each failed check, quote the specific evidence that determined the
result.