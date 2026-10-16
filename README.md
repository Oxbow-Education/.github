# Oxbow-Education/.github

Organization-wide default community health files and pull request / issue templates for `Oxbow-Education` repositories. GitHub automatically applies these files to any repository in the organization that does not define its own local override.

## Included files

| File | Purpose |
| --- | --- |
| [`.github/PULL_REQUEST_TEMPLATE.md`](.github/PULL_REQUEST_TEMPLATE.md) | Default PR template for feature, fix, and chore branches targeting `development`, `epic/<slug>`, or stacked PR bases via `gh stack` (includes the `## After deploy` block read by `verify-fix`). |
| [`.github/PULL_REQUEST_TEMPLATE/epic.md`](.github/PULL_REQUEST_TEMPLATE/epic.md) | Epic foundation PR template (`epic/<slug> → development`), structured as a live status dashboard (`Summary`, `Tickets`, `Open stack`, `Merge order`, `Not yet started`, `Working on this branch`). Open via `?template=epic.md&expand=1`. |
| [`.github/PULL_REQUEST_TEMPLATE/release.md`](.github/PULL_REQUEST_TEMPLATE/release.md) | Release PR template for promoting `release/YYYY-MM-DD → main` (full `development` train or selective chunk cut from `main`, merged via merge commit `--merge`, tagged `vYYYY.MM.DD`, and back-merged `main → development`). Open via `?template=release.md&expand=1` on the compare / new-PR URL. |
| [`.github/ISSUE_TEMPLATE/config.yml`](.github/ISSUE_TEMPLATE/config.yml) | Disables blank GitHub issues and routes bug and ops tracking to the Asana Bug Board and Asana Ops Board. |
| [`SECURITY.md`](SECURITY.md) | Organization security policy directing vulnerability reports to GitHub Private Vulnerability Reporting or WhereWeGo engineering rather than public issues. |

## Repo-specific context

Each repository keeps its own stack commands, architecture, deployment runbooks, and verification checklists in its root `CLAUDE.md` and `docs/` directory (such as `docs/README.md` and `docs/deployment.md`). The PR templates link to those files via relative paths (`../blob/HEAD/CLAUDE.md`, `../blob/HEAD/docs/deployment.md`) so they resolve inside whichever repository the pull request is opened on.
