<!--
  Release PR: release/YYYY-MM-DD → main (promotes a release branch to production; supports both a full `development` promotion via `release/YYYY-MM-DD` and a selective chunk cut from `main`).
  Open with this template via:  ?template=release.md&expand=1
  Example: https://github.com/Oxbow-Education/<repo>/compare/main...release/YYYY-MM-DD?template=release.md&expand=1

  This is NOT where code review happens — every change here was already reviewed
  when its PR merged into `development` (or `epic/*`). This PR is a manifest + go/no-go gate + rollback plan.

  ⚠️ MERGE METHOD: "Create a merge commit" (`gh pr merge --merge`) — NEVER Squash, NEVER Rebase.
  Both `development` and `main` are long-lived branches; squashing or rebasing makes
  their histories diverge so the next release or back-merge shows already-shipped commits as new
  and conflicts on every touched file.
-->

> **Repo-specific release & migration steps:** [docs/deployment.md](../blob/HEAD/docs/deployment.md) · [CLAUDE.md](../blob/HEAD/CLAUDE.md)

## Release summary

<!-- One line: the theme of this release chunk and why it's going out now. -->

- **Release chunk type:** <!-- Release train from development (cut from `development`) | Selective chunk cut from main (cut from `main` with cherry-picked / merged PRs) -->
- **Previous production release tag / SHA (`main`):** <!-- e.g. v2026.10.15 (`abc1234`) -->

## What's shipping

<!--
  Generate, don't hand-write:
    git log --no-merges origin/main..HEAD --pretty='- %s (%h)'
  Or by first-parent commits on the release branch:
    git log --first-parent origin/main..HEAD --pretty='- %s (%h)'
-->

-

## Risk / blast radius

- [ ] DB / schema migration required? Note ordering requirements (e.g., run migration against production direct DB URL before/alongside worker or app deploy per `docs/deployment.md`) — describe:
- [ ] Auth / session / cookie behavior touched? — describe:
- [ ] Infra / env / feature-flag change? — describe:
- [ ] External write-back, sync flow, or production-write guard touched? — describe:

## Env / config changes (apply in Coolify / 1Password)

<!-- New/changed env vars, build vars, secrets, or feature flags. Note whether each must be set BEFORE or AFTER the deploy. "(none)" if nothing. -->

- (none)

## Pre-merge verification checklist

- [ ] Release chunk type noted (`Release train from development` vs `Selective chunk cut from main`)
- [ ] Release branch and `development` CI are green (lint, typecheck, unit/contract/e2e tests, build)
- [ ] Staging (`development`) verified and smoke-tested per [`docs/deployment.md`](../blob/HEAD/docs/deployment.md)
- [ ] Every bundled PR was already reviewed and merged into `development`
- [ ] Database migrations applied to production before merge (if applicable, in the required order per `docs/deployment.md`)
- [ ] Production env vars / secrets verified in Coolify / 1Password
- [ ] Rollback target noted (previous `vYYYY.MM.DD` tag / commit SHA on `main`)
- [ ] Merge method confirmed as **Create a merge commit** (`gh pr merge --merge`) — never Squash or Rebase

## Rollback plan

<!-- Pick the path that applies and note any forward-only migration or external write-back caveats per docs/deployment.md. -->

- **Rollback target:** <!-- previous `vYYYY.MM.DD` tag / commit SHA on `main` -->
- Revert the merge commit on `main` (`git revert -m 1 <merge-sha>`) and redeploy (or redeploy the previous `vYYYY.MM.DD` production image in Coolify).
- Forward-only migrations / data implications: <!-- none / note any irreversible migration -->
- External write-back / drain pause required before rollback?: <!-- none / pause drain or scheduled write flow first if the issue is on an external write path -->

## Linked work

- Asana:
- Specs / PR docs:

---

## Post-merge checklist

- [ ] Automated `vYYYY.MM.DD` (or `vYYYY.MM.DD.N`) tag and GitHub Release created on `main`
- [ ] Production deploy healthy and `## After deploy` signals checked (plus any held schedules/monitors unpaused per `docs/deployment.md`)
- [ ] Back-merged `main -> development` (`gh pr merge --merge`) so `development` records the release merge commit and any release-branch / hotfix changes
