# Building Knowledge Graphs for Historical Research — With Claude Code

*How almost 1,000 photographs of 18th-century letters became a 495-node knowledge graph, and how Claude Code was the method the whole way through.*

---

In the late 18th century, Britain had a leather problem. The tanning industry depended on oak bark, supplies were tightening, and the quality of British leather was declining. Sir Joseph Banks — naturalist, President of the Royal Society, and the most connected scientific broker of the Georgian age — found himself at the centre of a sprawling effort to find botanical alternatives, drawing on correspondents from Calcutta to Parliament.

I've been building a knowledge graph around this story, and I want to share the method. Not because Claude Code was a useful add-on at the end — it was the method, from start to finish.

## Starting With Photographs

The project began with a 2023 trip to the Sutro Library in San Francisco, where I photographed almost 1,000 images of 181 handwritten letters related to the British leather trade (1797-1817). Handwritten. Late 18th-century handwritten. The kind of material that sits in archives because the barrier to working with it at scale is so high.

The first step was transcription. I used Claude Code to write processing scripts that sent the photographs to Google's Gemini for handwriting recognition, then extracted structured entities — people, places, commodities, institutions — from the transcriptions. Claude Code handled the pipeline: ingesting images, calling the Gemini API, parsing the results, and structuring the output into a format I could build on.

This wasn't a fire-and-forget process. The transcriptions needed human review, and the knowledge graph was the tool that made that review possible.

## The Knowledge Graph as Structured Note-Taking

I added the full correspondence network from Warren Dawson's *Calendar of the Banks Letters* at the British Library — nearly 7,000 entries — then pulled in select people related to leather and India from Neil Chambers' *Indian and Pacific Correspondence*. But the core of the work was more intimate than bulk data processing. It was structured note-taking.

I was trying to figure out a specific historical question: how did Banks identify catechu as a tanning agent? The knowledge graph became the way I tracked that question across sources. Every letter I read, every connection I noticed, every commodity mentioned — it went into the graph as structured triples: **Person → wrote to → Person**, **Letter → mentions → Commodity**, **Person → located in → Place**. Nothing fancy. No ontology committee required.

The leather network ended up with 275 people, 55 commodities, 119 places, and 46 institutions — 495 nodes in total. That's modest by any standard. But it was enough to see something you can't see by reading letters sequentially.

When you structure those letters as a graph — connecting Banks to William Roxburgh in Calcutta, to Samuel Purkis the tanner, to commodities like mimosa bark and terra japonica, to institutions like the East India Company and the House of Commons — you see the *system*. Banks wasn't just receiving letters about leather. He was the switchboard connecting Indian botanical research to British industrial policy, routing knowledge between people who would never otherwise have been in the same room. Robert Kyd at the Calcutta Botanic Garden, Charles Jenkinson in the House of Lords, Andrew Berry conducting tanning experiments — the graph reveals them as parts of a single coordinated network, with Banks at its centre.

## The Timeline as a Review Tool

The first visualization I built was the most important — not because it was the most visually striking, but because it was a research tool.

I asked Claude Code to create a dual-pane timeline: a scrollable sequence of over 230 events on the left, with a sidebar on the right showing details and the original transcriptions. The events are grouped into categories — Science, Botanical, Economic, Material, Correspondence, Legislation — and span from the first *Encyclopaedia Britannica*'s craft description of tanning in 1771 through to the final letters in 1815.

The point was human review. By laying the transcriptions out chronologically alongside the knowledge graph data, I could read through every key source in context and check the machine-generated transcriptions against my own reading. This is where I caught an error: Gemini had misread the signature on an important letter from Robert Kyd. Without the timeline visualization putting that letter in context — surrounded by other Kyd correspondence, linked to the Calcutta Botanic Garden node in the graph — I might not have noticed.

Click "Fothergill publishes Kerr's terra japonica text" in 1773 and you see the beginning of the botanical thread. Click "Kyd's commercial pivot" in 1786 and you see the moment the Calcutta Botanic Garden turned toward industrial applications. The timeline makes the narrative arc visible in a way that a network graph alone cannot.

## The Graph as Biographical Research

Building the knowledge graph didn't just help me visualize connections I already knew about — it drove me to research ones I didn't. When you see a name appear as a node connected to Banks, to a commodity, to a place, you want to know who that person actually was. The graph made those gaps in my knowledge visible and urgent.

Working through the catechu network, I ended up researching and connecting the biographies of all the key correspondents. Who was Robert Kyd before he ran the Calcutta Botanic Garden? What was Andrew Berry's relationship to the East India Company? How did Samuel Purkis come to be the tanner Banks trusted with experimental barks? The graph turned each name from a signature on a letter into a research question, and answering those questions thickened the graph further — adding institutional affiliations, career timelines, and connections between people that the letters alone didn't make explicit.

This is the part of knowledge graph work that's hard to convey in a methods section. The graph isn't just a product of research — it's an engine for it. Each node you add raises questions that pull you deeper into the sources.

## From Graph to Visualization

Once the data was reviewed and corrected, I used Claude Code to build two more interactive visualizations of the leather network.

**The knowledge graph.** A force-directed network of all 495 nodes. People appear as blue circles, commodities as orange diamonds, places as green squares, institutions as purple hexagons — with Banks as a red node at the centre. You can filter to show only people, or people and commodities together, and click any node to see its connections and source information. This is the "big picture" view — where you see the overall shape of the network and notice clusters you hadn't expected.

**The temporal network.** This was the more interesting experiment. I wanted to see how the leather network changed over time — who entered Banks' orbit in which years, how the conversation shifted from pure botany to industrial policy. Claude Code built a vis.js network with year nodes (1773 to 1810) anchored horizontally and people floating based on their letter connections. You can watch the network grow and shift as the crisis develops — the early years dominated by scientific contacts, the later years drawing in politicians and manufacturers.

The visualizations are all self-contained HTML files — no server, no build step, no dependencies to manage. You can open them in a browser, host them on GitHub Pages, or email them to a colleague. Each one embeds its data directly, making them permanently portable.

## What I Learned

**The whole pipeline is the point.** Claude Code wasn't just useful for the visualizations at the end. It wrote the image processing scripts, built the transcription pipeline, and created the review tools. The method is Claude Code the whole way through — from raw photographs to finished interactive visualizations.

**Small graphs are underrated.** You don't need thousands of nodes to gain insight. A 495-node graph built from 181 letters was enough to reshape my understanding of a forty-year episode in British industrial history. The constraint of a focused topic — leather, not all of Banks' correspondence — made the graph more interpretable, not less.

**The graph is a thinking tool, not just an output.** Building the graph forced me to make decisions — is "leather" a commodity or a topic? Is the East India Company a person or an institution? Does "My dear Lord" resolve to Charles Jenkinson? — that sharpened my understanding of the material. Every modelling choice is an interpretive act.

**Machine transcription needs human review, and visualizations make that review possible.** Gemini did a remarkable job with 18th-century handwriting, but it wasn't perfect. The timeline visualization — built by Claude Code — was what let me catch errors like the misattributed Kyd letter. The tools for creating the data and the tools for reviewing it were part of the same workflow.

**Bespoke beats generic.** A custom visualization built around your specific research question communicates more than any general-purpose network diagram. When you can design the visual encoding to match your argument — years as a horizontal axis, entity types as distinct shapes, node size reflecting documentary weight — the visualization becomes part of the scholarship, not just an illustration.

## Try It

The visualizations are live at the [GitHub repository](https://github.com/jburnford/JosephBanksKG). The data sources are Warren Dawson's *[The Banks Letters: A Calendar](https://www.biodiversitylibrary.org/bibliography/153857)* (1958), Neil Chambers' *Indian and Pacific Correspondence of Sir Joseph Banks* (2008), and 181 transcribed letters from the Sutro Library.

If you're a historian or researcher sitting on archival photographs, correspondence data, or any structured source material — consider building a knowledge graph. It doesn't have to be big. And with Claude Code, the gap between raw sources and interactive scholarship is shorter than you might think.
