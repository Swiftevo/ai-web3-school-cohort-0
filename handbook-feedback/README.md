# Handbook Feedback Workflow

Use this folder to turn learning friction into useful public feedback.

## When To Create Feedback

- A concept is unclear or missing prerequisites.
- A page has outdated information or broken links.
- A paragraph can be more precise.
- A minimum practice needs example output.
- A diagram, code sample, or bilingual wording would help.

## Feedback Format

Create one file per item:

```text
handbook-feedback/YYYY-MM-DD-short-title.md
```

Use this structure:

```markdown
# Feedback: Short Title

- Date:
- Handbook page:
- Section:
- Type: clarity / accuracy / structure / link / example / translation
- Status: draft

## Problem

Describe what was confusing or incorrect.

## Suggested Change

Suggest a concrete edit or addition.

## Source Or Reasoning

Add source links, screenshots, or your reasoning.

## Possible PR Text

Draft the text that could be submitted upstream.
```

## Weekly Loop

1. Collect feedback candidates in daily notes.
2. Promote useful ones into this folder.
3. Review wording and sources.
4. Submit through the Handbook GitHub or community channel after confirming the upstream contribution path.
5. Save the PR, issue, or discussion link back into the feedback file.

