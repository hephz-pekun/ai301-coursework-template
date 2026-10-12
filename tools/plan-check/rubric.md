# Rubric: is this plan ready to post and build from?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Diagnosis grounded | Plan diagnosis read against the repro evidence block | Pass if the diagnosis follows from behavior shown in the repro evidence or is clearly presented as a working hypothesis to investigate. The diagnosis does not need to prove the root cause before implementation begins. Fail if the diagnosis contradicts the reproduced behavior or presents unsupported assumptions as confirmed facts. | required |
| Bounded scope | Plan scope statement, out-of-scope statement, files/areas section | Pass if the plan describes one bounded change and clearly limits what will not be changed. Fail if the plan expands into unrelated improvements, refactors, or multiple independent fixes. | required |
| Executable by a stranger | Files/areas, approach section, implementation steps | Pass if another contributor could begin executing the planned investigation or implementation work without needing clarification from the author. Exact functions, lines, or final implementation details do not need to be known if the target areas and next actions are clearly identified. Fail if the plan leaves the next actions or areas of work substantially unspecified. | required |
| Test-decisive | Test plan read against the repro evidence | Pass if the test plan states observable success conditions and describes how the repro evidence will be re-run or adapted to verify the fix. Fail if success is defined only in vague terms such as "works correctly". | required |
| Honest uncertainty | Risks, unknowns, and deviation notes | Pass if assumptions, risks, hypotheses, and unknowns are identified where the evidence does not justify certainty. Working theories and suspected causes are acceptable when presented as hypotheses rather than established facts. Fail when speculation is presented as confirmed behavior or confirmed root cause without supporting evidence. | required |
| Comment faithful | Plan comment read against the plan document and thread context | Pass if the comment accurately reflects the plan's stated scope, approach, and test plan without promising work that the plan does not contain. | required |
| Repo conventions | Plan comment, repo contribution policy, templates, thread guidance | Pass if the package follows stated repository conventions, contribution requirements, and thread expectations. Do not fail for optional formatting preferences. | required |

## Verdict rule

Accept if every required check grades `pass`. Any required check graded
`fail` or `unclear` rejects the package. Unclear counts as fail because
a plan that cannot be verified is not ready to post or build from.