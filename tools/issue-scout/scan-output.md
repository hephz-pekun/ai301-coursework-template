
❯ issue-scout: run a scan

● Skill(issue-scout)
Successfully loaded skill

  Ran 4 shell commands

Found gh installed but not on PATH; checking auth, then running the four strategy queries.

  Ran 3 shell commands

Top 5 after ranking: andrewsiah/agentswarm-data-tasks #235, #234 and google/esmeralda #150, #164, #151. Gathering rubric evidence now.

  Ran 1 shell command

Quoting issue in PowerShell; switching to Bash with the full gh path.

  Ran 4 shell commands

● Write(scan-notes.md)
Wrote 17 lines to scan-notes.md
# Scan notes

## 2026-11-11 scan

Funnel: 400 raw results from 4 queries -> 398 unique -> 355 with no assignee -> 343 updated in the last 90 days
-> graded top 5.

Problems found while running the strategy and rubric:

- **The rubric's verdict rule says "all five required checks", but the table lists seven required checks.** I ap
… +9 lines (~2 KB)
Allowed by auto mode

Scan done: 3 of the top 5 candidates passed the rubric and 2 were rejected. The 4 queries returned 400 results, 398 of them unique. Dropping assigned issues left 355, and dropping anything not updated in the last 90 days left 343. I graded the top 5. All 5 came from query 1 (good first issue + Python). They ranked first because each has the label, 0 comments, its repo appears more than once in the results, and it was updated today.

Two things to know first:
- The rubric has an inconsistency. The verdict rule says "all five required checks" but the table lists seven required checks. I applied all seven.
- gh isn't on your PATH. I ran it from C:\Program Files\GitHub CLI\gh.exe.

Accepted (in fit order)

1. andrewsiah/agentswarm-data-tasks#234 (https://github.com/andrewsiah/agentswarm-data-tasks/issues/234): Fix cap_values
   - Fit: the best match for your profile. It's a small Python function about copying and capping a list, with a full spec and a checker script.
   - Caveat: the repo is 3 days old, has 1 star and is run by an AI agent. The issue says "production use … is not claimed", so this teaches you the contribution workflow, but nobody will run the code.
2. google/esmeralda#164 (https://github.com/google/esmeralda/issues/164): Validate agent model settings at test time
   - Fit: a Python backend validation task with real impact.
   - Caveats: you'd need to sign Google's CLA. The local setup (make test-all with uv, Envoy and Terraform) runs into your "avoid build tooling" preference. And every recent merged PR there was written by the one maintainer, so it's unproven that outside contributions get merged.
3. andrewsiah/agentswarm-data-tasks#235 (https://github.com/andrewsiah/agentswarm-data-tasks/issues/235): isSubsequence
   - Fit: the weakest. It's a JavaScript task, even though the repo is mostly Python, and it has the same "nobody runs it" caveat as #234.
   - First-timers only until 2026-11-12 20:10 UTC.

Rejected

- google/esmeralda#150 (https://github.com/google/esmeralda/issues/150): platform SLOs. Failed Newcomer scope: you would be setting the platform's targets and the rationale for them. Also failed Contribution availability: it needs a deployed dev environment to load-test, plus context from earlier issues #77 and #178.
- google/esmeralda#151 (https://github.com/google/esmeralda/issues/151): Envoy usage records. Failed Contribution availability: it builds on the usage-record format that was only merged today (#133), and needs the Envoy and Terraform setup.

If you decide to take one, comment /claim on it right away; both repos' contributing guides ask for that, and claiming upstream is your scope's rule. Both repos also allow AI assistance as long as you disclose it in the PR.

I logged the problems this scan exposed in C:\Users\hephz\.claude\skills\issue-scout\scan-notes.md. The main ones:
- The ranking favors brand-new issues. Because of "fewer comments" and "repo appears more than once", the top 5 were all opened today by people filing issues in bulk.
- The label preference does nothing. Every query already requires the good first issue label.
- Queries 2–4 add nothing. Query 1 already covers their results.
- The Python filter goes by the repo's language, not the issue's. That's how a JavaScript task got in.
- The rubric is missing a few checks. Nothing covers a repo nobody actually uses, whether outside contributors get merged, or CLA requirements.

[
  {"item": "https://github.com/andrewsiah/agentswarm-data-tasks/issues/234", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "PR #222 merged by owner andrewsiah 2026-11-11; owner commented 2026-11-11T20:10"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Not archived; 6+ PRs merged 2026-11-11 (no releases, repo created 2026-11-08)"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "Scope: `tasks/cap-values/cap_values.py` only; 'Effort: 30–60 minutes; beginner-friendly'"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "assignees=0, no linked PRs, 0 comments, no open PR references #234"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "'Humans, bots and AI-assisted contributors are welcome; disclose AI assistance in the PR'"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "Full contract in body + tasks/cap-values/SPEC.md + pinned checker command"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened 2026-11-11, no prior attempts or linked PRs; standalone task"}
  ], "verdict": "accept"},
  {"item": "https://github.com/google/esmeralda/issues/164", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "PR #133 merged by amenegola (COLLABORATOR) 2026-11-11T17:10"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Not archived, 25 stars, 6 PRs merged 2026-11-10..11, active issue triage"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "'Validate thinking level, max output tokens and model location against the model family in agent tests and at startup'; Effort: S"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "assignees=0, no linked PRs, 0 comments, no PR mentions #164"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "No ban; contributing.md has a 'Working with AI coding agents' section and repo ships AGENTS.md"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "AC: 'A test fails for an unsupported setting. The agent refuses to start with a clear message.'"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened 2026-11-11, no prior attempts; self-contained validation"}
  ], "verdict": "accept"},
  {"item": "https://github.com/andrewsiah/agentswarm-data-tasks/issues/235", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "PR #222 merged by owner andrewsiah 2026-11-11"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Not archived; 6+ PRs merged 2026-11-11"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "Scope: `tasks/is-subsequence/is_subsequence.mjs` only; 'Effort: 30–60 minutes'"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "assignees=0, no linked PRs, 0 comments; 'First-timers only for 24 hours'"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "'AI-assisted contributors are welcome; disclose AI assistance in the PR'"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "SPEC.md contract plus pinned checker command"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened 2026-11-11, no prior attempts"}
  ], "verdict": "accept"},
  {"item": "https://github.com/google/esmeralda/issues/150", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "PR #133 merged by amenegola 2026-11-11"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Not archived; 6 PRs merged 2026-11-10..11"},
    {"name": "Newcomer scope", "grade": "fail", "evidence": "'Targets set from measured baselines' / 'Targets and rationale documented': contributor would define the platform's SLO targets"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "assignees=0, no linked PRs, 0 comments"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "No ban; AGENTS.md shipped"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "Four concrete acceptance criteria listed"},
    {"name": "Contribution availability", "grade": "fail", "evidence": "'Every SLO shows data after a `dev` load test' needs a deployed GCP env; folds in items 'from #77' and #178"}
  ], "verdict": "reject"},
  {"item": "https://github.com/google/esmeralda/issues/151", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "PR #133 merged by amenegola 2026-11-11"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Not archived; 6 PRs merged 2026-11-10..11"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "One bounded artifact: 'An Envoy JSON access-log format that emits gateway.request records'"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "assignees=0, no linked PRs, 0 comments"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "No ban; AGENTS.md shipped"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "Record fields named (verified caller, route, status, latency, trace_id) and 2 AC"},
    {"name": "Contribution availability", "grade": "fail", "evidence": "Builds on the esmeralda.usage contract merged today (#133) and the Envoy/Terraform gateway harness: substantial prior work to absorb"}
  ], "verdict": "reject"}
]

✻ Cogitated for 3m 9s · done 3:21 PM

※ recap: You asked for an issue-scout scan for a first contribution, and it's finished: three issues passed, with agentswarm-data-tasks #234 (a small Python list function) the best fit. Next, pick one and comment /claim on it right away. (disable recaps in /config)
