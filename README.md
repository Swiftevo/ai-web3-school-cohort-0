# AI x Web3 School Learning Repo

Personal learning journal and proof-of-work workspace for AI x Web3 School.

## Fixed Entrypoints

- Handbook: https://aiweb3.school/zh/handbook/
- WCB course page: https://web3career.build/zh/programs/AI-Web3-School
- WCB Learning page: https://web3career.build/zh/programs/AI-Web3-School#tab=learning
- WCB Agent API docs: https://web3career.build/llms.txt
- GitHub: https://github.com/
- GitHub CLI: https://cli.github.com/

## Privacy Reminder

This repo is intended to be public proof-of-work. Do not commit API keys, seed phrases, private keys, passwords, verification codes, private contact details, internal meeting links, or other people's personal data.

## Directory Guide

- `profile.md`: learner profile and preferences.
- `learning-plan.md`: lightweight study roadmap and weekly rhythm.
- `daily/`: daily notes, check-in drafts, and submission links.
- `tasks/`: task notes and proof-of-work records.
- `experiments/`: runnable prototypes, prompts, scripts, and demos.
- `handbook-feedback/`: feedback items for Handbook pages.
- `hackathon/`: project ideas, specs, milestones, and demos.
- `submissions/`: submitted task records and public links.
- `templates/`: reusable daily note and task note templates.

## Daily Workflow

1. Open the WCB Learning page and confirm today's class, task, meeting, and check-in entry.
2. Read the matching Handbook page.
3. Create or update `daily/YYYY-MM-DD.md`.
4. Draft the check-in post.
5. Submit manually on WCB or the official check-in platform.
6. Paste the submitted link or record back into the daily note.

## GitHub Setup Status

Codex GitHub connector can access the GitHub account `Swiftevo` and read repository metadata for `Swiftevo/ai-web3-school-cohort-0`.

Current limitation: GitHub returned `403 Resource not accessible by integration` when Codex tried to write files to the repo. This means the connector currently does not have repository contents write access.

Local terminal status: `git` and `gh` are not currently available in this terminal. After installing them, run:

```bash
gh auth login
gh auth status
gh repo clone Swiftevo/ai-web3-school-cohort-0
```

Before syncing local changes, confirm no secrets are included.

## Codex And GitHub

There are two separate connections:

- Codex App GitHub connector: allows Codex to inspect GitHub repositories, issues, and pull requests. File writes require repository contents write permission.
- Local terminal Git/GitHub CLI: allows this workspace to run `git`, `gh`, commit, push, clone, and manage the repo from the local machine.

The connector is visible for `Swiftevo`, but repo contents write access is not currently granted. Local `git` / `gh` also still needs installation if you want normal command-line repo workflows from this workspace.
