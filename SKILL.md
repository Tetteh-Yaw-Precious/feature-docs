---
name: feature-docs
description: Write the three product documents for a single feature: the PRD (what must be true and why), the object model (the nouns, in OOUX ORCA terms), and the version one specification (screens, states, flows, copy). Use this whenever the task is to draft, structure, or extend any of those three, or when the user says "write the PRD", "do the object model", "draft the spec", "scope this to MVP or MVF", "what ships in v1", or "turn this into a document for the team". Trigger it even when only one of the three is asked for, and even when the user never says PRD, spec, or OOUX by name, for example "write this up for my designer", "document it so engineering can start", or "we need something to hand off". It enforces the Settled / Proposed / Open discipline, a named owner on every open question, surface allocation for multi-surface features, and states over happy paths.
---

# Feature documents

Three documents, one feature, three altitudes. This skill writes any of them.

| Mode | Document | Answers | Audience |
|---|---|---|---|
| **PRD** | Product requirements | What must be true, and why | Everyone. The reference document |
| **Object model** | The nouns | What things exist and how they relate | Spec author, engineering |
| **Spec** | Version one specification | What appears on screen and how it behaves | Design, then engineering |

If the user asks for all three, write them in that order: the PRD fixes the vocabulary, the object model fixes the nouns, the spec draws them.

If the user asks for one, write that one. Read the others if they already exist, so the vocabulary matches.

---

## Before writing anything

**Find the source of record.** Most products have one document that governs: a vision document, a brief, a set of principles, a founder's memo. Ask for it if it is not in context, or search past conversations. Everything these documents say should be traceable to it or marked as new. Do not reconstruct it from memory.

**Establish who decides what.** Every open question gets a named owner, and you need to know the names. Usually there are two or three: someone who owns product or policy, someone who owns design, sometimes someone who owns legal or clinical risk. Ask once, at the start, rather than writing "TBD" fifteen times.

**Never invent an answer to a policy question.** If the source of record does not settle it, mark it Open with an owner. A plausible placeholder in a document is worse than a visible hole, because the hole gets fixed and the placeholder gets built.

**If the product has settled rules, gather them before you write.** They live in this conversation, in the repository, or in the person you are talking to. Ask once, capture them in one block at the top of the work, and every document inherits them. A product with strong constraints (things it refuses to build, architectural walls, a house voice) needs those stated up front, or each document rediscovers them badly.

---

## The status key

Every document opens with it and every claim in the body carries one where it is not obvious.

- **Settled**: decided, and not open for rediscussion. Cite where.
- **Proposed**: consistent with the source of record but not written in it. This is the author's reading. Mark it, always, so nobody downstream mistakes a reading for a decision.
- **Open**: needs an answer from a named person before build.

Marking Proposed honestly is the single most important habit in these documents. When the work reaches the person who decides, they need to see instantly which parts are theirs to rule on.

---

## Rules that apply to every mode

**Silence in a specification is a decision made by an engineer at the wrong moment.** Every document needs a section that says what is deliberately *not* being built, written as requirements rather than as a note.

**One recommendation per open question, with reasoning.** Not a menu of options. Where two directions are genuinely live, name both, then recommend one and say why. A document that only poses questions makes the reader do the work twice.

**Empty cells stay honestly empty.** In any table, a blank means the thing does not exist there, and that absence is itself a requirement. Never pad with N/A.

**Define before justifying.** A reader who was not in the room cannot start at "why". Say what the thing is first.

**Plain language beats precise jargon in flows.** "She says she is coming" survives translation into every other document. "The guest confirms attendance" does not.

---

## Mode 1: the PRD

The PRD says what must be true. No pixels, no screens, no layout.

```
1. Where this sits          The feature's place in the product. Which area it lives
                            in, and (stated plainly) which areas it never touches.
                            Flag any vocabulary that is doing more than one job.
2. What it is               Define the object in one bold sentence, then unpack it.
                            Follow with "what it is not", because readers import
                            assumptions from products they already know.
                            End with a vocabulary block: the four to six words this
                            feature fixes. Everything downstream inherits them.
3. Why this exists          Two or three reasons, then one sentence that could be
                            said aloud.
4. Who it is for            The distinct users and their different rights.
                            Conflating them is the usual failure.
5. What we are building     The requirements, grouped. Each carries a status mark.
6. What we are deliberately These are requirements, not notes. Say what is refused
   not building             and why, so nobody rediscovers the argument later.
7. Constraints inherited    Product-level rules this feature must not break.
   from the architecture    Not this feature's decisions. Cite the source.
8. Surfaces and allocation  Only when the feature spans more than one surface.
9. Open questions           A table: question, owner. Nothing ownerless.
10. From vision to MVF      See below.
11. The flows               The inventory, in plain language, numbered, each tagged
                            v1 or later.
12. What this does not cover
```

### Surfaces and allocation

The moment a feature touches more than one surface, the PRD stays surface agnostic and allocates in one table: capabilities down the left, surfaces across the top.

Write one PRD and three specs, never three PRDs. A feature has one set of rules; splitting the rules by surface is how two teams end up building different products.

This table is not bureaucracy. It catches contradictions prose hides. A capability appearing in two owning columns is a defect in the requirements, and it is far cheaper to find here than in code. It also reveals the surface nobody planned, most features that involve user-generated anything need a back-of-house review or admin surface, and teams that map only the customer-facing screens cannot ship.

Remember the surfaces that are not screens: email and messaging, physical spaces and paper, and anything done by a person on the phone. Each has requirements.

State explicitly which rules survive the split. A number that is operational on an internal console must not appear on a surface where the product has refused numbers.

### From vision to MVF

MVF is minimum viable feature, the feature-level MVP. Two things must both be true: a real user gets real value from it on its own terms, **and** it teaches something. If it only teaches, it is an experiment, and an experiment run on people needs to be named as one.

Write this section as:

- **The shape of version one.** Name it precisely, and use the right word. *Closed pilot* means few users on the full feature. *Concierge* (or Wizard of Oz) means the operations are manual on purpose. *Thin slice* means the whole feature built narrowly, end to end. Most first versions are two of the three.
- **What the pilot is meant to learn.** One primary question, stated as a question.
- **The consequence for scope.** If the primary question is whether people ask for something, the asking must have somewhere to land. A pilot that cannot receive its own answer teaches nothing. This is the step teams skip.
- **In the first slice / not in the first slice.** Two lists.
- **The exit condition.** Concierge processes quietly become permanent because they work well enough. Name the trigger that ends the pilot, with an owner. Without it, the pilot becomes the product.
- **How the signal is gathered.** Say what is measurable, what is countable back of house, and what is only ever human. If the product refuses instrumentation, say that plainly rather than implying analytics that will not exist.

---

## Mode 2: the object model

Objects outlive features. Screens will be redesigned, the feature will grow a second version, whole areas will be rebuilt. The nouns will still be the same things. That is why this is its own document and not a section inside the PRD.

**Forage for the nouns before you judge them.** They come from the source of record, the transcripts, the existing screens and the way people say things out loud, not from your sense of what the data model ought to be. Then merge the synonyms and write down which word won. Two words for one thing is the most common defect in this document; one word doing two jobs is the most expensive.

The test, applied out loud to each candidate: **an object earns its place if it has its own life, its own name, and things that are true only of it.** If it exists only as a property of something else, it is an attribute.

Three questions make that checkable rather than a matter of taste. Does it have its own detail view. Would someone search for it by name. Does it have its own lifecycle. Three yes answers is an object; three no answers is an attribute wearing a noun. A split is the interesting case, and it belongs in section 4 with the reasoning rather than being resolved quietly.

```
1. Why this document exists separately
2. Reconciliation                 What earlier decisions retired, what survived,
                                  what is new. A flow that references a retired
                                  object is not caught until build.
3. The objects                    Each: one-line definition, why it earns objecthood,
                                  rules.
4. What fails the test, and why   As valuable as section 3. Say what was considered
                                  and rejected, so it is not re-proposed, and say
                                  which way it failed: demoted to an attribute,
                                  combined with another object, or cut outright.
5. Relationships                  A table, with cardinality and dependency, asked in
                                  both directions. Deliberate absences are rows.
6. The attributes                 Per object, a table. Kind, source and scope are
                                  columns, never prose. See below.
7. The CTAs                       A matrix: objects down, roles across. Verb plus
                                  object. This is the feature inventory.
8. Open questions                 With owners.
```

**Reconciliation is not optional when the product has changed direction.** If a newer document superseded an older architecture, some objects no longer exist. Mark what is dead before building on it.

**Watch for relationships doing too much work.** A relationship that starts carrying its own data (a contact detail, a consent, a role, a timestamp that matters) is becoming an object. Say so in the document, so the promotion is a decision rather than a drift.

**Watch for the state machine.** Many objects that look like several things are one object in several states. If an announcement becomes a record after an event, that is usually one object changing tense, not two objects. Getting this right removes a whole class of synchronisation bugs.

### The relationships table

| From | To | Cardinality | Dependency | Note |
|---|---|---|---|---|

**Ask every pair in both directions.** "An invoice has many payments" and "a payment belongs to one invoice" are two separate questions, and the second one is where the surprises live. A pair nobody asked about in the reverse direction is a pair whose cardinality is wrong.

**Dependency is its own column because it is a different question from cardinality.** Can either side exist without the other. That answer decides what deletion does, and deletion is where unowned rows and orphaned children come from.

**Deliberate absences belong in the table.** "X never relates to X" is a real row and it protects a refusal.

### The attributes

Attributes are gear four, and they are the gear that gets written as a shopping list of field names. A list of names carries none of the three things that actually decide the build, so make them columns:

| Attribute | Kind | Source | Scope | Required | Who may edit |
|---|---|---|---|---|---|

**Kind is core content or metadata, and the distinction is not pedantry.** Core content is what a person types or uploads, and it is unique to the instance. Metadata is the shared value chosen from a fixed set, the thing somebody will sort by, filter on, or group under. Every metadata attribute is therefore a requirement for a filter control, a sort order and an index. The ones discovered after the list screen is built are the expensive ones.

**Source is entered, derived, or external.** Entered means a person supplies it. Derived means the system computes it. External means it arrives from somewhere this team does not control, which makes it a value that can be absent, stale, or wrong in production.

**Scope is mandatory for anything derived, and it is the box that catches the bad number.** Say what it is derived from and across what range. "Total, this page" and "total, every record" are different numbers wearing the same label, and the label is what ships.

**Force-rank them.** Name the three to five that appear on the object's card or row, and rank the rest for the detail view. An unranked attribute list is not a decision, it is a layout argument deferred to whoever draws the screen.

### The CTAs

**CTAs are gear three of OOUX and they generate the feature list.** Verb plus object, never a naked verb: `Come to this gathering`, not `Join`. A naked verb leaves "what" unanswered and fails completely when read aloud by a screen reader. Also name the surfaces where there is deliberately *no* call to action, because someone will propose adding one.

**Write them as a matrix, objects down the left, roles across the top.** A per-object list reads fine and hides the thing worth knowing, which is who may do it. An empty cell means that role may not, and that is a requirement, not a gap.

**A role in the column header is not enough.** Most calls to action are conditional on the relationship between the actor and the particular instance: edit *my own*, approve *someone else's*, see the ones *at my branch*. Write the condition in the cell. A cell that says only `edit` is the shape a permission bug arrives in, because the code that checks the role is rarely the code that checks the instance.

**Go past create, edit and delete.** Two families get left out of every first draft. Lifecycle moves (archive, reactivate, void, close, reopen) and the contra-CTAs: undo, cancel, withdraw, dispute, report, block. The contra ones are what a user needs at the exact moment something has gone wrong, which is the worst possible moment to discover they were never built.

---

## Mode 3: the specification

The PRD says what must be true. The spec says what appears on screen and how it behaves. It is finished when someone who has never spoken to you could build it correctly. If they have to guess, the spec has a hole, and the hole gets filled by whoever is closest to the keyboard.

Two things deserve saying at the top of the document:

**States, not screens.** The full, populated version of a screen is easy. The version with one item on it is the actual problem, and it is the state that arrives on day one. Every screen lists its states, and the sparse ones get drawn first.

**Copy is part of the specification.** Not a placeholder for a writer later. Where words belong to someone else's voice (a founder, a brand owner, a clinician) mark them Open rather than filling them with something plausible that will ship.

```
1. How to read this        Including any standing rules that apply to every screen.
2. The flows               2.1 the plain list, in the user's own language, numbered
                           to match the PRD. 2.2 the same flows walked step by step
                           through lettered screens.
                           End with the spine: the object's lifecycle, and a
                           state-to-screen matrix. Empty cells in that matrix are
                           the holes a person falls into.
3. Screen inventory        Letter, name, surface, flows served.
4..n By surface            Most protected or most constrained surface first.
     Per screen            Purpose · Contents · The action · What is not here ·
                           a state table · Heard.
n+1 Accessibility          See below.
n+2 Open questions         With owners.
n+3 What is not covered
```

### Per screen

**Purpose** in one line, from the user's point of view.

**Contents**, and then **what is not here**, which is often the more useful list.

**The action**, verb plus object, and what it becomes once used.

**A state table.** Not just the happy path. Include: full, sparse, single-item, empty, loading, error, and every state of the underlying object. Mark which state to design first, usually the single-item one, because it is both the hardest and the one that ships on day one.

**Heard.** What this screen is for someone who cannot see it.

### Accessibility

Write it as a section, not a checklist at the end.

The principle: **equivalent in meaning, never equivalent in mechanics.** A screen reader wants labels, counts, and positions. If the product has deliberately refused those, announcing them by voice restores the meaning by breaking the rule. Find the non-numeric equivalent instead.

Cover: image descriptions written by a person and collected in the flow that creates the image, never machine-generated where the images are of real people; orientation for meaning that is carried visually by density, arrangement, or colour; stable order heard as well as seen; absence that reads warm rather than broken; and the ordinary requirements, contrast, type size, reach, reduced motion, touch targets, nothing carried by colour alone.

Set those ordinary requirements against the real audience. People who are tired, older, one-handed, in poor light, or on old devices are not edge cases in most products.

**Distinguish two things that both get called accessibility.** Screen accessibility is the above. **Physical access** (step-free entry, a usable toilet, a seat by the door, dietary and allergy needs) is a different problem that belongs in the flows and the forms. Anything health-adjacent a user declares is data with a purpose, a retention limit, and an owner. Ask only when it will be acted on, and delete it when its purpose ends.

---

## Producing the files

Write Markdown first. Convert to Word with pandoc when the user wants something to send:

```bash
pandoc doc.md -o doc.docx --from markdown+hard_line_breaks --to docx
```

`hard_line_breaks` keeps the header block from collapsing into one paragraph. Strip any `---` rule that directly follows a table, or it renders as a stray character. Render to PDF and view a page or two before handing it over.

Then say, briefly, what the document exposed that prose was hiding: the hole the matrix revealed, the flow that gained a step, the question that now has an owner. That is more useful than a summary of what was written.
