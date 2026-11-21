# Quality standards

These standards bind all agents and persons. `CLAUDE.md` has the rules of the repo; this
file does not change them. The teams are in `docs/TEAMS.md`. The Head of Quality and Risk
owns this file.

The aim is lean work of good quality. A check is here only if it finds real errors. A
small style point is a note. It does not block.

## 1. Evidence

1. A claim has a command with its output, a file and line, or a named source with an
   address and a date.
2. "Tested" means that the real command ran and its output was read.
3. A number in a document can be made again: write the command, the inputs and the date
   of the data.
4. A reviewer runs the commands again. A reviewer does not accept pasted output.
5. The code is more correct than a document.
6. Say what you did not check.

## 2. Independence

The quality assurance (QA) agents never review work from their own context.

1. The orchestrator starts a QA agent in a fresh context. It gives the work (branch,
   files, commands), not the conclusion of the author.
2. A QA agent runs the commands itself.
3. A QA agent does not edit the work. It reports. The author fixes.
4. An author never reviews its own output.

## 3. Findings and verdicts

| Level | Meaning | Blocks |
|---|---|---|
| CRIT | A wrong result that a person can use; a secret in a file; an action with real effect that nobody approved; an input set from the target; a fabricated source | Merge and publication |
| MAJ | A defect that changes a result or hides a risk; new logic with no test; a claim with no evidence; a binding rule broken | Merge and publication |
| MIN | A defect with no effect on a result (a weak test, an unclear sentence, a style point) | Nothing. List it with an owner. |

**Proportion.** Give the level from the realistic effect, not from the worst possible effect. In an
internal process or document, a risk that is only possible is a MIN, on the condition that no value,
data or action can change. Do not slow the work for it. A defect that is present keeps the level of the
table. Apply the levels strictly to a result that a person can use for a decision or an action. A hard
limit (section 8) keeps the level that the table gives it.

Verdicts: **PASS** (no open CRIT or MAJ), **PASS-WITH-NOTES** (the same, with MIN items
listed), **REVISE** (a MAJ is open), **REJECT** (a CRIT is open). "Pass" means PASS or
PASS-WITH-NOTES. A reviewer passes work that is correct and usable.

Review cycles: at most two for one piece of work. After the second cycle the
orchestrator decides, and writes the decision in the pull request.

## 4. Definition of done

All kinds: the ticket is `in-progress` before the work; one branch from `origin/main`;
a row in the ledger of your own folder; no secret and no private file in the commit.

| Kind | Done when |
|---|---|
| Code change | New logic has tests with fixed answers. The test suites pass. The real command ran. Reference results are the same, or the change is the aim of the ticket. Documents that name commands are right; no document names a test count. |
| Data source | Terms read and noted. Honest client name. Fixture tests pass. One real run with a date. The source is listed. The traps are in `docs/traps/`. |
| Model or design change | The reason does not use the target. Fixed-answer tests pass. Reference results are the same, or the change is the aim. The records of the model and its assumptions are current. |
| Investigation | One findings file: question, method, evidence, defects, what stays open. Each number was calculated again by a QA agent. |
| Report for a decision | The review steps of the project were done in order. A person approved it. |
| Recommendation for an action with real consequences (for example a release, a purchase, a change to a live system, a message to customers, or a trade) | Less than 3 pages. It rests on a result that passed the review steps of the project. The person decides the action. |
| Test or experiment on data that a person uses for a decision (for example an A/B test, a benchmark, a model evaluation, a backtest) | A hypothesis file committed before the first run (the hypothesis, the held-out data, the success criterion, the number of variants tried before it). One add-only log file for each run, written before any result shows; the count of the logs is the variant count (a deleted log stays counted from the git history). Where time matters, a test that changes later data and shows that no earlier result moves (no look-ahead). Held-out data that was seen before is marked "not clean". |
| Action with real consequences (for example a release, a purchase, a change to a live system, a message to customers, or a trade) | A write-up of at most 2 pages, one file for each action: the logic, the action, the steps taken, the risks; the result after it. |
| Document | The text follows the language standard. Each command and path exists. Each number has a source. |

## 5. Gates

The orchestrator does not merge before the listed QA agents pass the work. List the gates
of the project here. The rows are examples.

| Kind of work | Author | QA agents that must pass | What they check |
|---|---|---|---|
| Code change | `<builder>` | `<code-reviewer>` | Correct, tested, repo rules |
| Report with numbers | `<analyst>` | `<auditor>` | Numbers calculated again |
| Document or record | the author | `<document-reviewer>` | Purpose, evidence, language |
| Recommendation for an action | the head of the area | `<validator>`, `<auditor>`, `<risk officer>` | The result supports the action and its size; each number calculated again; the risks |

A small change (a typing error, a count, a ticket, a ledger row) has no gate: the
orchestrator examines it. A test agent and a risk agent are not in the gates. The
orchestrator adds one of them when the work needs it. A change of a gate needs the person.

## 6. No fit of a result to the target

The target measures and ranks. No input is set from the target. Each correction has a
reason that does not use the target. A value that the target implies is a measurement and
not an input. A test set does not select the rule that it scores. A test with model data
is not a result with real data.

## 7. Numbers and language

- A number has a unit, a date, and a way to get it again. A test count has its command.
- A document does not state a status that the board owns (`CLAUDE.md`, "Where the status
  is"). A first pass is labelled "no review".
- The language standard is in `CLAUDE.md` ("Work rules"). Frozen documents keep their text.

## 8. Hard limits

No secret in a file, a commit, a ticket, a message or a chat. No private contact detail in
a public repo. A subagent does not commit. A client name is honest; no program imitates a
browser. <Add the hard limits of the project, for example "no code that sends orders".>
