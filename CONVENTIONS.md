# Conventions

The rules behind the files of this starter, and the reason for each one.
They come from the projects we deliver at Nualt.

## What must stay true

- The files loaded in every session only tell the agent how to behave
  and where to look.
- The index holds one line per document, with no summary and no rule.
- A rule is written down only once it has proved itself.
- A person approves what goes into a document.

## 1. The index is its own file at the root

`INDEX.md` sits at the root and exists nowhere else. We ruled out the
README, which is written for the client and can be long: on one project
it ran to 155 lines, which the agent would have loaded to read six. We
ruled out `docs/` because an index is something you look for at the
root. Loading it in every session is a trade-off. It costs a little
context, and in return the agent finds the right document without
exploring the repository. The trade-off only holds at one line per
document.

## 2. CLAUDE.md only imports, AGENTS.md holds the instructions

Claude Code reads `CLAUDE.md` and supports imports. Codex reads
`AGENTS.md` and documents no import. Keeping the instructions in
`AGENTS.md` and two import lines in `CLAUDE.md` gives one set of
instructions for both tools. Because Codex cannot import the index,
`AGENTS.md` carries a line that points to it.

## 3. AGENTS.md only corrects the agent's behaviour

Two criteria decide whether a mistake goes into `AGENTS.md`: whether it
recurs, and where it comes from. A mistake that comes from the agent's
habits goes in. A mistake tied to the project's domain goes into a guide
or a reference document. What falls in between is judged case by case.

## 4. docs/ARCHITECTURE.md is mandatory

Every project has it, even a brochure site. A structural decision is
recorded there as a decision, with its reason, separately from the
discussion that led to it. A decision stays open to revision: when
tests overturn it, the behaviour is fixed first and the document is
updated once the fix is confirmed.

## 5. The design system follows the code

Styles are defined in code first. `docs/DESIGN-SYSTEM.md` is written
from them when the art direction is set, then maintained. An adjustment
is made in code, because its result is judged by eye, and the document
is updated after the adjustment is approved, never before. The document
exists to stop variations creeping in as the interface grows.

## 6. BACKLOG.md is at the root and is written for people

`BACKLOG.md` tracks day by day what has been done and what remains.
Tasks appear during the project, after a test, a difficulty or a client
request. It is a project management file and is not written for the
agent. Current and upcoming tasks come first, completed tasks last.

## 7. Guides stay flat, in two kinds

A guide describes something that is done, in steps, and is reread when
doing it. Runbooks describe an operation on the production system.
Checklists list verifications to replay before a deployment or a merge.
Guides stay in `docs/guides/` with no index of their own and no
subfolders until a project has about ten of them. A guide says how, and
leaves the why to `docs/ARCHITECTURE.md`.

## 8. Every document says what it covers

Each document opens with two or three lines stating what it covers and
what it leaves to its neighbours.

## Adopting the files in a repository that already has documentation

1. Move the list of documents out of the README or `docs/` into
   `INDEX.md`, and leave a one-line pointer behind.
2. Move the agent instructions into `AGENTS.md` and reduce `CLAUDE.md`
   to its two import lines.
3. Move domain rules out of the agent file into a guide or into
   `docs/ARCHITECTURE.md`.

## Known pitfalls

- An index line that grows into a summary. The index then costs more
  context than it saves.
- Domain rules added to `AGENTS.md`. The file then grows with the
  project and the agent's behaviour instructions get lost in it.
- A document that keeps the trace of everything that was tried. It
  works in a small repository and drowns the agent in a large one.
