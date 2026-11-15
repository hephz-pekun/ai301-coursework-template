# Issue Scout Scan Output

## Scan Results (2026-11-11)

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

---

## Candidate Issue Grading (2026-11-11)

❯ claude "issue-scout: grade https://github.com/andrewsiah/agentswarm-data-tasks/issues/234 https://github.com/google/esmeralda/issues/164 https://github.com/andrewsiah/agentswarm-data-tasks/issues/235"

Same three URLs again; re-checking claim status since that's what can change.
❯ claude "issue-scout: grade https://github.com/andrewsiah/agentswarm-data-tasks/issues/234 https://github.com/google/esmeassistance in the PR'"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "SPEC.md contract plus pinned checker command"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened 2026-11-11, no prior attempts"}
  ], "verdict": "accept"}
]

✻ Brewed for 23s · done 3:52 PM

──────────────────────────────────────────────────────── 1 new message ─────────────────────────────────────────────────────────

※ recap: You're looking for a first open-source issue, and three candidates passed the rubric, with agentswarm-data-tasks#234 (a small Python function) the best fit. Next, pick one and comment /claim on it right away. (disable recaps in /config)

##2026-11-14 scan
 issue-scout: run a scan

● Skill(issue-scout)
Successfully loaded skill

  Ran 4 shell commands

Four queries done (about 400 raw results). Next I'm ranking them with the strategy's filters.

  Ran 1 shell command

Top 5 after ranking: sf-exit #14 and #13, btclib-node #2500, priompt python-sdk #26 and #25. Now I'm collecting the evidence the rubric asks for.

  Ran 2 shell commands

Now the AI-policy check: reading CONTRIBUTING/AGENTS docs for the three repos.

  Read 1 file, ran 4 shell commands

I ran the scan, and all 5 top-ranked candidates passed all 7 required checks. Two warnings before you pick one: all five were filed today in batches, and the ranking lifted the same kind of issue it did on 11-11.

Funnel: 400 raw results from the 4 queries → 397 unique → 354 with no assignee → 342 updated in the last 90 days → top 5 graded.

How they reached the top 5: query 1 (good first issue, Python) found all five, and queries 2–4 added none. Every survivor had the label, 0 comments, its repo appearing 2–4 times in the results, and an update today.

Accepted, in fit order

1. priompt/python-sdk #26: the client cache never removes expired entries. You'd add expiry and an LRU size limit using an OrderedDict. It's a small backend fix built around a data structure, which is the profile's sweet spot. The issue includes a repro, acceptance criteria, and test fixtures that already exist.
2. akhsterminator/sf-exit #13: find Leads that already exist as Contacts. It's a new audit finding in Python that follows an existing pattern. Tests run against a fake Salesforce org, so you don't need an account.
3. akhsterminator/sf-exit #14: find fields that only ever hold one value. You'd keep a capped count of distinct values per field in analyse_object. It's small data-structure logic, but the spec is thinner than #13's.
4. priompt/python-sdk #25: the NATS connection error shows port "None". The fix is about one line plus a test. It's well specified but teaches the least.
5. btclib-org/btclib-node #2500: a start with -server=0 is refused when -rpcservertimeout is out of range. The bug is well scoped, but it ranks last on fit for two reasons:
   - The test has to run against a real bitcoind v32.1, which is the build tooling your profile wants to avoid.
   - Outside contributors rarely get merged there: 3 of the last ~100 merged PRs came from outsiders, and 20+ outside PRs are still open.

No candidates were rejected.

Problems the verdicts hide

- Weak "Repo in use" passes. sf-exit was created today with 1 star, and priompt has 0 stars. Both pass only because they have a recent release.
- Strategy flaws from 11-11 are still unfixed. Ranking still favors brand-new issues filed in bulk, and queries 2–4 still add nothing to the top 5.
- Maintainer badge. priompt's maintainer shows a CONTRIBUTOR badge even though they merge every PR, so I judged "Maintainer alive" from merged PRs instead.
- Verdict wording. The verdict rule still says "five" required checks, but the table lists seven. I applied all seven.

I logged all of this in C:\Users\hephz\.claude\skills\issue-scout\scan-notes.md under the 2026-11-14 heading.

Once you pick one, comment on the issue right away to claim it, as scope.md says.

[
  {"item": "https://github.com/priompt/python-sdk/issues/26", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "Maintainer sujal-maheshwari2004 merged PR #12 on 2026-10-18 (27 days ago) and opened this issue today"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Release priompt-sdk 0.7.1 on 2026-10-18; 5 merged PRs that day; not archived"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "Bounded: remove expired entries and add an LRU limit in PromptClient; approach suggested by the maintainer"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "0 assignees, 0 comments, no cross-referenced or linked PRs, no open PRs in the repo"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "No CONTRIBUTING, AI policy, or PR template in the repo; silence passes"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "Repro script, expected behavior, file and line pointers, and a 3-item acceptance checklist"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened today, no prior attempts, test fixtures (FakeStub, clock) already exist"}
  ], "verdict": "accept"},
  {"item": "https://github.com/akhsterminator/sf-exit/issues/13", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "Owner akhsterminator commented and committed in the repo on 2026-11-14"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Release v0.1.0 published 2026-11-14; not archived (but created today, 1 star)"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "One new audit finding in audit.py, following the existing duplicate-email finding, plus one test"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "0 assignees, 0 comments, no linked PRs; only dependabot PRs are open"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "CONTRIBUTING.md and the PR template say nothing about AI use"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "'matches Lead.Email (where IsConverted = false) against Contact.Email, case-insensitively'"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened today; CONTRIBUTING lists this exact finding as a suggested contribution"}
  ], "verdict": "accept"},
  {"item": "https://github.com/akhsterminator/sf-exit/issues/14", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "Owner akhsterminator commented and committed in the repo on 2026-11-14"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Release v0.1.0 published 2026-11-14; not archived (but created today, 1 star)"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "Track a capped distinct count per field in analyse_object and report single-value fields"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "0 assignees, 0 comments, no linked PRs"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "CONTRIBUTING.md and the PR template say nothing about AI use"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "Names the function and the expected output: fields whose non-empty values are all identical"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened today; listed in CONTRIBUTING as a suggested finding"}
  ], "verdict": "accept"},
  {"item": "https://github.com/priompt/python-sdk/issues/25", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "Maintainer merged PR #12 on 2026-10-18 and opened this issue today"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Release 0.7.1 on 2026-10-18; not archived"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "Single-line fix suggested: 'Use u.port or 4222', plus a unit test"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "0 assignees, 0 comments, no linked or open PRs"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "No contribution or AI policy files; silence passes"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "Actual vs expected error message given, plus an acceptance checklist"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened today, no prior attempts"}
  ], "verdict": "accept"},
  {"item": "https://github.com/btclib-org/btclib-node/issues/2500", "checks": [
    {"name": "Maintainer alive", "grade": "pass", "evidence": "fametrano merged PRs #2489-#2496 on 2026-11-14"},
    {"name": "Repo in use", "grade": "pass", "evidence": "Release v2026.11.14 today; 18 stars; repo active since 2020; not archived"},
    {"name": "Newcomer scope", "grade": "pass", "evidence": "'Where to look: src/btclib_node/cli.py, _after_lock, the rpcservertimeout read'"},
    {"name": "Unclaimed", "grade": "pass", "evidence": "0 assignees, 0 comments, no cross-referenced PRs; none of the open PRs mention #2500"},
    {"name": "AI contribution policy", "grade": "pass", "evidence": "CONTRIBUTING.md: 'Development here is LLM-based'; AGENTS.md present"},
    {"name": "Actionable requirements", "grade": "pass", "evidence": "'Done when a start with -server=0 does not read -rpcservertimeout ... and a test runs that start against bitcoind'"},
    {"name": "Contribution availability", "grade": "pass", "evidence": "Opened today, no prior attempts or linked PRs"}
  ], "verdict": "accept"}
]

✻ Brewed for 2m 46s · done 6:03 PM

※ recap: I ran an issue-scout scan to find your first open-source issue, and all 5 top candidates passed, with priompt/python-sdk #26 (cache eviction) the best fit. Next, pick one and comment on the issue to claim it. (disable recaps in /config)

## Candidate Selection

Selected:
- sf-exit #13

Reason:
- Python project
- Clear implementation scope
- Existing test pattern to follow
- Issue remained unclaimed and available