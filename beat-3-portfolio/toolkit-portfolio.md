# Toolkit Portfolio

Path: `beat-3-portfolio/toolkit-portfolio.md`

This file is Assignment 6, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. It has been waiting here since you created the repo in unit 1;
unit 9 is when you write it.

**Only this page is read.** Your `tools/` folders and your installed skill folders are never
opened, so every piece of evidence you want seen has to live inline here: an output excerpt,
a before/after pair, a dated commit reference.

**Write every sentence yourself.** AI may gather diffs, dates and excerpts for you; it does
not draft entries.

**Keep every section header below under its exact name** — Featured Tools, Inventory, The
Arc, and Limitations and What's Next. Feature three or four tools, each in the entry shape
shown below; give every other tool one inventory line.

**Some lines below are labelled, and the label is how they are read.** Three places on this
page use a `Label: your words` shape — the arc's beats, the tool-limits list, and nothing
else. Keep those labels exactly as written, one per line, and never delete a labelled line:
where you have nothing to put after a label, write `none` and move on. A deleted label reads
as a deleted answer.

**Before you finish**, replace every `[bracketed prompt]` with your own words, then delete
the unused `[Tool name]` entry stub, its copy-me sentence, and the prompt sentences under
each header. A leftover bracketed prompt reads as unfilled.

**Student:** Iyanuoluwa Hephzibah Olanipekun


## Featured Tools

I chose these tools because together they represent the full contribution workflow I developed during the term: finding issues, validating reproduction, evaluating plans, and reviewing pull requests. They also show the most substantial evolution across the semester, with multiple revisions driven by real grading feedback, evaluation disagreements, and issues encountered during my own contribution work.

### Issue Scout

**What it is, and the judgment hole I wrote:** Issue Scout evolved from issue-select. The original tool helped identify candidate GitHub issues. Issue Scout expanded that idea into a contribution-scouting workflow that searches GitHub, filters candidate issues, and grades them against repository activity, contribution availability, maintainer responsiveness, newcomer scope, actionable requirements, and AI-contribution policies. The judgment hole is deciding whether an issue is worth investing planning and implementation effort in.

**How it evolved, dated:** September 2026: I built issue-select to identify beginner-friendly issues with manageable scope. While searching for a contribution, I repeatedly found issues that looked promising but were stale, inactive, already claimed, or poorly specified. October-November 2026: I expanded issue-select into Issue Scout by adding maintainer-activity checks, repository-health checks, AI-contribution policy checks, and contribution-availability checks. The friction was spending substantial time investigating issues that ultimately could not be worked on.

**Evidence:** A real Issue Scout run processed approximately:

```text
400 raw issues
↓
397 unique issues
↓
354 unassigned issues
↓
342 recently active issues
↓
graded candidate set
```

The final rubric evaluated seven checks: Maintainer Alive, Repository In Use, Newcomer Scope, Unclaimed, AI Contribution Policy, Actionable Requirements, and Contribution Availability.

---

### Plan-Check

**What it is, and the judgment hole I wrote:** Plan-Check evaluates implementation plans and determines whether a proposed change is grounded in reproduced behavior, supported by evidence, scoped correctly, and executable by another contributor. The judgment hole is deciding whether a plan is ready to implement.

**How it evolved, dated:** October 2026: early versions of the rubric required very strong diagnostic certainty and often rejected plans that made reasonable technical observations. Evaluation disagreements showed that the rubric was penalizing plans for discussing likely causes. I revised the diagnosis-related checks and repeatedly validated the revisions with evaluation canaries. The friction was finding the balance between evidence requirements and practical software planning.

**Evidence:** During evaluation tuning, disagreement analysis revealed that a diagnosis-related check was overly restrictive. After revising that check and validating it with canaries, the final evaluation achieved complete agreement with the evaluation set.

---

### PR-Precheck

**What it is, and the judgment hole I wrote:** PR-Precheck evaluates whether a pull request is ready to submit by grading the implementation diff, supporting evidence, repository standards, disclosure requirements, and alignment with the accepted plan. I wrote the rubric, procedure, evidence guide, and verdict rules. The judgment hole is determining whether a pull request should be submitted or held.

**How it evolved, dated:** November 2026: the first version required visible test output for validation evidence and incorrectly rejected a package that the gold labels accepted. After analyzing pkg-19, I revised the "Evidence supports the change" check to accept explicitly reported validation evidence when it reasonably supported the claimed outcome. Later revisions focused on repository standards, disclosure requirements, and reviewer-facing communication. The friction came from repeatedly finding cases where valid work failed because the evidence requirements were too rigid.

**Evidence:** Evaluation history:

```text
18/19 (one package errored due to Windows encoding issues)
5/5 canary rerun
20/20 final evaluation
```

Final result:

```text
agreement: 20/20 scored items
(bar: 18/20 PASS)
```

The same tool reviewed my issue #53 pull request and eventually produced:

```json
{
  "verdict": "accept"
}
```

after I corrected missing disclosure details, testing evidence, reviewer notes, and repository-template requirements.

---

### Repro-Check

**What it is, and the judgment hole I wrote:** Repro-Check evaluates issue reports and generates structured reproduction workflows. It connects issue descriptions, expected behavior, observed behavior, validation steps, and evidence requirements. The judgment hole is deciding whether an issue is reproducible and whether the expected outcome can be validated.

**How it evolved, dated:** November 2026: the first version primarily generated reproduction instructions. As I used it in later units, I expanded it into a playbook that connected reproduction evidence directly to planning and implementation validation. The friction was ensuring that issue reports could be converted into workflows another contributor could consistently execute.

**Evidence:** Reproduction workflows generated through the tool were used to create before-and-after evidence for multiple assignments. The resulting reproduction plans were reused during issue investigation, implementation planning, testing, and pull-request validation.

## Inventory

- Voice Guide: Communication rules and writing standards carried through issue discussions, plans, and pull requests.
- Evidence Guide: Maps evidence types to rubric checks so grading decisions remain grounded in observable facts.
- Scope Files: Repository-specific constraints that limit tool execution to the intended environment.
- Search Strategy: Query design and filtering process used by Issue Scout's GitHub discovery workflow.
- Procedure Guides: Step-by-step execution instructions for tool consistency and repeatability.
- Rubric Collections: The structured evaluation criteria used across issue scouting, planning, reproduction, and pull-request grading.

## The Arc

**Beat 1**  
Date: September 2026  
Friction: I spent significant time manually reviewing GitHub issues only to discover they were stale, already claimed, inactive, or unsuitable for a first-time contributor.  
Change: I built issue-select and later expanded it into Issue Scout with repository-health, maintainer-activity, and contribution-availability checks.  
Result: The process became repeatable and reduced hundreds of candidate issues to a small set of realistic contribution opportunities.

**Beat 2**  
Date: October 2026  
Friction: Evaluation runs exposed disagreements about how much diagnosis and technical interpretation a plan could contain before implementation evidence existed.  
Change: I revised Plan-Check's diagnosis-related checks and validated the revisions using evaluation canaries.  
Result: Agreement improved and the final evaluation achieved complete agreement with the grading set.

**Beat 3**  
Date: November 2026  
Friction: PR-Precheck incorrectly rejected a valid package because the rubric required visible test output instead of allowing explicitly reported validation evidence.  
Change: I revised the "Evidence supports the change" check and tested the revision against pkg-19 and multiple category canaries.  
Result: The tool achieved 20/20 scored items on the evaluation suite.

**Beat 4**  
Date: November 2026  
Friction: While preparing my issue #53 pull request, I focused on implementation details and initially overlooked repository-template requirements, reviewer communication, disclosure requirements, and testing documentation.  
Change: I repeatedly ran PR-Precheck against my branch and revised the pull request description, testing checklist, disclosure statements, and reviewer notes.  
Result: The final review returned an accept verdict, all five CI checks passed, and the pull request was successfully opened.

## Limitations and What's Next

The toolkit covers issue discovery, reproduction, planning, implementation review, and pull-request readiness, but it still relies heavily on static evidence and manual context gathering. Most tools evaluate artifacts that already exist rather than collecting repository context automatically. If I continued development, I would integrate Issue Scout directly with Repro-Check and Plan-Check so that issue discovery, reproduction evidence, and planning evidence flow automatically between tools instead of being recreated manually.

**Tool limits.**

issue-scout: Cannot predict future maintainer responsiveness or guarantee that an available issue will remain unclaimed.

plan-check: Depends on the evidence included in the plan and may miss important context that only exists in issue discussions.

pr-precheck: Evaluates documented standards and evidence but cannot reliably predict reviewer preferences or future repository-policy changes.

repro-check: Requires enough issue detail to build reproduction steps and struggles when reports lack observable behavior or validation criteria.