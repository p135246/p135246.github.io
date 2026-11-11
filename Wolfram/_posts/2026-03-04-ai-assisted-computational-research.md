---
title:      "Computational research and AI"
categories: [Software, Wolfram]
mathjax:    false
utterances: true
---

*This post is a living document. Last updated on 2026-10-03.*

# Computational research and AI

At the [Wolfram Institute][WI], I explore how ideas from mathematical physics carry over to the framework of [Wolfram models][WP].

Before committing to a concrete project, I brainstorm ideas, gather resources, implement computable notions in [Wolfram Language][WL], and create experimental notebooks. If a direction looks promising and gets accepted by colleagues, I develop it further, eventually contributing to Wolfram Institute projects, [paclets][paclet-repo], or independent writing.

I find the **exploratory phase**, **repo maintenance and organization**, and the **polishing phase** especially suitable for **AI assistance**.

## History of my use of AI

I have used freely available AI since 2024 in a basic way—for asking questions, reformatting, and limited-scope debugging. I worked in a corporate environment at that time, and I was anxious about causing a compliance breach by sharing unwanted context and about having end-to-end responsibility for code that would go into production. My AI proficiency before fall 2025 consisted mainly of configuring, understanding, and using the functionality of [CodeCompanion][codecompanion] for [Neovim][neovim]. I had not done any agentic workflows or vibe coding.

A turning point came with the release of [Claude Opus 4.5][opus]. I began experimenting with agentic workflows and got used to offloading tasks to Claude using only guidance and specifications, without touching the code directly. The results were surprisingly good. My first "wow" moment was [vibe-coding][vibe-coding] a [Swift][swift] app to manage and time-track my weekly tasks—generated entirely from a screenshot of my wife's Excel table. I have never programmed in Swift and have never looked at the generated code, yet the app works perfectly. It feels like we are approaching a world where anyone can define the app they need and let the AI build it, like selecting a song on a jukebox.

Rapid prototyping—getting from A to B without deep dives—also seems essentially solved. When improvements are needed, the simplest approach is to direct the AI to reuse fragments of earlier code or templates. When I have time or need specific architecture, I still refine things myself, but AI gives me the option to strategically postpone that work.

Given this shift, I think it is time to think about researchers' **best practices for computational research in the AI era**. I am not aware of any general standards or guidelines at the moment, and I don't have time to dive too deep, so I decided to stay within the [Claude][claude] ecosystem and began writing a [plugin that captures my workflow][comp-research].

## Computational research plugin

The [plugin][comp-research] ([GitHub][comp-research]) is installed from the [Wolfram Institute marketplace][marketplace]. Core principles:

- **Computational engine.** A link to the Wolfram kernel for computational validation.
- **Knowledge base.** A Markdown wiki readable by both humans and LLMs.
- **Resource management.** Resources stored as Markdown with recovery instructions.
- **Repo organization.** Notebooks, code, paclets, etc.
- **Tour.** Guide the user through the project, tracking progress and revision.
- **Formal verification.** Validation of statements using Lean.
- **Prompt provenance.** Tracking of prompts that can regenerate LLM artifacts.

See the LLM-updated [version history](#version-history) below for a changelog after major releases.

## AI in mathematics research

There will be some central database of formalized and verifiable mathematics, with hypotheses and an LLM as its I/O API:

- **Future mathematician.** They can enter a new result in any form, even blackboard photos, and the AI will take care of placing it correctly in the database, formalizing it, and queuing it for verification. The mathematician will also be encouraged to attach an author's note, without LLM edits, capturing their personal impression. They will not have to stitch together a math paper. They can focus on coming up with novel contributions, presenting and advertising them to a human audience, and creating other personal traces such as blog posts or videos.
- **Math consumer.** They can search through the database with the help of LLMs and generate a study-ready paper tailored to their needs.

Perhaps [Lean][lean] and [Mathlib][mathlib], which I still have to get more familiar with, can already provide the backbone for such a database. However, they are still too technical, and it is not easy to verify that a formalized statement corresponds to a human-understandable one.

Note that in our project [UniversalityDB](https://github.com/WolframInstitute/UniversalityDB), we want to demonstrate that LLMs, when equipped with a knowledge base, a computational engine, and human guidelines, can help with auto-formalization in Lean and lower the threshold for using it.

## Human role in AI era

AI will surely make certain hard skills obsolete. Paradigm shifts are exciting, and letting things go and starting anew deepens life experience. But several human roles remain essential:

- **Curiosity** — the drive to explore a direction and push it as far as possible through questions and tasks.
- **Ideas** — identifying an AI-unsolvable problem that matters to your group of humans and challenging yourself to solve it.
- **Coordination** — defining the workflow for agents and deciding when humans intervene.
- **Communication** — spreading enthusiasm among humans about your problem and convincing them it is worth their time and resources.

## Technical ideas for AI workflow

Along the way I have crystallized some ideas for future workflow improvements:

- **A clear definition of an agent.** What exactly is an agent? Can an agent create other agents? Can such agents be reused across contexts?
- **An orchestration graph.** A workflow graph including agents, tools, and humans, ideally compilable into a minimal version where most tasks are performed by tools—a more capable successor to [LLMGraph][llmgraph].
- **Reproducible AI workflow.** The LLM keeps a single prompt that recovers the current state of the work. Versioning every LLM prompt is one option, but not necessary.
- **A distinction between human-revised and LLM-generated data.** A clear marker of which content has been reviewed by a human and which was produced by the LLM.

## Version history

*[LLM generated]*

### Version 5.6 (2026-10-03)

Version 5.6.0 gives a document a memory of how it was revised. A correction the human made by hand in one round used to be forgotten as soon as the round ended, and could return in a later one wherever a note made the machine rewrite that passage. Now each document keeps a record beside it of what the human wrote, where, and what came back, and from it a short list of rules that the machine reads before every new version. A mistake needs to be corrected once. The record also changes what is kept: the notebook, a generated thing, stays out of version control, and its text source, which is what the human and the machine actually discuss, takes its place.

### Version 5.5 (2026-09-30)

Version 5.5.0 gives every project the same handwriting. Until now each repository carried its own copy of the code conventions, and the copies had drifted apart: one allowed what another forbade, and a personal style kept in the author's own configuration was silently overruled by the project it was meant to govern. The conventions now live in one place and are the same for code, for the notebooks that explain it and for the papers that state it: what a definition looks like on the page, how a figure is coloured so that it reads in light and in dark, how a notebook walks a reader from pictures to a result. A project no longer says how to write; it says only what is particular to it.

### Version 5.4 (2026-09-27)

Version 5.4.0 moves the review into the document. The human no longer explains in a chat what should change in a paper or a notebook. They write short notes into the text itself, or simply fix it, and the machine answers with the next version beside the old one. Every round is kept, so the exchange between reader and machine becomes a trail of drafts, the way a manuscript passes between an author and an editor. The machine may change only what the notes ask for, and nothing else.

### Version 5.3 (2026-09-26)

Version 5.3.0 turns the description of the tool into its specification. The front page now says what the plugin promises, area by area, each with the reason it exists, and every sentence there is a promise a user can hold it to. Where the promise runs ahead of the code, the gap becomes a piece of planned work, so the page is at once the philosophy, the acceptance test and the backlog. The same version lets the machine work that backlog while the human watches: each task goes to its own worker, visible and open to a word from the human, rather than to a process nobody can see.

### Version 5.1 (2026-09-26)

[Version 5.1.0][comp-research] admits that the plan of work has two readers. Until now it was written for the machine: a compact contract that a fresh session could load cheaply, which a human could read but was not meant to enjoy. Now it opens the way a good issue tracker does, with what the task is, why it matters and how we will know it is done, and the technical contract comes after. The division of labour follows the same line. The human spends hours on the backlog writing the why and the what, while the machine thinks through the how. Nothing runs until the human says the plan is ready, and nothing counts as finished until a human has checked it against instructions the machine left for that purpose. Autonomy grows by keeping the human at the two ends where judgement matters, not by removing them.

Version 5.1.1 changes how mathematical objects are written in code. A segment or a group is now an inert name holding only its defining data, and it computes nothing until it meets the structure it is read in. An object exists only where a theorem says it is well defined. The code conventions also move closer to those of a larger sister project: input that does not fit is left alone rather than rejected, and a question the code cannot decide stays open instead of being answered "no".

### Version 4.16 (2026-08-21)

[Version 4.16.0][comp-research] tests a promise instead of restating it. The system had a rule that nothing a document discards may disappear quietly, and the rule had never met a document with something to discard, because the exercise built to produce one produced nothing. Constructing the missing case took an afternoon and found three separate ways the promise could not be kept: it was announced after the document it governs had already been finished, it told the writer to mark what was left over without saying what a mark is, and it reported to a place the reporter cannot write to. None of that is visible from the design side and all of it is obvious from one instance. There is a second lesson about artifacts: the earlier exercise's documents were thrown away once their conclusions had been written down, and that is precisely what left this promise untested. A conclusion is not a substitute for the thing it was drawn from.

### Version 4.15 (2026-08-21)

[Version 4.15.0][comp-research] is the first version whose writing rules were read rather than reasoned. They had been written from a diagnosis of why machine-written documents flood the page, which makes every one of them a guess until somebody sits down with a finished document and checks whether it can be checked. Most of the guesses held. One was backwards: cutting the examples that accompany new definitions had been counted as restraint, and it is the opposite, because a definition is where the reader meets an object for the first time and cannot verify anything about it without seeing one. Restraint that removes what the reader needs is not restraint. The general lesson is cheaper than the specific one — a rule invented to prevent a failure is worth about as much as an untested hypothesis, and reading one real document under it costs less than living with it.

### Version 4.14 (2026-08-20)

[Version 4.14.0][comp-research] lets a plan price the work it divides. Whoever splits a problem into sessions already knows which of them is routine and which one decides something, and that judgement used to be thrown away — an unattended task ran on whichever model happened to be selected that day. Now the plan carries the judgement and the machine obeys it. The honesty around it matters as much: the report says which model actually did each piece, declines to claim it knows how hard the machine was thinking, and when the cheap choice fails it says so rather than quietly trying the same thing again. A first real run then priced the idea and corrected it. The cheapest model did the work correctly and then failed the bookkeeping around it, which is the expensive kind of failure: it costs a person's attention rather than pennies. So the cheap option came off the table for anything that has to keep its own books. Frugality is only frugal when what you are saving is the scarce thing, and the scarce thing here is not money.

### Version 4.13 (2026-08-18)

[Version 4.13.0][comp-research] asks a document to earn the reader's trust before it asks for their time. A written argument is either complete enough to be checked line by line or it does not belong in the paper; what was merely observed to hold moves somewhere that says so, and a small result proved properly is worth more than a broad one hedged. The assistant is named as the author, since it wrote the thing, and the paper states plainly how much of its own direction was the assistant's — whether a human specified the mathematics or only named a topic and let it look. That is a question a reader of a machine-written paper asks first, and it should not have to be guessed.

### Version 4.10 (2026-07-29)

[Version 4.10.0][comp-research] treats a research notebook as a paper rather than a worksheet: the mathematics comes first and the machinery moves out of the reader's way. A claim earns its place by a computation that answers something, not by a picture illustrating it.

### Version 4.9 (2026-07-28)

[Version 4.9.0][comp-research] turns the plugin's rules on the plugin itself — a thing is said once and read on demand, rather than repeated wherever it might be needed. The version-4 line asked what the assistant can be trusted to do alone: generate a document one way from a source it does not own, and work through a task list unattended, with a human merging the result.

### Version 3.8 (2026-05-31)

[Version 3.8.0][comp-research] treats the compute session as shared and finite rather than free. Work happens inside one live [Wolfram][wolfram-mcp] session the human is also sitting in, instead of starting a fresh one whenever that is convenient.

### Version 3.2 (2026-05-29)

[Version 3.2.0][comp-research] separates what is known from what is being done. Execution state leaves the knowledge base and becomes something version control can follow, and planning gets deliberately lighter — a long plan rots faster than it is followed.

### Version 3 (2026-04-12)

[Version 3.0.0][comp-research] widens the ambition from exploring to shipping: a project is carried from the first question through to a [paclet][paclet-repo] or a paper, rather than stopping at organized notes.

### Version 2 (2026-04-05)

[Version 2.0.0][comp-research] puts the knowledge in plain text that the human and the model read the same way, navigated by links rather than by scanning everything. What can be regenerated is rebuilt on demand instead of stored (idea by [sw1sh][sw1sh]), and what the human wrote is protected from being overwritten.

The core [MCP][mcp] servers remain [Wolfram MCP][wolfram-mcp] (or the unofficial [wolfram-mcp][wolfram-mcp-sw1sh] with [LSP][lsp] support) and [arXiv-mcp][arxiv-mcp] (plus [arxiv-latex-mcp][arxiv-latex-mcp] for reading LaTeX source).

### Version 1 (2026-03-04)

The first version of the [plugin][comp-research] was a handful of task-shaped skills: turn a prompt into a Wolfram notebook (an idea by [sw1sh][sw1sh]), scaffold a research project, gather papers from [arXiv][arxiv] and [Wolfram Community][wolfram-community] into cited notes.

After a few projects the design felt too broad and not goal-oriented enough. Exploring, collecting, and organizing were tangled together, and there was no single place where what I knew actually lived. That diagnosis is what every later version answers.

[WI]: https://wolframinstitute.org/
[WP]: https://www.wolframphysics.org/
[wolfram-page]: /Wolfram.html
[infrageometry-post]: /wolfram/2026/03/31/talks-infrageometry-srni-madrid.html
[WL]: https://www.wolfram.com/language/
[codecompanion]: https://github.com/olimorris/codecompanion.nvim
[neovim]: https://neovim.io/
[opus]: https://www.anthropic.com/news/claude-opus-4-5
[comp-research]: https://github.com/WolframInstitute/ClaudePluginComputationalResearch
[sw1sh]: https://github.com/sw1sh
[arxiv]: https://arxiv.org/
[wolfram-community]: https://community.wolfram.com/
[wolfram-mcp]: https://www.wolfram.com/artificial-intelligence/foundation-tool/
[wolfram-mcp-sw1sh]: https://github.com/sw1sh/WolframMCP
[arxiv-mcp]: https://github.com/blazickjp/arxiv-mcp-server
[arxiv-latex-mcp]: https://github.com/takashiishida/arxiv-latex-mcp
[lean]: https://lean-lang.org/
[llmgraph]: https://reference.wolfram.com/language/ref/LLMGraph.html
[vibe-coding]: https://en.wikipedia.org/wiki/Vibe_coding
[mcp]: https://modelcontextprotocol.io/
[lsp]: https://microsoft.github.io/language-server-protocol/
[paclet-repo]: https://resources.wolframcloud.com/PacletRepository/
[swift]: https://www.swift.org/
[mathlib]: https://leanprover-community.github.io/
[claude]: https://claude.ai/
[marketplace]: https://github.com/WolframInstitute/ClaudePluginMarketplace
[wolfram-cloud]: https://www.wolframcloud.com/
[wolfram-docs]: https://reference.wolfram.com/language/
[function-repo]: https://resources.wolframcloud.com/FunctionRepository/
[wolfram-writings]: https://writings.stephenwolfram.com/
[amsart]: https://ctan.org/pkg/amsart
[biblatex]: https://ctan.org/pkg/biblatex
