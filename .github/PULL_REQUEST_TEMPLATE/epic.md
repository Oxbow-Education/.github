<!--
  Epic foundation PR: epic/<slug> → development (or <epic> → development).
  Open with this template via:  ?template=epic.md&expand=1
  Example: https://github.com/Oxbow-Education/<repo>/compare/development...epic/<slug>?template=epic.md&expand=1

  Keep this PR in Draft while ticket PRs land into the epic branch.
  Treat this description as a live status dashboard (current state of the epic),
  never a chronological diary. Update it as ticket PRs open, stack, or merge.
-->

> **Repo-specific context:** [CLAUDE.md](../blob/HEAD/CLAUDE.md) · [docs/README.md](../blob/HEAD/docs/README.md) · [docs/deployment.md](../blob/HEAD/docs/deployment.md)

## Summary

<!-- 2–3 sentences on what the epic delivers, a link to `docs/<epic>/plan.md` as the source of truth, and 1 line on what the foundation branch currently carries. -->

- **Plan / spec (source of truth):** [`docs/<epic>/plan.md`](../blob/HEAD/docs/)
- **Foundation branch currently carries:** <!-- 1 line describing shared schema, types, or merged tickets currently on this branch -->

## Tickets

<!-- Status legend: `✅ merged (#N)` · `🔄 **#N**` (open PR) · `⬜ not started — gated, below` -->

| Ticket | What | Status |
| --- | --- | --- |
| `<ticket-1>` | <!-- short description --> | ✅ merged (#N) |
| `<ticket-2>` | <!-- short description --> | 🔄 **#N** |
| `<ticket-3>` | <!-- short description --> | ⬜ not started — gated, below |

## Open stack

<!--
  ASCII tree of live ticket branches and their bases.
  Default to flat sibling branches off `epic/<slug>`; stack (`gh stack`) only when one ticket has a real code dependency on another unmerged ticket.
-->

```text
development
└── epic/<slug> (this PR)
    ├── feat/<ticket-a> (#N)
    └── feat/<ticket-b> (#M)
        └── feat/<ticket-c-stacked-on-b> (#P)
```

## Merge order

<!-- Numbered list naming blocking conditions, rebases needed after upstream merges, and ordered-resource claims (e.g. next free migration index). -->

1. **#N (`feat/<ticket-a>`):** <!-- e.g. Ready to merge into `epic/<slug>`; claims migration `0042` -->
2. **#M (`feat/<ticket-b>`):** <!-- e.g. Blocked on review; rebase `#P` via `gh stack sync` once merged; next free migration index: `0043` -->

## Not yet started

<!-- List each unstarted ticket (`⬜`), what blocks it, and what breaks or stays incomplete if the epic ships without it. -->

- **`<ticket-3>`:**
  - **Blocked by:** <!-- e.g. `#M` landing shared table / API contract -->
  - **If epic ships without it:** <!-- what breaks or degrades in production -->

## Working on this branch

<!-- Local-dev gotchas for anyone checking out `epic/<slug>` or branching off it: DB reset commands, new env vars (`1Password` item), seed scripts, or pending migrations. -->

- **Database / migrations:** <!-- e.g. Run migration / reset local DB Needed? -->
- **Env vars / secrets:** <!-- e.g. New vars in `.env.example` / `1Password` `<project>.env.local` -->
- **Seeds / fixtures:** <!-- e.g. Seed script or test data setup -->
