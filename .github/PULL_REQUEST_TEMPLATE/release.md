<!--
  Release PR: development → main (promotes staging to production).
  Open with this template via:  ?template=release.md&expand=1
  Example: https://github.com/Oxbow-Education/<repo>/compare/main...development?template=release.md&expand=1

  This is NOT where code review happens — every change here was already reviewed
  when its PR merged into `development`. This PR is a manifest + go/no-go gate + rollback plan.

  ⚠️ MERGE METHOD: "Create a merge commit" — NOT squash, NOT rebase.
  Both `development` and `main` are long-lived branches; squashing or rebasing makes
  their histories diverge so the next release PR shows already-shipped commits as new
  and conflicts on every touched file.
-->

> **Repo-specific release & migration steps:** [docs/deployment.md](../blob/HEAD/docs/deployment.md) · [CLAUDE.md](../blob/HEAD/CLAUDE.md)

## Release summary

<!-- One line: the theme of this batch and why it's going out now. -->

## What's shipping

<!--
  Generate, don't hand-write:
    git log --first-parent origin/main..origin/development --pretty='- %s'
-->

-

## Risk / blast radius

- [ ] DB / schema migration required? Note ordering requirements (e.g., run migration against production direct DB URL before/alongside worker or app deploy per `docs/deployment.md`) — describe:
- [ ] Auth / session / cookie behavior touched? — describe:
- [ ] Infra / env / feature-flag change? — describe:
- [ ] External write-back, sync flow, or production-write guard touched? — describe:

## Env / config changes (apply in Coolify / platform)

<!-- New/changed env vars, build vars, secrets, or feature flags. Note whether each must be set BEFORE or AFTER the deploy. "(none)" if nothing. -->

- (none)

## Verification

- [ ] `development` CI is green (lint, typecheck, unit/contract/e2e tests, build)
- [ ] Staging deployed from `development` and smoke-tested per [`docs/deployment.md`](../blob/HEAD/docs/deployment.md)
- [ ] Every bundled PR was already reviewed and merged into `development`
- [ ] No unmerged hotfix drift: any commit on `main` since the last release is also present in `development`

Post-deploy prod smoke checks & unpausing held schedules/monitors:

- [ ] Run post-deploy production smoke checks with the named production identity (per `docs/deployment.md`)
- [ ] Unpause any held schedules or monitors (e.g., new Prefect schedules, Uptime Kuma monitors) once smoke checks pass
- [ ]

## Rollback plan

<!-- Pick the path that applies and note any forward-only migration or external write-back caveats per docs/deployment.md. -->

- Revert the merge commit on `main` (`git revert -m 1 <merge-sha>`) and redeploy (or redeploy the previous production image in Coolify).
- Forward-only migrations / data implications: <!-- none / note any irreversible migration -->
- External write-back / drain pause required before rollback?: <!-- none / pause drain or scheduled write flow first if the issue is on an external write path -->

## Linked work

- Asana:
- Specs / PR docs:

---

### Merge checklist (release captain)

- [ ] Merge method = **Create a merge commit** (not squash / not rebase)
- [ ] Apply pending production database migrations in the required order per `docs/deployment.md`
- [ ] After merge: confirm production deploy succeeded
- [ ] After merge: run the production smoke checks and unpause any held schedules/monitors above
- [ ] If any hotfix landed directly on `main`, back-merge `main → development`
