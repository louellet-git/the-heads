# The heads: a lean operating system for Claude Code projects

A head is one cloud session of Claude Code that leads one area of a project. A head is
an orchestrator agent: it plans, gives work to the agents of its team, examines the
result, and commits. This repo gives the rules. It has no agent files and no skills.
It has the rules for how a head makes them.

## What the system gives

| Part | File |
|---|---|
| Who a head is, its queue, its messages, its reviews | `chiefs/ORIENTATION.md` |
| A small memory for each head | `chiefs/MEMORY-HOWTO.md` |
| The form of an agent file and a skill file, and the flows | `docs/TEAMS.md` |
| Evidence, findings, verdicts, definition of done, gates | `docs/QUALITY-STANDARDS.md` |
| One file for each ticket, one queue for each head | `PLANNING/board/README.md` |
| One file for each trap | `docs/traps/README.md` |
| The rules of the project for each agent | `CLAUDE.template.md` |

## Set-up for a new project

1. Copy the files of this repo (not `.git`) into the root of the project.
2. Rename `CLAUDE.template.md` to `CLAUDE.md`. Fill each `<...>` placeholder.
3. In `chiefs/ORIENTATION.md`, choose `<PREFIX>` and fill the table of heads (section 1)
   and the table of owned files (section 2).
4. Make the agent files of each team in `.claude/agents/`. Follow `docs/TEAMS.md`. Make a
   skill only when a head does a procedure again and again.
5. Merge all of this to the default branch.
6. Start one cloud session for each head. The first message is:
   "You are <PREFIX>-<tag> - Head of <Area>. Set your session title to that text, then
   read CLAUDE.md and chiefs/ORIENTATION.md."
7. Send one test message from one head to another (`chiefs/ORIENTATION.md`, section 5).
   Check that the other head gets it.

## What not to build

- A hook or a guard that reads session ids. An id changes; a title does not.
- A wake clock or a schedule that starts a head.
- One shared file that all heads write. Use one file for each new entry.
- A large memory. Few files and one small dashboard are better.
- A rule that the source of this system does not have. Add a rule only after an error
  shows that you need it.

## Standing choices of the owner (defaults)

- Agent files give the Sonnet model; a head can choose a different model for one run.
- Questions for the person are yes/no tickets, asked as a clickable question with a push
  (`chiefs/ORIENTATION.md`, section 5).
- Documents use ASD-STE100 Simplified Technical English, to about 85%.
- Each action with real consequences (for example a trade) has a write-up of at most 2 pages.
- After a ticket, a head reports and takes the next ticket with no wait, until the person
  says stop.
- Agents and skills stay lean. They are not obsessive and not tight-fisted.
