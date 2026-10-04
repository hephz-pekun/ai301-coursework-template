# Rubric: is this reproduction package ready to post?

## Checks

| Check | Evidence | Pass condition | Weight |
|---|---|---|---|
| Environment recorded | Repro report environment section; issue description; repo documentation | The report names the environment used to test the issue (platform, version, dependency version, commit, or other relevant runtime details) and provides enough context for another contributor to understand where the behavior was observed. | required |
| Reproduction steps | Repro report steps section and issue description | The report provides a complete path from starting state to observed result. A reasonable contributor could follow the described actions without guessing missing steps. | required |
| Behavior matches issue | Repro report artifacts (output, logs, screenshots, test results) read against the issue description | The evidence shown demonstrates the behavior described by the issue rather than a different failure or adjacent problem. | required |
| Honest outcome | Repro report conclusion and supporting evidence | The conclusion matches the evidence shown. Successful reproductions are supported by artifacts, and cannot-reproduce outcomes clearly state what was tried and what was observed. | required |
| Claim comment specificity | Claim comment read against the issue | The claim names the issue's actual problem and explains the contributor's next investigation step without promising a fix, timeline, or outcome. | required |
| Repo conventions | Claim comment, repro report, contribution policy, templates, and issue discussion | The package follows any stated repository conventions, including disclosure requirements, reporting expectations, or comment-format requirements. | required |
| Evidence quality | Output excerpts, logs, screenshots, or test results | The artifacts are directly relevant to the issue and are sufficient to support the report's conclusion. | preferred |

## Verdict rule

Accept if every required check grades `pass`. Preferred checks never
change the verdict. Any required check graded `fail` or `unclear`
rejects the package. In claim-only mode, checks that require a repro
report grade `unclear` with evidence `not yet applicable: claim-only
draft` and are excluded from the verdict; the verdict then answers
only whether the claim comment is ready to post.
