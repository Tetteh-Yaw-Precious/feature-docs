# feature-docs

> **In plain terms:** Before a feature gets built, somebody has to write down what it is. This is a
> skill that gets an AI assistant to write that properly, in three documents at three zoom levels:
> why the thing must exist, what the real nouns in it are, and what actually appears on screen.
> Think of a building again. One document is the agreement about what the building is for, one is
> the list of rooms and how they connect, and one is the floor plan with the measurements on it.
> Most teams write a vague version of the first one and skip straight to construction.

The rest of this page explains the three documents, the one rule that makes them trustworthy, and
how to install it. You don't need to already know the tools to follow along.

## What am I looking at?

This is a **skill for AI coding agents** like Claude Code, Cursor, Codex, and Gemini CLI. A skill
is a set of written instructions the agent reads and follows. You install it once, and then asking
for "the PRD", "the spec", or "write this up for my designer" gets you a real document instead of a
confident-sounding sketch.

## The three documents

| You ask for | It answers | Who reads it |
|---|---|---|
| **The PRD** | What must be true, and why | Everyone. This is the reference. |
| **The object model** | What things exist and how they relate | Whoever writes the spec, and engineering |
| **The specification** | What appears on screen and how it behaves | Design first, then engineering |

Ask for all three and it writes them in that order, because the PRD fixes the vocabulary, the
object model fixes the nouns, and the spec draws them. Ask for one and it writes that one, reading
the others first if they exist so the words match.

## The rule that makes them trustworthy

Every claim in every document is marked as one of three things:

- **Settled.** Decided, not open for rediscussion, with a note of where it was decided.
- **Proposed.** Consistent with what the product already believes, but nobody actually decided it.
  This is the author's reading, and it is always marked as such so nobody downstream mistakes a
  reading for a decision.
- **Open.** Needs an answer from a **named person** before anyone builds it. Not "TBD". A name.

That third one is the point of the whole skill:

> A plausible placeholder in a document is worse than a visible hole, because the hole gets fixed
> and the placeholder gets built.

So the agent is forbidden from inventing an answer to a policy question. If the source of record
doesn't settle it, it goes in as Open with somebody's name against it. Fifteen instances of "TBD"
is how a document stops being read.

## The parts people don't think to ask for

**Where does this feature live, on every surface?** Not just the main screen. A table maps each
capability to the places it appears: the customer's app, the staff console, the admin back office,
the emails, the printed paper, the thing somebody does on the phone. The table isn't bureaucracy,
it catches contradictions that prose hides. A capability that appears in two owning columns is a
defect in the requirements, and it is much cheaper to find there than in code. It also exposes the
surface nobody planned: almost any feature involving user-generated anything needs a
back-of-house review screen, and teams that map only the customer-facing ones cannot ship.

**What is version one actually for?** It makes you use the right word. A *closed pilot* is few
users on the full feature. *Concierge* means the work is done by hand on purpose. A *thin slice* is
the whole feature built narrowly, end to end. Most first versions are two of those three, and
calling it the wrong one leads to the wrong scope.

Then it asks the question that gets skipped: **if the pilot is meant to learn something, can it
receive its own answer?** If you're testing whether people will ask for a thing, the asking has to
have somewhere to land. A pilot that can't hear the answer teaches nothing.

And it insists on an **exit condition with an owner**, because manual, hand-run processes quietly
become permanent once they work well enough. Name the trigger that ends the pilot or the pilot
becomes the product.

**Every state, not the happy path.** A screen specification has to cover full, sparse, one item,
empty, loading, and broken, and it names which one to design first. Usually the empty one, because
that's what day one looks like and it's the one that gets drawn last and badly.

## Requirements

- An AI coding agent that supports the Agent Skills standard: Claude Code, Cursor (2.4+), Codex,
  Gemini CLI, or GitHub Copilot CLI. They all read the same `SKILL.md` format, so one copy works in
  any of them.

That's it. This skill writes documents, so it needs no tools beyond the agent itself.

## Install

| Agent | Where skills live |
|-------|-------------------|
| Claude Code | `~/.claude/skills/` (your home folder, used by every project) |
| Codex | `~/.agents/skills/` |
| Gemini CLI | `~/.agents/skills/` |
| GitHub Copilot CLI | `~/.agents/skills/` |
| Cursor (2.4+) | `.cursor/skills/` **inside the project** you want to use it in |

```bash
# Claude Code
git clone https://github.com/Tetteh-Yaw-Precious/feature-docs.git \
  ~/.claude/skills/feature-docs

# Codex, Gemini CLI, or Copilot CLI
git clone https://github.com/Tetteh-Yaw-Precious/feature-docs.git \
  ~/.agents/skills/feature-docs
```

Then ask for the PRD, or the object model, or the spec. It also triggers on the way people actually
talk: "write this up for my designer", "document it so engineering can start", "what ships in v1".

## Before it writes, it asks you two things

**Where is the source of record?** The vision document, the brief, the founder's memo, the set of
principles. Everything the documents claim should be traceable to it or flagged as new, rather than
reconstructed from memory.

**Who decides what?** Usually two or three people: someone who owns product, someone who owns
design, sometimes someone who owns legal or clinical risk. It asks once, at the start, so that every
Open question can carry a real name.

## Companion skills

| Skill | How it relates |
|---|---|
| [`feature-boilerplate`](https://github.com/Tetteh-Yaw-Precious/feature-boilerplate) | The faster, lighter version: a guided conversation ending in one spec file and a tracked backlog. Use that when you want momentum, this when the feature needs a document that will be read by people who weren't in the room. |
| [`feature-cycle`](https://github.com/Tetteh-Yaw-Precious/feature-cycle) | The build loop. It calls this skill when the feature needs a specification before building, or a document after. |
| [`lifecycle-feature`](https://github.com/Tetteh-Yaw-Precious/lifecycle-feature) | If the object model turns out to have a thing two parties both act on, with statuses and moves, that skill carries the recipe for building it. |

## License

MIT.
