# Building Knowledge Graphs for Historical Research — With Claude Code

*How nodes and edges replaced my Word docs and spreadsheets, and why a knowledge graph is the best note-taking method I've found for historical research.*

---

In the late 18th century, Britain had a leather problem. The tanning industry depended on oak bark, supplies were tightening, and the quality of British leather was declining. Sir Joseph Banks — naturalist, President of the Royal Society, and the most connected scientific broker of the Georgian age — found himself at the centre of a sprawling effort to find botanical alternatives, drawing on correspondents from Calcutta to Parliament.

I've been building a knowledge graph around this story, and I want to share the method. Not because the technology is novel — it isn't. But because a knowledge graph turns out to be the best way I've found to take research notes, and Claude Code made the whole process possible.

## Notes as Nodes and Edges

Every historian has a system for research notes. Word documents, Excel spreadsheets, index cards, Zotero libraries, folders of photographs. The problem is always the same: as the material accumulates, the connections between sources get lost. You know you read something about a person six months ago, but where? You know two events are related, but the evidence is scattered across three different files.

A knowledge graph solves this by making connections first-class objects. Instead of writing a note that says "Kyd sent Banks tanning bark samples from Calcutta," you create nodes — Kyd, Banks, tanning bark, Calcutta — and edges between them: *sent to*, *located in*, *mentioned in*. The note and the structure are the same thing.

This isn't linked data or semantic web technology. If you've ever used Gephi or drawn a network diagram, you already understand the concept. Nodes are things (people, places, commodities, institutions, sources, events). Edges are relationships between them. That's it. No ontology committee required.

The shift is simple but profound. In a Word document, information is organised by when you found it. In a spreadsheet, it's organised by whatever columns you chose at the start. In a knowledge graph, information is organised by what it's *about* — and every new note automatically connects to everything else you already know about the same people, places, and topics.

## The Leather Network

I started building the leather knowledge graph after a 2023 trip to the Sutro Library in San Francisco, where I photographed almost 1,000 images of 181 handwritten letters related to the British leather trade (1797-1817). I used Claude Code to write processing scripts that sent the photographs to Google's Gemini for handwriting recognition, then extracted structured entities from the transcriptions. Claude Code handled the pipeline: ingesting images, calling the Gemini API, parsing the results, and structuring the output as nodes and edges.

I added the full correspondence network from Warren Dawson's *Calendar of the Banks Letters* at the British Library — nearly 7,000 entries — then pulled in select people related to leather and India from Neil Chambers' *Indian and Pacific Correspondence*. But the core of the work was note-taking. I was trying to figure out a specific historical question: how did Banks identify catechu as a tanning agent? Every letter I read, every connection I noticed, every commodity mentioned — it went into the graph as nodes and edges.

The leather network ended up with 275 people, 55 commodities, 119 places, and 46 institutions — 495 nodes in total. That's modest by any standard. But it was enough to see something you can't see by reading letters sequentially.

When you structure those letters as a graph — connecting Banks to William Roxburgh in Calcutta, to Samuel Purkis the tanner, to commodities like mimosa bark and terra japonica, to institutions like the East India Company and the House of Commons — you see the *system*. Banks wasn't just receiving letters about leather. He was the switchboard connecting Indian botanical research to British industrial policy, routing knowledge between people who would never otherwise have been in the same room. Robert Kyd at the Calcutta Botanic Garden, Charles Jenkinson in the House of Lords, Andrew Berry conducting tanning experiments — the graph reveals them as parts of a single coordinated network, with Banks at its centre.

## The Same Method, Different Sources: Dry Rot

The leather network started with archival photographs and machine transcription, but the same note-taking method works with entirely traditional research. I've been using it for a second project: tracing the history of dry rot in the British Navy.

For dry rot, there are no bulk transcriptions to process. The research is searching through digitised 18th-century sources — books, pamphlets, parliamentary reports, Royal Society proceedings — looking for the earliest mentions of timber rot, naval ship decay, and the scientific debates around fungal damage. The kind of research where you're deep in ECCO and Google Books, following citation trails and cross-referencing dates.

The graph has nodes for authors, fungi, years, institutions (the Royal Society, Parliament, the Society for the Arts), and bibliographical nodes for each source where I find a discussion of dry rot or timber preservation. There are event nodes for key crisis moments — ships condemned, committees convened, experiments ordered. Every time I find a new source, I don't add a line to a spreadsheet. I add nodes and edges: *this author* wrote *this work* in *this year*, discussing *this fungus*, citing *this earlier source*, presented to *this institution*.

The advantage is immediate. When I add a new source that mentions an author I've already encountered in a different context, the connection is already there in the graph. I don't have to remember it or search for it. The graph accumulates knowledge in a way that flat notes cannot — because the structure *is* the knowledge.

## The Timeline as a Review Tool

Back on the leather project, the first visualization I built was the most important — not because it was the most visually striking, but because it was a research tool.

I asked Claude Code to create a dual-pane timeline: a scrollable sequence of over 230 events on the left, with a sidebar on the right showing details and the original transcriptions. The events are grouped into categories — Science, Botanical, Economic, Material, Correspondence, Legislation — and span from the first *Encyclopaedia Britannica*'s craft description of tanning in 1771 through to the final letters in 1815.

The point was human review. By laying the transcriptions out chronologically alongside the knowledge graph data, I could read through every key source in context and check the machine-generated transcriptions against my own reading. This is where I caught an error: Gemini had misread the signature on an important letter from Robert Kyd. Without the timeline visualization putting that letter in context — surrounded by other Kyd correspondence, linked to the Calcutta Botanic Garden node in the graph — I might not have noticed.

Click "Fothergill publishes Kerr's terra japonica text" in 1773 and you see the beginning of the botanical thread. Click "Kyd's commercial pivot" in 1786 and you see the moment the Calcutta Botanic Garden turned toward industrial applications. The timeline makes the narrative arc visible in a way that a network graph alone cannot.

## The Graph as Biographical Research

Building the knowledge graph didn't just help me visualize connections I already knew about — it drove me to research ones I didn't. When you see a name appear as a node connected to Banks, to a commodity, to a place, you want to know who that person actually was. The graph made those gaps in my knowledge visible and urgent.

Working through the catechu network, I ended up researching and connecting the biographies of all the key correspondents. Who was Robert Kyd before he ran the Calcutta Botanic Garden? What was Andrew Berry's relationship to the East India Company? How did Samuel Purkis come to be the tanner Banks trusted with experimental barks? The graph turned each name from a signature on a letter into a research question, and answering those questions thickened the graph further — adding institutional affiliations, career timelines, and connections between people that the letters alone didn't make explicit.

One example: Samuel Purkis and Humphry Davy. The graph showed that Purkis and Banks were correspondents throughout the 1790s — well before Davy began his work with Banks. Researching their biographies revealed that Purkis and Davy were already friends. That connection reframes how Davy entered Banks' orbit on the tanning question: not cold, but through an existing relationship with someone Banks had been working with for years. You don't see that in any single letter. You see it in the graph.

This is the part of knowledge graph work that's hard to convey in a methods section. The graph isn't just a product of research — it's an engine for it. Each node you add raises questions that pull you deeper into the sources.

## Bespoke Visualizations With Claude Code

Once the data was reviewed and corrected, I used Claude Code to build two more interactive visualizations of the leather network.

**The knowledge graph.** A force-directed network of all 495 nodes. People appear as blue circles, commodities as orange diamonds, places as green squares, institutions as purple hexagons — with Banks as a red node at the centre. You can filter to show only people, or people and commodities together, and click any node to see its connections and source information. This is the "big picture" view — where you see the overall shape of the network and notice clusters you hadn't expected.

**The temporal network.** I wanted to see how the leather network changed over time — who entered Banks' orbit in which years, how the conversation shifted from pure botany to industrial policy. Claude Code built a vis.js network with year nodes (1773 to 1810) anchored horizontally and people floating based on their letter connections. You can watch the network grow and shift as the crisis develops — the early years dominated by scientific contacts, the later years drawing in politicians and manufacturers.

The visualizations are all self-contained HTML files — no server, no build step, no dependencies to manage. You can open them in a browser, host them on GitHub Pages, or email them to a colleague. Each one embeds its data directly, making them permanently portable. And because Claude Code built them through conversation — "the nodes are too cluttered, can we add filtering?" — the visual encoding matches the research argument rather than the defaults of a generic tool.

## What I Learned

**Nodes and edges beat flat notes.** A Word document organises information by when you found it. A spreadsheet locks you into columns you chose before you understood the material. A knowledge graph organises information by what it's about, and every new entry automatically connects to everything you already know. For research that involves tracking people, institutions, events, and sources across time, there is no better format.

**Small graphs are underrated.** You don't need thousands of nodes to gain insight. A 495-node graph built from 181 letters was enough to reshape my understanding of a forty-year episode in British industrial history. The constraint of a focused topic — leather, not all of Banks' correspondence — made the graph more interpretable, not less.

**The graph is a thinking tool, not just an output.** Building the graph forced me to make decisions — is "leather" a commodity or a topic? Is the East India Company a person or an institution? Does "My dear Lord" resolve to Charles Jenkinson? — that sharpened my understanding of the material. Every modelling choice is an interpretive act.

**Machine transcription needs human review, and visualizations make that review possible.** Gemini did a remarkable job with 18th-century handwriting, but it wasn't perfect. The timeline visualization — built by Claude Code — was what let me catch errors like the misattributed Kyd letter. The tools for creating the data and the tools for reviewing it were part of the same workflow.

**Claude Code is the method, not just a tool.** It wrote the image processing scripts, built the transcription pipeline, created the timeline for human review, and produced the final interactive visualizations. The gap between raw archival photographs and interactive scholarship is shorter than you might think.

## Try It

The leather network visualizations are live at the [GitHub repository](https://github.com/jburnford/JosephBanksKG). The data sources are Warren Dawson's *[The Banks Letters: A Calendar](https://www.biodiversitylibrary.org/bibliography/153857)* (1958), Neil Chambers' *Indian and Pacific Correspondence of Sir Joseph Banks* (2008), and 181 transcribed letters from the Sutro Library.

If you're a historian or researcher taking notes in Word documents and spreadsheets — consider nodes and edges instead. You don't need a computer science background. If you've used Gephi, you already understand the model. And with Claude Code, you can go from a pile of archival photographs or a stack of digitised sources to an interactive, explorable knowledge graph without writing JavaScript yourself.
