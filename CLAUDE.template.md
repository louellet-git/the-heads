# CLAUDE.md — orientation for agents

If your session title starts with `<PREFIX>-`, you are a head of an area. Read
`chiefs/ORIENTATION.md` after this file. It says who you are and how the heads send
messages to each other.

Read this file first. Then read `README.md` (commands), `docs/TEAMS.md` (the agents) and
`docs/QUALITY-STANDARDS.md` (the standards and the gates). The known traps are in
`docs/traps/`.

## Purpose

<Two or three sentences: what the project does, who uses it, what it does not do.>

## Where the status is

- Work now and next: the board, `PLANNING/board/` (rules in its `README.md`).
- Work without a ticket: `<PLANNING/tickets.md>`.
- No other file contains status. Do not add status text to this file or to `README.md`.
- Do not write a test count or other number that each change makes old. Give the command
  that prints it.

## Which source is correct when two sources disagree

1. **The code is correct.** A number in a document that disagrees with a new run of the
   code is old.
2. **<Your source of truth, for example a config file>** is correct before the text that
   describes it.
3. <Add a rule for each pair of sources that can disagree.>

## Work rules

- **Language.** Write each new document, and each document that you change, in ASD-STE100
  Simplified Technical English, to about 85% (default of the owner; a project can change it): a
  sentence can break a rule where the STE form is less clear. A document that already meets
  this needs no rework. Frozen documents keep their original text.
- **Write-ups of actions.** Each action with real consequences (for example a trade) has one
  write-up of at most 2 pages: the logic and the steps taken, then the result. One file for each
  action; a write-up is a record and is never deleted.
- **Ticket first.** Before you start, set a board ticket to `in-progress` with your login
  and branch, and push that change.
- **One branch for one ticket.** Start it from `origin/main`. Merge through a pull
  request only.
- **Parallel agents use git worktrees** (`git worktree add ../wt-<name> -b <branch>
  origin/main`). Do not change the branch of a checkout that other agents use.
- **Subagents do not commit.** The orchestrator examines the work and makes the commit.
- **Smoke test.** A ticket is complete only after the real command runs and the next
  step can use the output.
- **No bloat.** Add one small part, show that it gives value, then add the next part.
- **Main language.** <language> for the code that calculates or gets data. A different
  language is permitted where it fits the work better.
- **Data.** <Where the shared data comes from, and who writes it. Delete this rule if the
  project has no shared data.>
- **No secret and no personal contact detail** in a file, a commit, a ticket or a message.
  This is necessary when the repo is public.
- **Cost of the checks.** The owner pays for the check runs. Follow
  `chiefs/ORIENTATION.md`, section 6.
- **Token ledger.** Add a row for each run to the `ledger.md` file of your own folder
  (`chiefs/ORIENTATION.md`, section 8).
- **Frozen documents.** <List the documents that nobody changes. Write a new version.>

## Commands

```bash
<command>   # what it does
```
