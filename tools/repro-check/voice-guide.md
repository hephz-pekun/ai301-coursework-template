# Voice guide: how I talk upstream

## Who I am in threads

I am a student contributor learning open source workflows. I want my
comments to be specific, evidence-based, and respectful of maintainers'
time. I claim work carefully, reproduce behavior before drawing
conclusions, and avoid overstating what I know.

## Rules I write by

### Rule: Describe plans, not promises

When claiming an issue, I explain what I plan to investigate rather
than promising a fix.

- Wrong: "I'll have this fixed by tomorrow."
- Right: "My next step is to reproduce the behavior locally and document the results."

### Rule: State evidence before conclusions

I explain what I observed before explaining what I believe is happening.

- Wrong: "The bug is definitely caused by the phone regex."
- Right: "The reproduction shows that parenthesized phone numbers are not detected; I have not yet confirmed the root cause."

### Rule: Be specific about the issue

I refer to the actual behavior from the issue rather than speaking
generically.

- Wrong: "I'm looking into this bug."
- Right: "I'm investigating why `(555) 123-4567` is not being redacted by the PII scrubber."

### Rule: Distinguish observation from speculation

I separate observed facts from possible explanations.

- Wrong: "The parser is broken because whitespace handling is wrong."
- Right: "The parser failed to detect sections in my test case. A possible cause is whitespace handling."

### Rule: Respect maintainer time

I provide concise updates supported by evidence.

- Wrong: "Still working on it, no updates."
- Right: "I reproduced the issue and captured the failing output; I'm now comparing it with the expected behavior."

## Things I never post

- Promises of a fix or completion date.
- Claims that I reproduced something without evidence.
- Accusatory language toward maintainers or contributors.
- Statements presented as facts when they are only guesses.
- AI-generated explanations that I cannot personally explain.
