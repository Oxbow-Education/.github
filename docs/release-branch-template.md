# Release & Epic PR Templates for 4-Tier Branching

## Goal

Update the organization-wide pull request templates and `README.md` in `Oxbow-Education/.github` to support the 4-tier branching model (`feat/* | fix/*` -> `epic/*` (or `gh stack`) -> `development` -> `release/YYYY-MM-DD -> main`), live epic status dashboards (`?template=epic.md&expand=1`), CalVer release tagging (`vYYYY.MM.DD`), and `main -> development` back-merges.

## Done

- `.github/PULL_REQUEST_TEMPLATE/epic.md` provides the 6-section live status dashboard (`Summary`, `Tickets`, `Open stack`, `Merge order`, `Not yet started`, `Working on this branch`) for `<epic> -> development` draft PRs.
- `.github/PULL_REQUEST_TEMPLATE/release.md` covers `release/YYYY-MM-DD -> main` (and full `development` promotions via a release branch) merged strictly with **Create a merge commit** (`gh pr merge --merge`), never Squash or Rebase.
- `.github/PULL_REQUEST_TEMPLATE/release.md` includes `git log --no-merges origin/main..HEAD --pretty='- %s (%h)'` alongside `--first-parent` for generating the commit manifest.
- `.github/PULL_REQUEST_TEMPLATE/release.md` pre-merge verification checklist covers release chunk type (`Release train from development` vs `Selective chunk cut from main`), staging verification on `development`, production database migrations applied before merge, production env vars/secrets verified in Coolify / 1Password, and the rollback target (`vYYYY.MM.DD` tag / commit SHA on `main`).
- `.github/PULL_REQUEST_TEMPLATE/release.md` includes a **Post-merge checklist** covering the automated `vYYYY.MM.DD` (or `vYYYY.MM.DD.N`) tag and GitHub Release on `main`, production deploy health and `## After deploy` signals, and back-merging `main -> development` (`gh pr merge --merge`).
- `.github/PULL_REQUEST_TEMPLATE.md` and `README.md` reference the 4-tier branch targets (`development`, `epic/*` / `gh stack`, and `release/YYYY-MM-DD -> main`) and link to both `epic.md` and `release.md`.
