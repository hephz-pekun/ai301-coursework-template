# Contribution: Find Leads that already exist as Contacts

Path: `beat-2-contribution/contribution-story.md`

This file is Assignment 5, and it is graded at the path above; a copy kept anywhere else in
the repository is not read. **Keep every section header below under its exact name** — the
format criteria grade exactly that. Your course repo link is the whole submission: no tool
files and no evidence uploads are part of Assignment 5.

**Contribution Number:** [1]
**Student:** Hephzibah Olanipekun
**GitHub Username:** hephz-pekun
**Issue:** https://github.com/akhsterminator/sf-exit/issues/13
**Pull Request:** (https://github.com/akhsterminator/sf-exit/pull/17#issue-6399423119)

One repository, built across units 5 to 8, telling the whole story of your real
contribution. Fill it as you work, not at the end — the sections below ask for evidence that
is far easier to write down as it happens than to reconstruct in the last weekend.

Contribution Number stays `[1]` unless you make more than one contribution this term; it
just numbers them.

---

## Toolkit

Every story section below, from Why I Chose This Issue through Pull
Request, ends with a Toolkit block: which tool did that phase's work
and how you used it, what it produced, what difficulties or
shortcomings it presented, and what you changed or would change
because of them. Together the blocks are the thread the rubric's
Toolkit points read, and they are the raw material for your unit-9
portfolio, so keep them current as you work rather than
reconstructing them later.

A Toolkit block looks like this (copy it into each story section and
fill it there):

```text
**Toolkit**

- Tool: issue-scout. I used my custom search strategy and rubric to scan and grade open-source issues that matched my Python and testing interests.
- What it produced: A ranked list of candidate issues. After earlier selections became unavailable, the scout identified sf-exit#13 as a strong alternative and graded it as an acceptable contribution opportunity.
- Difficulties: The scout consistently favored newly-created issues and often returned multiple issues from the same repository.
- What changed: I reran the scan, reviewed new candidates, and selected an issue that was still available while documenting weaknesses in the ranking strategy.
```

This section also keeps one short dated entry per week of tool work,
starting below: what you built or changed that week, what broke, and
what you changed because of it. The blocks tell the story where it
happened; these entries are the toolkit's own timeline.

All four entries are graded. Keep every heading below, and fill each
one in the week it belongs to.

**Unit 9: Built and evaluated an issue-scout workflow for selecting an open-source contribution**

I configured the issue-scout tool using a profile focused on Python, testing, and bug-fix work. After running a scan, I reviewed the five highest-ranked issues and compared the recommendations against my own goals for a first contribution. The scan identified several useful candidates, including agentswarm-data-tasks#234, but it also exposed weaknesses in the ranking strategy such as duplicate query coverage and a tendency to favor newly created issues. I recorded those findings in scan-notes.md and used the results to choose a contribution target.

**Unit 10: [one line on the tool work]**

**Unit 11: [one line on the tool work]**

[2-4 sentences: the ship-gate and your gate manifest. What it produced
on your real branch, what fought you, what changed because of it.]

**Unit 12: [one line on the tool work]**

[2-4 sentences: the PR-monitor and your playbook. What it read, what it
drafted, what you did with the draft.]

---

## Why I Chose This Issue

I used my issue-scout tool to search for beginner-friendly Python issues related to testing, data processing, and bug fixing. My initial top-ranked selections were claimed before I could begin work on them, so I reran the scout and evaluated a new set of candidates. The scout accepted sf-exit#13 and identified it as a strong match because the scope was limited to a single audit finding and accompanying test coverage in an active Python project.

I chose this issue because it involves understanding an existing codebase, extending functionality, and validating the change with automated tests. The issue focuses on a real Salesforce data-quality problem: identifying unconverted Leads that already exist as Contacts. It fits my interests in backend logic and testing while remaining small enough for a first open-source contribution.

**Claim comment:** https://github.com/akhsterminator/sf-exit/issues/13#issuecomment-6887436774


**Toolkit**

- Tool: issue-scout. I used my custom search strategy and rubric to scan and grade open-source issues that matched my Python and testing interests.
- What it produced: A ranked list of candidate issues. After earlier selections became unavailable, the scout identified sf-exit#13 as a strong alternative and graded it as an acceptable contribution opportunity.
- Difficulties: The scout consistently favored newly-created issues and often returned multiple issues from the same repository.
- What changed: I reran the scan, reviewed new candidates, and selected an issue that was still available while documenting weaknesses in the ranking strategy.
---

## Understanding the Issue

**Problem Description**

The audit tool currently reports duplicate email addresses across Contact and Lead records, but it does not generate a dedicated finding when an unconverted Lead matches an existing Contact by email address. This specific Salesforce data-quality problem can indicate duplicate representations of the same person and is not currently surfaced in the audit report.

**Expected Behavior**

The audit should generate a finding when Lead.Email matches Contact.Email, ignoring case, for Leads where IsConverted is false. The finding should appear in the audit output and identify the overlapping email addresses.

**Current Behavior**

The existing implementation aggregates duplicate email addresses through the duplicate-emails finding but does not separately identify unconverted Leads that already exist as Contacts. As a result, this common data-quality issue is not explicitly reported.

**Affected Components**

- src/sf_exit/audit.py
- tests/test_tools.py
- tests/fake_org.py

**Toolkit**

- Tool: None used
- What it produced: N/A
- Difficulties: N/A
- What changed: N/A

---

## Reproduction Process

**Environment Setup**

Windows 11, Python 3.14, and a local clone of the sf-exit repository. Dependencies were installed from pyproject.toml using:

pip install -e ".[dev]"

The test suite uses pytest and a fake Salesforce organization defined in tests/fake_org.py.

**Steps to Reproduce**

1. Add a Lead fixture whose email matches an existing Contact email using different casing.
2. Add a test expectation for a Lead-to-Contact audit finding.
3. Run:

   pytest tests/test_tools.py -q

4. Observe that the new test fails because the finding is not generated.

**Reproduction Evidence**
- **Comment showing reproduction:**
https://github.com/akhsterminator/sf-exit/issues/13#issuecomment-6887752507

- **Screenshots/logs:** Traceback (most recent call last):
```
PS C:\Users\hephz\OneDrive\Desktop\sf-exit> pytest tests/test_tools.py -qF....                                                                                                              [100%]======================================================= FAILURES ========================================================____________________________________________ test_audit_finds_real_problems _____________________________________________export_dir = WindowsPath('C:/Users/hephz/AppData/Local/Temp/pytest-of-hephz/pytest-2/exp0')tmp_path = WindowsPath('C:/Users/hephz/AppData/Local/Temp/pytest-of-hephz/pytest-2/test_audit_finds_real_problems0')    def test_audit_finds_real_problems(export_dir, tmp_path):        report = run_audit(export_dir, tmp_path / "audit")        ids = {f["id"]: f for f in report["findings"]}>       assert "lead-contact-overlap" in idsE       AssertionError: assert 'lead-contact-overlap' in {'overdue-opportunities': {'id': 'overdue-opportunities', 'severity': 'high', 'title': '15 open opportunities are past... owned by deactivated users', 'detail': 'Nobody is responsible for them. Reassign them before a migration.', ...}, ...}tests\test_tools.py:28: AssertionError================================================ short test summary info ================================================FAILED tests/test_tools.py::test_audit_finds_real_problems - AssertionError: assert 'lead-contact-overlap' in {'overdue-opportunities': {'id': 'overdue-opportunities', 'severity'...1 failed, 4 passed in 2.50sPS C:\Users\hephz\OneDrive\Desktop\sf-exit> 
```
```
AssertionError: assert 'lead-contact-overlap' in ids
```

- **My findings:** I reproduced the issue by extending the fake Salesforce organization with an unconverted Lead whose email matched an existing Contact using different letter casing. After adding a test expectation for a new Lead-to-Contact finding, the test suite failed with "AssertionError: assert 'lead-contact-overlap' in ids". This confirmed that the current audit implementation does not generate a dedicated finding when Lead.Email matches Contact.Email case-insensitively.

**Toolkit**

- Tool: None used 
- What it produced: N/A
- Difficulties: N/A
- What changed: N/A

---

## Solution Approach

**Analysis**

The existing audit logic already identifies duplicate email addresses through the duplicate-emails finding, but it does not separately identify the Salesforce-specific data quality issue described in the issue: an unconverted Lead whose email address already exists on a Contact. During code review, I found that email addresses were already being normalized to lowercase and collected for duplicate detection, making it possible to extend the existing audit workflow with a dedicated Lead-to-Contact finding.

**Proposed Solution**

I extended the audit pipeline to track Contact email addresses and unconverted Lead email addresses independently while preserving the existing duplicate-email functionality. I then added a new lead-contact-overlap finding that reports case-insensitive matches between Contacts and Leads where IsConverted is false. To verify the behavior, I extended the fake Salesforce organization with Lead test data and added test coverage for the new finding.

**Implementation Plan**

1. Extend the fake Salesforce organization with an unconverted Lead whose email matches an existing Contact.
2. Add a failing test that expects a Lead-to-Contact overlap finding.
3. Update audit.py to collect Contact and unconverted Lead email addresses separately.
4. Create a new lead-contact-overlap finding based on case-insensitive email matches.
5. Run the test suite and linting tools to verify correctness.

No deviations were required from the original implementation plan.

**Toolkit**

- Tool: None used
- What it produced: N/A
- Difficulties: N/A
- What changed: N/A

---

## Testing Strategy

I validated the change using automated tests and the project's existing fake Salesforce environment.

First, I extended the fake org with an unconverted Lead whose email matched an existing Contact using different letter casing (ADA1@x.example versus ada1@x.example). I then added a failing test that expected a new lead-contact-overlap finding.

After implementing the change, I verified:

the finding exists,
the finding count equals 1,
the matching email address appears in the finding output,
all existing audit tests continue to pass.

Commands executed:

```
pytest tests/test_tools.py -q
ruff check .
```

Results:

```
5 passed in 2.49s
All checks passed!
```

**Toolkit**

- Tool: None used
- What it produced: N/A
- Difficulties: N/A
- What changed: N/A

---

## Implementation Notes

**2026-11-14**

I selected sf-exit issue #13 after earlier issue-scout recommendations became unavailable. I reviewed the existing duplicate-emails finding and reproduced the missing behavior by extending the fake Salesforce organization with an unconverted Lead whose email matched an existing Contact using different casing. A new test expecting a lead-contact-overlap finding failed, confirming the feature was not implemented.

I updated audit.py to track Contact and unconverted Lead email addresses separately and added a new lead-contact-overlap finding based on case-insensitive matches. I then extended the test suite with assertions validating the finding count and matched email address. The final implementation passed both pytest and ruff check.

**Toolkit**

- Tool: None used
- What it produced: N/A
- Difficulties: N/A
- What changed: N/A

---

## Pull Request

**PR Link:** (https://github.com/akhsterminator/sf-exit/pull/17#issue-6399423119)

**PR Description:** 
## What does this change?

Adds a new audit finding that identifies unconverted Leads whose email addresses already exist on Contacts.

Changes include:

- Added tracking for Contact email addresses and unconverted Lead email addresses.
- Added a new `lead-contact-overlap` audit finding for case-insensitive Contact/Lead email matches.
- Extended the fake Salesforce org with Lead fixture data.
- Added test coverage validating the overlap finding, count, and matching email address.

## How was it tested?

- [x] `pytest` passes
- [x] `ruff check .` passes
- [x] Added or updated tests (extend `tests/fake_org.py` if needed)
- [ ] Updated `CHANGELOG.md` / docs if user-facing

Commands run:

```bash
pytest tests/test_tools.py -q
ruff check .
```

**Maintainer Feedback:**

- 2026-11-14: none yet. 
- 2026-11-14: not applicable.

**Status:** Awaiting review

**Toolkit**

- Tool: None used
- What it produced: N/A
- Difficulties: N/A
- What changed: N/A

---

## Learnings and Reflections

**Technical Skills Gained**

I learned how to extend an existing audit pipeline without duplicating logic, how to add meaningful test fixtures for a simulated environment, and how to use pytest to drive implementation through reproduction and validation. I also gained experience working with Salesforce-style data structures and case-insensitive matching logic.

**Challenges Overcome**

The most significant challenge was identifying where the new behavior belonged in the existing audit workflow. The code already tracked duplicate email addresses, so I needed to understand how email data moved through aggregation and finding generation before implementing the new feature. Creating a failing test first helped confirm my understanding and provided a reliable way to validate the implementation.

**What I'd Do Differently Next Time**

I would inspect the test fixtures and existing finding patterns earlier in the process. Understanding the test environment sooner would have reduced the time spent exploring the codebase and made reproduction faster.
---

## Resources Used

[What actually helped, not a reading list. List things this story
already shows you using: the doc you followed to set the environment
up, the thread that explained the bug, the person who answered you.
One real entry beats ten plausible ones.]

- https://github.com/akhsterminator/sf-exit/issues/13
- https://github.com/akhsterminator/sf-exit/issues/13#issuecomment-6887752507
- src/sf_exit/audit.py
- tests/fake_org.py
- tests/test_tools.py
