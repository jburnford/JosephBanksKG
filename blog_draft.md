# Building Knowledge Graphs for Historical Research — With Help From Claude Code

*How 181 letters about leather became a 495-node knowledge graph, and how Claude Code turned it into interactive visualizations I couldn't have built myself.*

---

In the late 18th century, Britain had a leather problem. The tanning industry depended on oak bark, supplies were tightening, and the quality of British leather was declining. Sir Joseph Banks — naturalist, President of the Royal Society, and the most connected scientific broker of the Georgian age — found himself at the centre of a sprawling effort to find botanical alternatives, drawing on correspondents from Calcutta to Parliament.

I've been building a knowledge graph around this story, drawn primarily from 181 transcribed letters in the Sutro Library (1797-1817), supplemented by Warren Dawson's *Calendar of the Banks Letters* and Neil Chambers' *Indian and Pacific Correspondence*. What I want to share isn't the leather crisis itself (though it's a remarkable story). It's the method — how even a small, focused knowledge graph changes the way you see your sources, and how Claude Code turned out to be a surprisingly effective tool for creating bespoke visualizations from that graph.

## Why a Knowledge Graph?

Historians have always built mental models of who knew whom, what was discussed, and how ideas moved. We do this by reading, note-taking, and accumulating a kind of tacit spatial sense of a correspondence network. The problem is that this mental model doesn't scale, it's hard to share, and it's impossible to interrogate systematically.

A knowledge graph makes the implicit explicit. At its simplest, it's just structured triples: **Person → wrote to → Person**, **Letter → mentions → Commodity**, **Person → located in → Place**. Nothing fancy. No ontology committee required.

The leather network is a good example of how small can be powerful. It contains 275 people, 55 commodities, 119 places, and 46 institutions — 495 nodes in total, connected by relationships extracted from those 181 letters and their surrounding context. That's a modest dataset by any standard. But it's enough to see something you can't see by reading the letters sequentially.

Reading the Sutro letters one by one, you follow a narrative about tanning shortages and botanical alternatives. When you structure those same letters as a graph — connecting Banks to William Roxburgh in Calcutta, to Samuel Purkis the tanner, to commodities like mimosa bark and terra japonica, to institutions like the East India Company and the House of Commons — you start to see the *system*. Banks wasn't just receiving letters about leather. He was the switchboard connecting Indian botanical research to British industrial policy, routing knowledge between people who would never otherwise have been in the same room. Robert Kyd at the Calcutta Botanic Garden, Charles Jenkinson in the House of Lords, Andrew Berry conducting tanning experiments — the graph reveals them as parts of a single coordinated network, with Banks at its centre.

That's the kind of insight a knowledge graph gives you. Not a replacement for close reading, but a scaffold for it.

## The Visualization Problem

Once you have a knowledge graph, you want to *see* it. And this is where most researchers hit a wall.

The standard tools — Gephi, Neo4j Bloom, various network analysis packages — are excellent for exploration. But they produce generic outputs. If you want a visualization that actually communicates your argument — that shows the temporal evolution of a network, or distinguishes people from commodities from institutions — you need something custom.

Custom usually means learning D3.js, or finding a developer, or spending weeks wrestling with a JavaScript framework when you'd rather be reading letters. This is the gap where Claude Code turned out to be genuinely useful.

## Claude Code as a Visualization Partner

Claude Code is Anthropic's agentic coding tool. You give it a task, it reads your files, writes code, runs it, and iterates until the output is right. I used it to build three different interactive visualizations of the leather network, each designed to answer a different question about the same underlying data.

**The knowledge graph.** The first visualization is a force-directed network of all 495 nodes. People appear as blue circles, commodities as orange diamonds, places as green squares, institutions as purple hexagons — with Banks as a red node at the centre. You can filter to show only people, or people and commodities together, and click any node to see its connections and source information. This is the "big picture" view — where you see the overall shape of the network and notice clusters you hadn't expected.

**The temporal network.** This was the more interesting experiment. I wanted to see how the leather network changed over time — who entered Banks' orbit in which years, how the conversation shifted from pure botany to industrial policy. Claude Code built a vis.js network with year nodes (1773 to 1810) anchored horizontally and people floating based on their letter connections. You can watch the network grow and shift as the crisis develops — the early years dominated by scientific contacts, the later years drawing in politicians and manufacturers.

**The timeline.** This dual-pane visualization pairs a scrollable timeline of over 230 events with a sidebar showing details and original transcriptions. The events are grouped into categories — Science, Botanical, Economic, Material, Correspondence, Legislation — and span from the first *Encyclopaedia Britannica*'s craft description of tanning in 1771 through to the final letters in 1815. Click "Fothergill publishes Kerr's terra japonica text" in 1773 and you see the beginning of the botanical thread. Click "Kyd's commercial pivot" in 1786 and you see the moment the Calcutta Botanic Garden turned toward industrial applications. The timeline makes the narrative arc visible in a way that a network graph alone cannot.

In every case, the workflow was the same: I described what I wanted to show, pointed Claude Code at the data, and refined the output through conversation. The visualizations are all self-contained HTML files — no server, no build step, no dependencies to manage. You can open them in a browser, host them on GitHub Pages, or email them to a colleague. Each one embeds its data directly, making them permanently portable.

## What I Learned

**Small graphs are underrated.** You don't need thousands of nodes to gain insight. A 495-node graph built from 181 letters was enough to reshape my understanding of a forty-year episode in British industrial history. The constraint of a focused topic — leather, not all of Banks' correspondence — made the graph more interpretable, not less.

**The graph is a thinking tool, not just an output.** Building the graph forced me to make decisions — is "leather" a commodity or a topic? Is the East India Company a person or an institution? Does "My dear Lord" resolve to Charles Jenkinson? — that sharpened my understanding of the material. Every modelling choice is an interpretive act.

**Bespoke beats generic.** A custom visualization built around your specific research question communicates more than any general-purpose network diagram. When you can design the visual encoding to match your argument — years as a horizontal axis, entity types as distinct shapes, node size reflecting documentary weight — the visualization becomes part of the scholarship, not just an illustration.

**Claude Code lowers the barrier dramatically.** I'm not a JavaScript developer. I could not have built these visualizations from scratch in any reasonable timeframe. But I know what I want to show and why. Claude Code bridges that gap — you bring the research judgment, it handles the implementation. The conversation is iterative: you see a first draft, say "the nodes are too cluttered, can we add filtering?", and it revises. It feels less like programming and more like directing.

## Try It

The visualizations are live at the [GitHub repository](https://github.com/jburnford/JosephBanksKG). The data sources are Warren Dawson's *[The Banks Letters: A Calendar](https://www.biodiversitylibrary.org/bibliography/153857)* (1958), Neil Chambers' *Indian and Pacific Correspondence of Sir Joseph Banks* (2008), and 181 transcribed letters from the Sutro Library.

If you're a historian or researcher sitting on correspondence data, catalogue records, or any structured source material — consider building a knowledge graph. It doesn't have to be big. And if the visualization tools have been the bottleneck, they don't have to be anymore.
