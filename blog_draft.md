# Building Knowledge Graphs for Historical Research — With Help From Claude Code

*How a simple structured approach to 18th-century correspondence revealed networks, trade routes, and institutional connections that narrative reading alone would miss.*

---

A few months ago I started building a knowledge graph around Sir Joseph Banks — the naturalist, President of the Royal Society, and arguably the most connected scientific figure in the late Georgian world. The dataset was modest: Warren Dawson's 1958 *Calendar of the Banks Letters* (nearly 7,000 entries), Neil Chambers' *Indian and Pacific Correspondence*, and 181 transcribed letters from the Sutro Library dealing with the British leather trade.

What I want to share isn't the history itself (though the leather crisis story is fascinating). It's the method — and specifically, how building even a basic knowledge graph changes the way you see your sources, and how Claude Code turned out to be a surprisingly powerful tool for creating bespoke visualizations from that graph.

## Why a Knowledge Graph?

Historians have always built mental models of who knew whom, what was discussed, and how ideas moved. We do this by reading, note-taking, and accumulating a kind of tacit spatial sense of a correspondence network. The problem is that this mental model doesn't scale, it's hard to share, and it's impossible to interrogate systematically.

A knowledge graph makes the implicit explicit. At its simplest, it's just structured triples: **Person → wrote to → Person**, **Letter → mentions → Commodity**, **Person → located in → Place**. Nothing fancy. No ontology committee required.

For the Banks project, I ended up with a graph built from over 7,000 documents, covering around 700 correspondents (plus several hundred more people mentioned in the letters), thousands of commodity references, and places spanning Britain, India, continental Europe, and the Pacific. These aren't numbers that impress anyone working in data science. But for a single historical figure's correspondence network, they're rich enough to surface patterns that are genuinely hard to see through sequential reading.

For instance: the leather crisis. Reading the Sutro letters one by one, you follow a narrative about tanning shortages and botanical alternatives. But when you structure those letters as a graph — connecting Banks to correspondents like William Roxburgh in Calcutta, to commodities like Indian tanning barks, to institutions like the East India Company and Parliament — you start to see the *system*. Banks wasn't just receiving letters about leather. He was the switchboard connecting Indian botanical research to British industrial policy, routing knowledge between people who would never otherwise have been in the same room.

That's the kind of insight a knowledge graph gives you. Not a replacement for close reading, but a scaffold for it.

## The Visualization Problem

Once you have a knowledge graph, you want to *see* it. And this is where most researchers hit a wall.

The standard tools — Gephi, Neo4j Bloom, various network analysis packages — are excellent for exploration. But they produce generic outputs. If you want a visualization that actually communicates your argument — that shows the temporal evolution of a network, or traces commodity flows from decades through trade goods to specific places — you need something custom.

Custom usually means learning D3.js, or finding a developer, or spending weeks wrestling with a JavaScript framework when you'd rather be reading letters. This is the gap where Claude Code turned out to be genuinely useful.

## Claude Code as a Visualization Partner

Claude Code is Anthropic's agentic coding tool. You give it a task, it reads your files, writes code, runs it, and iterates until the output is right. I used it to build six interactive visualizations directly from my knowledge graph data, each tailored to a specific research question.

Here's what that looked like in practice:

**The correspondence Sankey.** I wanted to show the top 100 people who wrote to Banks and the top 100 he wrote to, organized by decade. A standard network graph would have been unreadable at that scale. Instead, I described what I wanted — a bi-directional flow diagram with decades as the spine — and Claude Code produced a Plotly.js Sankey diagram. Teal flows on the left for letters received, orange on the right for letters sent. The result immediately shows that Banks' network exploded in the 1780s and 1790s, and you can see at a glance which correspondents persisted across decades versus those who appeared briefly.

**The temporal network.** For the leather crisis specifically, I wanted to see how the network changed over time — who entered Banks' orbit in which years, how the conversation shifted from pure botany to industrial policy. Claude Code built a vis.js network with year nodes anchored horizontally and people floating based on their letter connections. You can watch the network grow and shift as the crisis develops.

**The commodity flow diagram.** This one maps decades to commodities (Plants, Seeds, Books, Leather, Metals, and more) to geographic places. It answers a deceptively simple question: what was being discussed in connection with which places, and when? The answer revealed that "Plants" dominates early decades and connects overwhelmingly to India and Kew, while "Books" flows more toward continental Europe.

**The combined timeline and knowledge graph.** This dual-pane visualization pairs a scrollable timeline of 45 key milestones with an interactive network graph. Click an event — say, "Roxburgh arrives in India" in 1781 — and the sidebar shows the relevant context and links to the underlying documents. This was the hardest to build manually but perhaps took the least time with Claude Code, because I could describe the two-panel layout conversationally and iterate on the interaction design.

In every case, the workflow was the same: I described what I wanted to show, pointed Claude Code at the data, and refined the output through conversation. The visualizations are all self-contained HTML files — no server, no build step, no dependencies to manage. You can open them in a browser, host them on GitHub Pages, or email them to a colleague. Each one embeds its data directly, making them permanently portable.

## What I Learned

**Start simple.** My knowledge graph is just entities and relationships extracted from structured catalogue data and letter transcriptions. I didn't build an OWL ontology or set up a triple store. A well-structured JSON file was enough to power every visualization in the project.

**The graph is a thinking tool, not just an output.** Building the graph forced me to make decisions — is "leather" a commodity or a topic? Is the East India Company a person or an institution? — that sharpened my understanding of the material. Every modeling choice is an interpretive act.

**Bespoke beats generic.** A custom visualization built around your specific research question communicates more than any general-purpose network diagram. When you can design the visual encoding to match your argument — decades as a horizontal axis, commodity types as color-coded diamonds, flow width as letter count — the visualization becomes part of the scholarship, not just an illustration.

**Claude Code lowers the barrier dramatically.** I'm not a JavaScript developer. I could not have built these visualizations from scratch in any reasonable timeframe. But I know what I want to show and why. Claude Code bridges that gap — you bring the research judgment, it handles the implementation. The conversation is iterative: you see a first draft, say "the nodes are too cluttered, can we add filtering?", and it revises. It feels less like programming and more like directing.

## Try It

The visualizations are live at the [GitHub repository](https://github.com/jburnford/JosephBanksKG). The data sources are Warren Dawson's *[The Banks Letters: A Calendar](https://www.biodiversitylibrary.org/bibliography/153857)* (1958), Neil Chambers' *Indian and Pacific Correspondence of Sir Joseph Banks* (2008), and 181 transcribed letters from the Sutro Library.

If you're a historian or researcher sitting on correspondence data, catalogue records, or any structured source material — consider building a knowledge graph. It doesn't have to be complicated. And if the visualization tools have been the bottleneck, they don't have to be anymore.
