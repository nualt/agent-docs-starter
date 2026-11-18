# agent-docs-starter

A starting point for documenting a project that AI agents work in. The
repository is the template: its files are the ones to keep in your own
project, written as Markdown and versioned with the code.

An agent reads the code in seconds. What it does not find there is why a
decision was made, what was tried and dropped, and which mistakes were
already fixed. Give it too little and it repeats them. Give it the whole
history and it drowns. These are the files we use at
[Nualt](https://nualt.fr) to sit between the two: a short part loaded in
every session, and the rest read on demand.

It works with Claude Code and Codex, and it is plain Markdown: readable
by a person, useful with any agent, and useful with none.

## What is in here

```
README.md                   this page, to replace with your own
AGENTS.md                   how the agent should behave
CLAUDE.md                   imports AGENTS.md and INDEX.md
INDEX.md                    one line per document
BACKLOG.md                  what is done and what remains
docs/ARCHITECTURE.md        how the system is built and why
docs/DESIGN-SYSTEM.md       visual rules
docs/guides/deployment.md   a runbook
docs/guides/smoke-tests.md  a checklist
CONVENTIONS.md              the rules behind these files and why each one exists
LICENSE                     MIT
```

## Getting started

1. Create your repository from this one with **Use this template**, or
   copy the files into an existing repository.
2. Replace this README with your own, from the outline below.
3. Fill `docs/ARCHITECTURE.md` with the decisions already made, each
   with its reason. Delete `docs/DESIGN-SYSTEM.md` if the project has no
   interface, and rename or delete the two guides to match your
   operations.
4. Update `INDEX.md` so that it lists every document, one line each.
5. Leave `AGENTS.md` almost empty. Add an instruction only when the
   agent repeats a mistake that comes from its own habits.
6. Read `CONVENTIONS.md`, then delete it or keep it, as you prefer.

To check the result, open a new session and ask the agent where the
deployment procedure is. It should answer from the index, without
exploring the repository.

## How the files work together

- **Every session.** `CLAUDE.md` imports `AGENTS.md` and `INDEX.md`.
  Codex loads `AGENTS.md` on its own, and `AGENTS.md` points to the
  index. These files stay short because they sit in the context for the
  whole session.
- **On demand.** The index sends the agent to `docs/ARCHITECTURE.md`,
  `docs/DESIGN-SYSTEM.md` or a guide when the task calls for it.
- **For the client.** `README.md` is the only file written for the
  person who receives the project. The others are delivered with the
  code and remain readable by a person.
- **For project tracking.** `BACKLOG.md` follows day by day what has
  been done and what remains. It is written for the people running the
  project.

## The outline of your own README

```markdown
# Project name

One paragraph that says what the project is.

## What this project contains

## Getting started

## Deployment

## Documentation

The list of documents is in [INDEX.md](INDEX.md).
```

For a client, Getting started covers day-to-day use first, then how to
change the code. For a tool, it covers installation, then configuration.

## License

MIT, see [LICENSE](LICENSE).
