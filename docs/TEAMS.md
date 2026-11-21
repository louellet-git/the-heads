# The teams

A team is the set of agents that one head starts. An agent is a file in
`.claude/agents/<name>.md`. A shared procedure is a skill in `.claude/skills/<name>/SKILL.md`.
All agents use the Sonnet model unless the person says otherwise. The standards are in
`docs/QUALITY-STANDARDS.md`; the rules of the repo are in `CLAUDE.md`. The rules for who
makes and changes agents and skills are in `chiefs/ORIENTATION.md`, section 3.
Keep agents and skills lean. They are not obsessive and not tight-fisted.

## The agents

List each agent here. The rows are examples. Replace them.

| Team | Agent | Job |
|---|---|---|
| `<team>` | `<builder>` (example) | Writes and changes the product code |
| QA | `<code-reviewer>` (example) | Checks the correctness of a diff and the repo rules (read only) |
| QA | `<auditor>` (example) | Traces each claim to a source and calculates each number again (read only) |

## The form of an agent file

Frontmatter fields:

| Field | Rule |
|---|---|
| `name` | The file name, with no `.md`. |
| `description` | When to use the agent and when not to. The orchestrator reads this line to choose. |
| `tools` | The smallest list that does the job. A QA agent has read and run tools only (`Read, Grep, Glob, Bash`). |
| `model` | `sonnet`. |
| `skills` | The skills that the agent uses. |

Body, in this order: **Purpose**, **Inputs**, **Output**, **Checks** (5 or fewer),
**Never**, **Stop and ask**. About 40 lines in all. One purpose for each agent.

## The form of a skill file

`.claude/skills/<name>/SKILL.md`. Frontmatter: `name` and `description` (when to use it).
Body: a short title, the rules it follows, then numbered steps. Make a skill when a team
does the same procedure again and again. Do not make one for a single use.

## QA agents

QA agents have no edit tool and no write tool. They report in the final message. The
orchestrator saves the report if needed.

## Flows

A flow is the order of agents for one kind of work. List the flows of the project here.

| Flow | Steps |
|---|---|
| Code change | `<builder>` -> `<code-reviewer>` (example) |
| Report with numbers | `<analyst>` -> `<auditor>` (example) |

A flow has at most two QA agents. The orchestrator adds a test agent or a risk agent only
when the work needs it. A project can set a longer flow for one kind of work in
`CLAUDE.md`.

## Rules of the orchestrator

The orchestrator is the main Claude Code session. A head is the orchestrator of its area.

1. Only the orchestrator commits, pushes, opens and merges pull requests.
2. Ticket first: set it `in-progress` with the login and the branch, and push. One branch
   for one ticket, from `origin/main`.
3. Parallel agents work in git worktrees. Each agent gets its own path.
4. Each brief has the ticket, the goal, the files, the commands and the acceptance. A QA
   agent gets the work and no conclusion, in a fresh context.
5. The orchestrator reads the diff and runs the real command before it commits.
6. It applies the gates of `docs/QUALITY-STANDARDS.md`. After two review cycles it
   decides.
7. It adds a row to the ledger of its own folder for each run. After the merge it moves
   the ticket file to `PLANNING/board/done/` (never deletes it).
8. A decision for a person (a rule, a closed decision, a paid source) goes to the person.

## How a person starts an agent

Name the agent: "Use the `<name>` agent to do X. Ticket: `T-...`." Claude Code also starts
an agent when the task fits its description. `/agents` lists them.
