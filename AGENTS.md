This is a presentation for the 2026 Annual Water Resources Conference this November 9-11 in Philadelphia, PA. 

I am one of the core developers of Geoconnex. The talk should be structured in a way that people get a better sense for what I do as a developer in the geoconnex community. My audience will be a mix of public sector, private sector, and academic professionals who are in a variety of Integrated Water Resources Management roles. IT professionals and people who have background in the technical details will be there but they are not the core audience for the talk.

It should be around a 15 minute presentation. It should use a water and graph based visual motif design style according to cgs design guidelines. 

The Geoconnex docs can be found at https://docs.geoconnex.us/ and the querying skills are provided in this repo even though they may be unnecessary to call out since they may be too technical. You should use slidev to structure this presentation. The slides should have a variety of useful diagrams and limit excessive text content on the slides. 

Here is the abstract that this presentation should seek to address:

Linking the Fabric: Persistent Identifiers and the geoconnex Knowledge Graph
A hydrofabric is most useful when its features can be referenced unambiguously by other datasets, by other agencies, and by other models. Without that, every integration becomes a custom join, and the same river reach ends up represented a dozen incompatible ways across the federal data landscape. The geoconnex system addresses this problem directly: it mints persistent HTTP identifiers for water features, resolves them through 303 redirects to authoritative landing pages, and harvests embedded JSON-LD into a knowledge graph that can be queried across organizational boundaries. This talk describes how geoconnex connects to the community hydrofabric work presented earlier in the session. Reference feature collections, including mainstems, HUCs, aquifers, dams, gages, and administrative geographies, are served via OGC API - Features at reference.geoconnex.us. When a monitoring location, model output, or local dataset is published referencing a geoconnex URI, it inherits a stable handle that other systems can resolve without prior coordination. We will walk through several concrete examples: linking USGS and other streamgages to mainstems and downstream reservoirs, connecting reservoir operations data to the reference hydrography, and assembling a watershed report from heterogenous data sources on the fly by a single feature from PID resolution through landing page, JSON-LD, and SPARQL query. We will also discuss the practical mechanics of contributing to the system: how data providers expose JSON-LD on their own pages, how sideloaded data is incorporated when self-hosting is not feasible, and how vocabulary alignment through SKOS lets organizations keep their own terms while remaining interoperable. The talk closes with where the linkage layer is thin today and where the community can usefully invest: more authoritative and informative landing pages and tighter coupling between geoconnex identifiers and the derived data that build on or reference the hydrofabric.

This is the full session context: https://events.rdmobile.com/Sessions/Details/3625808

It would be good to have slides on:
- Who am I: a Geoconnex core developer; work along Dave Blodgett at USGS and the wider Internet of Water community. My info can be found here: https://colton.place/ and https://colton.place/portfolio/
- What is Geoconnex
- What are persistent identifiers and what they accomplish in the Geoconnex system in a hydrologic context.
- What are controlled vocabularies and how they help interoperability. 
- How Geoconnex links across federal agencies
- How Geoconnex links a mainstem river with associated features. Embed https://internetofwater.github.io/Geoconnex-Feature-UI/ for that and I can give a live demo. 
- How organizations can contribute to Geoconnex
- Contact page for me at my email cloftus@lincolninst.edu and the github repo for Geoconnex at https://github.com/internetofwater/geoconnex.us