# Triage Labels

The skills speak in terms of five canonical triage roles. This file maps those roles to the actual label strings used in this repo's issue tracker.

Because this repo tracks issues as local markdown (see `issue-tracker.md`), a "label" is the value of the `Status:` line near the top of an issue file.

| Label in mattpocock/skills | Label in our tracker | Meaning                                  |
| -------------------------- | -------------------- | ---------------------------------------- |
| `needs-triage`             | `needs-triage`       | Maintainer needs to evaluate this issue  |
| `needs-info`               | `needs-info`         | Waiting on reporter for more information |
| `ready-for-agent`          | `ready-for-agent`    | Fully specified, ready for an AFK agent  |
| `ready-for-human`          | `ready-for-human`    | Requires human implementation            |
| `wontfix`                  | `wontfix`            | Will not be actioned                     |
| —                          | `done`               | Implemented; acceptance criteria met     |

When a skill mentions a role (e.g. "apply the AFK-ready triage label"), use the corresponding label string from this table.

Edit the right-hand column to match whatever vocabulary you actually use.

## `done` is local to this repo

The five canonical roles are all triage states: they say what a ticket needs next, not that it is
finished. This tracker needs a terminal state too, so `done` exists here with no counterpart on the
left-hand column. No skill will ask for it by name — set it yourself when a ticket's acceptance
criteria are all met, and record what was built in the ticket's `## Comments` section.

`done` means the work is implemented and the criteria are ticked. It does not mean shipped: on this
repo the merge to `main` publishes straight to the live site, so a `done` ticket can still be
sitting on a branch waiting for a human to look at it.
