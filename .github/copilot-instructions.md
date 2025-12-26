# Copilot Instructions (Repo-wide)

This is a **single-project repository** for neural network training techniques.

## Scope safety
- This repo IS the project; all project files may be edited for portfolio readiness.
- Never modify:
  - `.git/`
  - `history/` (git historian outputs)

## Output requirements
- Portfolio readiness: fix absolute paths, remove assignment traces, update README, improve documentation
- No feature creep: preserve original functionality and results
- Git historian outputs go under `history/`:
  - `github_steps.md`
  - `steps/step_01..step_N` (full snapshots excluding history/ itself)

## Logging discipline
- All discovered issues go to `suggestion.txt` (TYPE, FILE, LOCATOR, BEFORE_SNIPPET, PROPOSED_CHANGE, RATIONALE, STATUS)
- All applied changes go to `suggestions_done.txt` (FILE, LOCATOR, BEFORE_SNIPPET, AFTER_SNIPPET, NOTES)
- `report.md` documents all phases and verification steps

## Snapshot rules for Git Historian
- Snapshots must represent the project working tree EXCLUDING `.git/` and `history/`
- step_01 = initial commit (README + .gitignore)
- step_N = final portfolio-ready state (byte-for-byte match)
- No recursion: history/ folder must NOT appear in any snapshot

## Do not stop early
Maintain a checklist and do not finish until all acceptance criteria are satisfied.
