---
title:      "Computational research and AI"
categories: [Software, Wolfram]
mathjax:    false
utterances: true
---

# Computational research and AI

At the [Wolfram Institute][WI], I study ideas from mathematical physics in the framework of [Wolfram models][WP] and perform novel **computational research** — the process of designing the least complex discrete model of phenomena, implementing it, setting up a computational experiment, doing empirical research, searching for emergent patterns and laws, and formulating interesting questions.

Concretely, I brainstorm ideas, read papers, distill suitable constructions, implement them in [Wolfram Language][WL], create Wolfram notebooks for playing and presentation, and eventually contribute to Wolfram Institutes's projects, paclets, or write something myself.

## Utilizing AI

I have used AI for two years in a basic way for chat, reformats, and corrections. Previously working in a corporate environment, I was very anxious about the scope of the context and correctness. The pinnacle of my AI usage was utilizing most functionality of the [CodeCompanion][codecompanion] plugin for [Neovim][neovim], except agents.

A turning point came with the release of [Claude Opus 4.5][opus]. I got into agentic workflows and started offloading more and more tasks to Claude without direct interaction with the code — just guidance and specifications. The results are surprisingly good. My first wow moment was vibe-coding an app to manage and time-track my weekly tasks in Swift just from a screenshot of my wife's Excel table. It works well even though I have never looked at the code or programmed in Swift. It seems like in the near future everybody will be able to define an app they need and let the AI build it, like playing a song on a jukebox.

Coding prototypes to get from A to B fast without having to dig deep and with satisfactory results also seems to be solved. When there is a need to improve the result, the easiest is to direct AI to reuse fragments of previous code and templates. When I have time or really need speed or specific architecture, I still work on improvements myself, but AI gives me the option to strategically skip it for the time being. As for the process of computational research, I think that it is the time to define an **agentic workflow** and **best practices** even though general standards and guidelines seem to be yet missing. I decided to stick with the Claude ecosystem and start writing a [plugin that captures my workflow][comp-research].

## Computational research plugin

The [plugin][comp-research] is a work in progress bundling several Claude skills and tools. Currently I have **wolfram-notebook**, which creates a Wolfram notebook from a prompt via import from Markdown without touching the front end (an idea of [sw1sh](https://github.com/sw1sh)), and the **research project skill**, which scaffolds a research project and performs an initial scouting and gathering of resources:

```
Infrageometry/
├── CLAUDE.md
├── Infrageometry1.nb
├── Code/
│   ├── Tools.wl
│   ├── Infrageometry.wl
│   └── InfrageometryVisualization.wl
├── Papers1.nb
├── Papers/
└── Article/
    ├── article1.tex
    ├── notes1.tex
    └── references.bib
```

The skill searches [arXiv][arxiv] and [Wolfram Community][wolfram-community] for relevant papers and resources, downloads them, writes summaries, and writes organized notes with citations. I always want to write the final article myself, but the notes serve as well-formatted extended memory suitable for both me and Claude, where I can just dump ideas and resources and Claude takes care of the rest.

The core MCP servers are [Wolfram MCP][wolfram-mcp], or the unofficial [wolfram-mcp][wolfram-mcp-sw1sh] (with LSP support) to evaluate WL code and create notebooks, and [arXiv-mcp][arxiv-mcp] to search and download arXiv papers.

## Missing pieces

- **Central database to store both verified and incomplete math.** Something like [Lean][lean] but tolerant of partially defined objects to lower the threshold for using it. This should remove the necessity to write math papers. A researcher just inputs new results and a reader will generate a paper that is suitable for him to study using his AI.
- **Agent definition.** What is an agent? Is there an agent that creates agents? Can I reuse it in different contexts?
- **Orchestration graph.** A workflow graph including agents, exact tools, and humans. It should be possible to compile it into a minimal version where most tasks are performed by tools (a better version of [LLMGraph][llmgraph]?).

## Human role

It is clear that AI will make certain hard skills obsolete. Paradigm changes are good, and letting things go and starting anew deepens life experience. There are still some things left for us though:

- **Curiosity.** The drive to explore a direction and go as far as possible by asking and tasking.
- **Ideas.** Find an AI-unsolvable problem interesting for your group of humans, zoom in, and challenge yourself to solve it.
- **Coordination.** Define your workflow, which agents do what, how they interact, and when a human intervenes.
- **Communication.** Spread enthusiasm among humans about your problem and convince them it is worth their time and resources.

[WI]: https://wolframinstitute.org/
[WP]: https://www.wolframphysics.org/
[WL]: https://www.wolfram.com/language/
[codecompanion]: https://github.com/olimorris/codecompanion.nvim
[neovim]: https://neovim.io/
[opus]: https://www.anthropic.com/news/claude-opus-4-5
[comp-research]: https://github.com/p135246/computational-research
[arxiv]: https://arxiv.org/
[wolfram-community]: https://community.wolfram.com/
[wolfram-mcp]: https://www.wolfram.com/artificial-intelligence/foundation-tool/
[wolfram-mcp-sw1sh]: https://github.com/sw1sh/WolframMCP
[arxiv-mcp]: https://github.com/blazickjp/arxiv-mcp-server
[lean]: https://lean-lang.org/
[llmgraph]: https://reference.wolfram.com/language/ref/LLMGraph.html
