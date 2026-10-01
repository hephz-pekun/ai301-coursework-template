# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

[The individual Path Review issue page. A link to the repository or the issue list
does not satisfy this field.]

**Verdict output**

[Your skill's live-mode output for this issue, pasted verbatim and ending with the
fenced JSON verdict block. A summary does not satisfy this field.]

**The verdict must record `accept` for this issue.** Choose an issue your own skill
accepts. If your skill rejects every candidate you try, that is a signal about your
rubric rather than about the issues: revise it and re-run — retries are unlimited and a
partial re-run costs about $0.20 — or run the skill on different candidates. Output
recording `reject` for the issue you chose earns no credit for this field.

```
# Unit 1 — Issue Selection

Path: `beat-1-sandbox/unit-1/selection.md`

Record of the issue carried into Unit 2, and of the evaluation runs that produced
`eval-run.txt`. This file is graded at the path above; a copy kept anywhere else in
the repository is not read.

Complete every labelled field below. Each is graded on its own; content placed under the
wrong label is not graded.

---

## Selected issue

**Issue link**

https://github.com/codepath/pathreview-ai301-fa26-howard/issues/53

**Verdict output**

Issue #53: PII scrubber fails to redact parenthesized US phone numbers. This is a live-mode run, inside the scoped repo codepath/pathreview-ai301-fa26-howard, using evidence from the GitHub REST API on 2026-10-01.

Check | Grade | Evidence
---|---|---
Maintainer alive | pass | Collaborator Aburke225 committed on 2026-09-16 and commented in the repo on 2026-09-16. That's 15 days ago, well inside 60.
Repo in use | pass | Not archived. The last push was 2026-09-16, there are 76 open issues being triaged with labels, and 5 open student PRs. There are no releases and no merged PRs, which is normal for a classroom repo.
Newcomer scope | pass | It's a single bug in one regex in safety/pii_scrubber.py, with reproduction steps and four named failing tests.
Unclaimed | pass | No assignees, no comments, and none of the 5 PRs in the repo mentions #53, phone or PII.
AI contribution policy | pass | The repo has no CONTRIBUTING.md, AI_POLICY.md or PR template, and silence passes.
Actionable requirements | pass | The issue states what you see now and what should happen instead, and names the tests that define "done".
Contribution availability | pass | It's freshly filed (2026-09-14), carries a good first issue label, and has no earlier attempts or linked PRs.

Verdict: accept.

Fit: This matches your profile well. It's a small backend Python function, and the work is regex and pattern-matching logic rather than CSS or build tooling. The likely cause shows in the code: phone_us starts with \b. A word boundary can't match right before (, so the area code's opening bracket is never picked up. The pattern also doesn't allow the space after ) in (555) 123-4567. Run tests/unit/test_pii_scrubber.py before and after your change to confirm the fix.

```json
{
  "item": "https://github.com/codepath/pathreview-ai301-fa26-howard/issues/53",
  "checks": [
    {
      "name": "Maintainer alive",
      "grade": "pass",
      "evidence": "Collaborator Aburke225 committed and commented in the repo on 2026-09-16, 15 days before 2026-10-01"
    },
    {
      "name": "Repo in use",
      "grade": "pass",
      "evidence": "archived: false; last push 2026-09-16; 76 open labelled issues; 5 open contributor PRs"
    },
    {
      "name": "Newcomer scope",
      "grade": "pass",
      "evidence": "Single bug in the phone_us regex in safety/pii_scrubber.py with repro steps and four named failing tests"
    },
    {
      "name": "Unclaimed",
      "grade": "pass",
      "evidence": "assignees: none; 0 comments; no PR among the repo's 5 references #53, phone, or PII"
    },
    {
      "name": "AI contribution policy",
      "grade": "pass",
      "evidence": "No CONTRIBUTING.md, AI_POLICY.md, AI_USAGE_POLICY.md, or PR template in repo; silence passes"
    },
    {
      "name": "Actionable requirements",
      "grade": "pass",
      "evidence": "Body gives observed vs expected output for '(555) 123-4567' and lists failing tests in tests/unit/test_pii_scrubber.py"
    },
    {
      "name": "Contribution availability",
      "grade": "pass",
      "evidence": "Opened 2026-09-14 with 'good first issue' label; no prior attempts or linked PRs"
    }
  ],
  "verdict": "accept"
}
```

---

## Eval iterations

Quote source text directly in each field below. Paraphrase does not satisfy them.

**Run history**

[The agreement score of each run you did, in order. A single run is a complete answer if
only one run occurred. **The last score in your list must match the agreement line in the
`eval-run.txt` you committed** — that file is the record of your final run.]
15/20

The initial rubric used five required checks: Maintainer alive, Repo in use,
Newcomer scope, Unclaimed, and AI contribution policy. The first full run
scored 15/20, with most misses caused by an overly strict Newcomer scope
check.

16/20

I broadened Newcomer scope and added an Actionable requirements check.
This improved agreement on several accepted issues but still missed some
borderline cases.

17/20

I refined the wording of Newcomer scope and experimented with additional
checks to distinguish open-ended work from bounded contribution tasks.

18/20 

I added a Contribution availability check and adjusted the scope criteria
to focus on whether a newcomer could make meaningful progress without
being responsible for architectural decisions. The final full evaluation
passed the required threshold and met the category floor. The agreement
score in this section matches the final score recorded in eval-run.txt.

20/20(final)
Further iteration improved the handling of contribution history and
availability while preserving acceptance of legitimately bounded newcomer
issues. The final evaluation achieved perfect agreement across all scored
issues and satisfied every category requirement.

**Issue analysis**

[One scored issue, identified by id (`issue-01` through `issue-20`; the `calib-`
issues are not scored). State your rubric's decision, the gold label, and the
reasoning that produced your rubric's result.]

I analyzed issue-19.

My rubric rejected the issue, while the gold label accepted it.

The issue described a bug with multiple possible root causes and several
suggested solution directions. My rubric interpreted this as evidence
that the work required significant investigation and therefore failed
the Newcomer scope check.

The gold label treated the issue differently because the underlying
problem was still bounded and concrete. This mismatch showed me that my
rubric was sometimes confusing exploratory debugging with architectural
ownership. As a result, I revised the Newcomer scope wording to focus on
whether a newcomer could make meaningful progress without being
responsible for defining the final design.

**Check rationale**

[One check from the `rubric.md` uploaded to `tools/issue-select/`, quoted as it is
currently written, with the reasoning behind its current form.]
Current rubric wording:
 
Current rubric wording:

"Accept only if all required checks grade `pass`. Any required check
graded `fail` or `unclear` rejects the issue — unclear is treated as fail,
because a first issue you cannot verify is not one you should take. There
are no preferred checks in this rubric: personal fit is handled entirely
by the fit profile in `scope.md`, which ranks accepted issues but never
gates the verdict."

I chose this wording because earlier versions of the rubric rejected
issues whenever the root cause or implementation path was uncertain.
Those versions incorrectly classified several acceptable newcomer issues
as too complex. The updated wording focuses on whether the problem is
bounded and actionable rather than whether every technical detail is
already known.

**Trade-offs**

[What the quoted check gives up. Any one of these is a complete answer: an issue whose
result it changes, a canary you re-ran with `--only`, a case you accept it will miss, or a
stated reason nothing changed elsewhere. "Nothing changed, and here is how I know" earns
the point in full when the reason follows.]

Earlier versions of the rubric traded precision for simplicity and either
accepted long-running coordination issues or rejected legitimate beginner
tasks. The final version balances those concerns by requiring both a
bounded scope and evidence that the issue remains an available
contribution opportunity. The final evaluation achieved 20/20 agreement,
suggesting that these trade-offs aligned well with the benchmark.

---

## Selection rationale

Graded on whether all three are answered, in your own words. Not on how good the
reasoning is, and not on length — a short honest answer to each earns the full marks.
This is also the basis for the claim comment you write in Unit 2.

**Selection rationale**

[Answer all three:

1. The issue's fit to your interests and to the time available.
2. What the verdict identified correctly, and what you weighed that the rubric could
   not.
3. The anticipated difficulty in claiming it.]

1. The issue fits my interests because it involves a small backend Python
bug in the PII scrubbing logic rather than frontend styling, design, or
build tooling. The scope appears realistic for the available time and
matches my goal of gaining backend implementation experience.

2. The verdict correctly identified that the repository is active, the
issue is unclaimed, and the task is newcomer-friendly. In addition to
the rubric's checks, I considered my personal interest in backend and
security-related functionality. Since the bug affects PII detection and
redaction, it aligns well with the kinds of problems I want to learn
from.

3. Claiming the issue should be relatively straightforward because there
are no comments, linked pull requests, or previous contributor attempts
associated with the issue. Compared with other candidate issues, there
is less risk of duplicating someone else's work.
---

Related paths: `eval-run.txt` in this directory; your skill's files in
`tools/issue-select/`.
