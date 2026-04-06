# Knowledge Graphs as Research Notes — From Personal to LOD

*How nodes and edges replaced my Word docs and spreadsheets, and how Claude Code made it possible.*

---

## The Old Barrier

Building a knowledge graph used to require either serious technical infrastructure or a funded project with developers. You needed a triple store or a graph database, an ontology, an ingest pipeline, maybe a SPARQL endpoint. The barrier was so high that knowledge graphs remained the province of large digital humanities projects — useful in principle, inaccessible in practice for a researcher working alone on a specific question.

That's changed. With Claude Code, I've been building knowledge graphs as a way to take research notes — and it turns out that nodes and edges are a better format for historical research than anything I've used before.

## Why Nodes and Edges?

Every historian has a system for research notes. Word documents, Excel spreadsheets, index cards, Zotero libraries, folders of photographs. The problem is always the same: as the material accumulates, the connections between sources get lost. You know you read something about a person six months ago, but where? You know two events are related, but the evidence is scattered across three different files.

A knowledge graph solves this by making connections first-class objects. Instead of writing a note that says "Kyd sent Banks tanning bark samples from Calcutta," you create nodes — Kyd, Banks, tanning bark, Calcutta — and edges between them: *sent to*, *located in*, *mentioned in*. The note and the structure are the same thing.

If you've ever used Gephi or drawn a network diagram, you already understand the concept. Nodes are things: people, places, commodities, institutions, sources, events. Edges are relationships between them. That's it.

The shift is simple but profound. In a Word document, information is organised by when you found it. In a spreadsheet, it's organised by whatever columns you chose at the start. In a knowledge graph, information is organised by what it's *about* — and every new note automatically connects to everything else you already know about the same people, places, and topics.

## Small: Dry Rot and Traditional Research

I've been using this method to trace the history of dry rot in the British Navy. There's no bulk data to process — it's traditional research. Searching through digitised 18th-century sources — books, pamphlets, parliamentary reports, Royal Society proceedings — looking for the earliest mentions of timber rot, naval ship decay, and the scientific debates around fungal damage. The kind of research where you're deep in ECCO and Google Books, following citation trails and cross-referencing dates.

Every time I find a new source, I don't add a line to a spreadsheet. I add nodes and edges. The graph has nodes for authors, fungi, years, and institutions — the Royal Society, Parliament, the Society for the Arts. There are bibliographical nodes for each source where I find a discussion of dry rot or timber preservation. There are event nodes for key crisis moments: ships condemned, committees convened, experiments ordered.

*This author* wrote *this work* in *this year*, discussing *this fungus*, citing *this earlier source*, presented to *this institution*. That's a note. But it's also structure. When I add a new source that mentions an author I've already encountered in a different context, the connection is already there. I don't have to remember it or search for it. The graph accumulates knowledge in a way that flat notes cannot — because the structure *is* the knowledge.

Claude Code makes this practical. I describe the nodes and edges I want to add, and it handles the data entry, the formatting, and the consistency. It's like having a research assistant who never loses the thread.

## Medium: The Banks Leather Network

The dry rot graph is small and growing. The Joseph Banks leather project shows what happens when the same method scales up and combines with machine transcription.

It started with a 2023 trip to the Sutro Library in San Francisco, where I photographed almost 1,000 images of 181 handwritten letters related to the British leather trade (1797-1817). I used Claude Code to write processing scripts that sent the photographs to Google's Gemini for handwriting recognition, then extracted structured entities from the transcriptions — outputting the results as nodes and edges.

I added the full correspondence network from Warren Dawson's *Calendar of the Banks Letters* at the British Library — nearly 7,000 entries — then pulled in select people related to leather and India from Neil Chambers' *Indian and Pacific Correspondence*. But the core of the work was still note-taking. I was trying to figure out a specific question: how did Banks identify catechu as a tanning agent?

The leather network ended up with 275 people, 55 commodities, 119 places, and 46 institutions — 495 nodes in total. That's modest. But it revealed connections that sequential reading couldn't.

The graph showed that Banks was the switchboard connecting Indian botanical research to British industrial policy — routing knowledge between people who would never otherwise have been in the same room. Robert Kyd at the Calcutta Botanic Garden, Charles Jenkinson in the House of Lords, Samuel Purkis the tanner, Andrew Berry conducting tanning experiments — the graph reveals them as parts of a single coordinated network, with Banks at its centre.

Working through the graph drove biographical research. I ended up tracing the lives of all the key correspondents. One surprise: Samuel Purkis and Humphry Davy were already friends before Davy began working with Banks, and Purkis had been corresponding with Banks throughout the 1790s. The graph didn't explain the connection — but it surfaced it, turning a name on a letter into a question worth investigating further.

## Visualizations as Research Tools

Claude Code also built the visualizations — and the most important one was a research tool, not a presentation.

The first was a dual-pane timeline: over 230 events on the left, with a sidebar showing details and the original transcriptions. By laying the transcriptions out chronologically, I could check the machine-generated text against my own reading. This is where I caught Gemini misreading the signature on an important letter from Robert Kyd. Without the timeline putting that letter in context — surrounded by other Kyd correspondence — I might not have noticed.

From there, Claude Code built a force-directed knowledge graph (all 495 nodes, filterable by type) and something I'm particularly excited about: a temporal network. Standard tools give you either a timeline or a network graph — not both. The temporal network fuses them. Years are fixed along the x-axis from left to right, and people float below, pulled toward the years when they wrote or received letters. The gravitational force reveals temporal patterns: you can see correspondents cluster around their most active periods, watch the network grow as the crisis develops, and spot the moment when the conversation shifted from botanical science to industrial policy. I don't think this kind of hybrid layout existed as an off-the-shelf option before — it emerged from describing what I wanted to see and letting Claude Code figure out the implementation.

All of these are self-contained HTML files — no server, no build step. You can open them in a browser or host them on GitHub Pages.

This is the key point about bespoke visualizations. Because Claude Code builds through conversation — "the nodes are too cluttered, can we add filtering?", "can we anchor the years and let the people float?" — each visualization matches the research question rather than the defaults of a generic tool. You can invent new layouts that don't exist in any library's dropdown menu. Visualizations that would have required hiring a developer or learning D3.js are now part of the normal research workflow.

## Large: From Personal Graphs to Linked Open Data

The dry rot and leather graphs are personal research tools — my nodes, my edges, my questions. But the same thinking scales.

I've been involved with [LINCS](https://lincsproject.ca/) (Linked Infrastructure for Networked Cultural Scholarship), a project that builds linked open data infrastructure for cultural heritage across North America. One of its datasets, [Historical Canadians](https://lincsproject.ca/docs/explore-lod/project-datasets/hist-cdns/), augments biographical information from the *Dictionary of Canadian Biography* with data from Wikidata and scholarly sources — documenting individuals, their familial connections, occupations, residences, and gender identities, modelled using CIDOC-CRM and queryable via SPARQL.

That's the far end of the spectrum: formal ontologies, institutional infrastructure, interoperability between datasets. It's important work. But the point I want to make is that the distance between a personal research graph and a project like LINCS is shorter than it looks. The underlying logic is the same — nodes and edges, entities and relationships. A dry rot graph built in an afternoon and a LOD dataset serving an international scholarly community are different in scale and formality, but not in kind. The habits of structured thinking you develop building a small graph are exactly the habits that make large-scale linked data projects legible and useful.

And the barrier to starting has collapsed. You don't need a grant or a developer. You need a research question, a willingness to think in nodes and edges, and Claude Code.

## Try It

The Banks leather network visualizations are live at the [GitHub repository](https://github.com/jburnford/JosephBanksKG). The data sources are Warren Dawson's *[The Banks Letters: A Calendar](https://www.biodiversitylibrary.org/bibliography/153857)* (1958), Neil Chambers' *Indian and Pacific Correspondence of Sir Joseph Banks* (2008), and 181 transcribed letters from the Sutro Library.

If you're a historian or researcher taking notes in Word documents and spreadsheets — consider nodes and edges instead. Start small. The graph will grow with your research, and you might be surprised how far it takes you.
