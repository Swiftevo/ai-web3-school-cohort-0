# Task: GitHub Learning Repo Setup

## Current Status

- Local learning workspace: `C:\Users\User\Documents\AI x Web3 school`
- `git`: not found in current terminal
- `gh`: not found in current terminal
- Codex GitHub connector account: `Swiftevo`
- Remote GitHub repo URL: https://github.com/Swiftevo/ai-web3-school-cohort-0
- Connector write status: blocked by GitHub `403 Resource not accessible by integration` for repository contents writes

## Recommended Remote Repo

- Name: `ai-web3-school-cohort-0`
- Visibility: public
- Description: `Personal learning journal and proof-of-work for AI x Web3 School.`

## Steps

1. Codex App GitHub connector is linked to `Swiftevo`, but current repo contents write permission is blocked.
2. Install local Git if needed: https://git-scm.com/downloads
3. Install GitHub CLI: https://cli.github.com/
4. Run:

```bash
gh auth login
gh auth status
```

5. Clone the existing repo if you want local command-line sync:

```bash
gh repo clone Swiftevo/ai-web3-school-cohort-0
```

6. Copy or move the initialized files into the cloned repo if you choose a different local path.
7. Commit only after reviewing the files for secrets.

```bash
git status --short
git add .
git commit -m "Initialize AI Web3 School learning repo"
git push
```
