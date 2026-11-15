# Scan notes

## 2026-11-11 scan

Funnel: 400 raw results from 4 queries -> 398 unique -> 355 with no assignee -> 343 updated in the last 90 days -> graded top 5.

Problems found while running the strategy and rubric:

- **The rubric's verdict rule says "all five required checks", but the table lists seven required checks.** I applied all seven. Fix the verdict text so it matches the table.
- **The "prefer good first issue label" filter does nothing.** All four queries already require that label, so every result has it.
- **"Prefer fewer comments" ends up favoring brand-new issues.** All top 5 had 0 comments and were opened today by two people creating issues in bulk. Repos that open lots of issues at once take over the ranking. Ideas: require the issue to be at least a few days old, or cap how many results one repo can have in the top N.
- **"Prefer repos that appear more than once" makes that worse.** agentswarm-data-tasks had 16 hits and bondbench had 8, so the bulk filers come out ahead.
- **Queries 2-4 (test / bug / llm) added nothing to the top 5.** Query 1 has no keyword, so its results already cover theirs. All five survivors came from query 1.
- **`--language python` filters by the repo's language, not the issue's.** agentswarm #235 is a JavaScript task in a Python-majority repo.
- **"Repo in use" passed a repo the rubric doesn't really mean to pass.** andrewsiah/agentswarm-data-tasks is 3 days old, has 1 star and no releases, is run by an AI agent, and says "production use by agentswarm.space is not claimed". It passes on "recent merged PRs", which is exactly the "merged PR nobody runs" case. Consider a check on adoption (stars or dependents) or on real-world use.
- **No check asks whether outside contributors get merged.** All of google/esmeralda's recent merged PRs were written by the one collaborator (amenegola). There's also a Google CLA requirement, which no check covers either.
- **The setup cost of the dev environment isn't graded.** In esmeralda, `make test-all` needs uv, Envoy and Terraform, which runs into the fit profile's "avoid build tooling". Fit doesn't change verdicts, so this only shows up in the ranking.
