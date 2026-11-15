## Queries

# I want to contribute to Python projects and work on bug fixes that are suitable for first-time contributors.
gh search issues --label "good first issue" --language python --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

# I enjoy writing and improving tests.
gh search issues test --label "good first issue" --language python --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

# I prefer debugging and fixing existing functionality over building large new features.
gh search issues bug --label "good first issue" --language python --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

# I am interested in AI and LLM-related projects when beginner-friendly opportunities are available.
gh search issues llm --label "good first issue" --language python --state open --limit 100 --json title,repository,labels,assignees,commentsCount,updatedAt,url

## Ranking filters

- drop any result with an assignee
- drop any result not updated in the last 90 days
- prefer issues with the "good first issue" label
- prefer fewer comments over more comments
- prefer repositories that appear more than once in the search results
- use most recently updated as the final tie-breaker

## How many to grade

Grade the top **5** ranked results per scan.