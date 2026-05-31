---
title:      "Computational research and AI"
categories: [Software, Wolfram]
mathjax:    false
utterances: true
---

*This post is a living document. Last updated on 2026-05-31.*

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

### Version 3.8 (2026-05-31)

[Version 3.8.0][comp-research] makes Wolfram execution **MCP-first**: work runs in one persistent [Wolfram MCP][wolfram-mcp] kernel rather than spawning a new kernel per call, so the plugin stays within the license's kernel budget. Standalone scripts become a fallback for when no kernel is shared.

### Version 3.2 (2026-05-29)

[Version 3.2.0][comp-research] adds a more focused work-tracking workflow, with one place for specifications, task checklists, and session progress, together with a lighter planning process to limit context rot. Planning also moves out of the wiki and into a workflow better suited to version control.

### Version 3 (2026-04-12)

[Version 3.0.0][comp-research] expands the plugin from a wiki-centric research tool into a full project lifecycle manager: scaffolding for research projects, paclet repos, and standalone paclets; skills for building and publishing paclets to [Wolfram Cloud][wolfram-cloud]; LaTeX paper scaffolding with [amsart][amsart] and [biblatex][biblatex]; and search across the [Wolfram ecosystem][wolfram-docs] (documentation, [Function Repository][function-repo], [Community][wolfram-community], [writings][wolfram-writings], [Physics Project][WP]).

### Version 2 (2026-04-05)

[Version 2.0.0][comp-research] introduces a plain-markdown wiki as the central knowledge base — readable by both LLMs and humans, version-controlled, with cross-references the LLM navigates instead of scanning every file. Resources and notebooks are stored as Markdown with recovery instructions, built on demand (idea by [sw1sh][sw1sh]). A revision protocol prevents the LLM from overwriting human-edited content. A tour skill walks through the project from simple to advanced.

The core [MCP][mcp] servers remain [Wolfram MCP][wolfram-mcp] (or the unofficial [wolfram-mcp][wolfram-mcp-sw1sh] with [LSP][lsp] support) and [arXiv-mcp][arxiv-mcp] (plus [arxiv-latex-mcp][arxiv-latex-mcp] for reading LaTeX source).

### Version 1 (2026-03-04)

The first version of the [plugin][comp-research] bundled a few Claude skills: wolfram-notebook for creating Wolfram notebooks from prompts via Markdown import (an idea by [sw1sh][sw1sh]), and computational-exploration for scaffolding a structured research project.

The skill searched [arXiv][arxiv] and [Wolfram Community][wolfram-community] for papers, downloaded them, and produced organized notes with citations. Planned skills included notes-to-article, list-topics, setup-experiment, and polish-research.

After using this on several projects, I found the design too broad and not goal-oriented enough. Exploration, resource management, and knowledge organization were tangled together. Knowledge was spread across `CLAUDE.md`, notebooks, LaTeX notes, and resources. Generated notebooks were redundant to store, as they can be imported from Markdown anyway. Resources had no recovery mechanism, so a fresh clone lost all downloaded papers. And there was no revision protocol, so the LLM could overwrite user-edited content.

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
