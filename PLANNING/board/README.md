# Board

The board is the one list of work that a person does now or does next.
One ticket is one file: `PLANNING/board/<id>.md`.
Work without a ticket is in the backlog: `<PLANNING/tickets.md>`.

## Ticket format

```
---
id: T-YYYYMMDD-example
title: Short title that starts with a verb
area: <area>
status: backlog
owner: <github-login>
requested_by: <github-login>
head: <folder name of a head>
order: 3
branch:
created: YYYY-MM-DD
acceptance: One sentence that a person can check.
---
Free text.
```

| Field | Rule |
|---|---|
| `id` | `T-YYYYMMDD-<slug>`. The file name is the id. |
| `title` | Short. It starts with a verb. |
| `area` | <List the areas of the project.>, and `ask` (a question or a permission request for the person; `chiefs/ORIENTATION.md`, section 5). |
| `status` | `backlog`, `in-progress`, `review`, or `done`. |
| `owner` | A GitHub login. It has a meaning from `in-progress`. |
| `requested_by` | The login of the person who asked for the work. A head offers only the tickets of its own person. No field means `<owner of the repo>`. |
| `head` | The head that is responsible for the ticket (its folder name in `chiefs/ORIENTATION.md`). `owner` means that only a person can do the work. Each ticket has this field. |
| `order` | The position in the queue of its head. The lowest number is first. A person can change it. |
| `branch` | The git branch. Necessary when the status is `in-progress` or `review`. |
| `created` | The date of the ticket. |
| `acceptance` | One sentence that a person can check. |

| Status | Meaning |
|---|---|
| `backlog` | Planned. No person has the ticket. |
| `in-progress` | A person works on the branch of the ticket. |
| `review` | A pull request is open. |
| `done` | The pull request is merged. In the subsequent change, move the ticket file to `PLANNING/board/done/` with `git mv`. Set `status: done` and add a line `merged: <pull request>`. Never delete a ticket. |

## Rules

1. Before you start work, set the ticket to `in-progress` with your login and branch.
   Push this change first. Then the other person can see that the ticket is yours.
2. Use one branch for one ticket. Start the branch from `origin/main`.
3. Merge to the default branch only through a pull request.
4. A new ticket has a `head`, an `order` and a `requested_by`. If the work is in the
   areas of two heads, make two tickets.
5. The queues are the files at the top of `PLANNING/board/`. The folder `done/` keeps the
   closed tickets as a record. A head does not read it for work and does not take a
   ticket from it.
6. No tool enforces these rules. Each person and each agent obeys them.
