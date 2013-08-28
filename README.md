BioNames: linking taxonomy, texts, and trees
============================================

Roderic D. M. Page
Institute of Biodiversity, Animal Health and Comparative Medicine
College of Medical, Veterinary and Life Sciences
Graham Kerr Building
University of Glasgow
Glasgow G12 8QQ, UK

# Abstract

BioNames is a web database of taxonomic names for animals, linked to the primary literature and, wherever possible, to phylogenetic trees. It aims to provide a biodiversity "dashboard" where at a glance we can see a summary of the taxonomic and phylogenetic information we have for a given taxon and hence provide a quick answer to the basic question "what is this taxon?" BioNames combines classifications from the Global Biodiversity Information Facility (GBIF) and GenBank, imagery from the Encyclopedia of Life (EOL), animal names from the Index of Organism Names (ION), and bibliographic data from multiple sources including the Biodiversity Heritage Library (BHL) and CrossRef. The user interface design includes display of full text articles, interactive timelines, and zoomable phylogenies. It is available at http://bionames.org.


# Introduction

Large-scale digitisation of biodiversity data is underway on at least three broad fronts. The first, and perhaps the only category that is genuinely "born digital" is DNA sequencing [Benson et al. 2012]. DNA barcoding [Hebert 2003] and, more recently, "metabarcoding" [Taberlet et al. 2012] is generating a flood of sequence data, much of it tied to a specific place and time. The contents of natural history collections are being digitised [Baird 2000], both the specimens themselves [Blagoderov et al. 2012] and metadata about those specimens. The latter is being aggregated by [GBIF](http://data.gbif.org) to provide an overview of the spatial distribution of life on Earth. Much of the biological literature is similarly being converted from physical to digital form, most notably by the [Biodiversity Heritage Library](http://www.biodiversitylibrary.org). Taxonomic publication is becoming increasingly digital through rise of "mega" journals such as [Zootaxa](http://www.mapress.com/zootaxa/), and semantically enriched journals such as [ZooKeys](http://www.pensoft.net/journals/zookeys/).

The increasing use of sequence data has made taxonomic relationships readily computable (e.g., by building phylogenetic trees). Yet many DNA sequences are disconnected from classical taxonomy because they lack formal taxonomic names [Page 2011c][Parr et al. 2012]. Barcoding has been responsible for a massive influx of these "dark taxa" into the sequence databases [Page 2011c]. Many of these unnamed barcode taxa have since been suppressed by Genbank. But even without the barcoding sequences, dark taxa have been steadily increasing in number in recent years. Names may have a special place in the hearts of taxonomists [Patterson et al. 2010], but the pace of biodiversity discovery is outstripping our ability to put names on taxa, as evidenced by the rise of dark taxa in GenBank. There are increasing calls to adopt less formal taxonomic naming schemes [Schindel and Miller 2010], or to focus on describing biodiversity without necessarily naming it [Deans et al. 2012][Maddison et al. 2012]. A significant challenge will be determining whether these dark taxa represent newly discovered taxa, or come from known taxa but have not been identified as such [Hibbett and Glotzer 2011][Nagy et al. 2011].

Most taxonomic databases are little more than online collections of 5×3 index cards, a technology taxonomy's founding father Linnaeus himself pioneered [Müller-Wille and Charmantier 2012]. When taxonomic literature is cited, it is typically as a text string, with no link to the growing corpus of digitised literature. Yet the vision of "Biodiversity Information on Every Desktop" [Edwards 2000] (perhaps updated to "biodiversity on every device") rests on our ability to not only digitise life (and the documents we have generated during centuries of cataloguing and studying biodiversity) but also to integrate the wealth of data emerging from sequencing machines and optical scanners. There are numerous points of contact between these different efforts, such as specimen codes, bibliographic identifiers, and GenBank accession numbers [Page 2008a][Page 2010] (Fig. MODEL). However, the most commonly shared identifier that spans sequences, specimens, and publications is the taxonomic name [Sarkar 2007] [Patterson et al. 2010], despite the potential ambiguity in what a given taxonomic name "means" [Kennedy et al. 2005] [Franz and Cardona-Duque 2013]. 

Figure. MODEL shows a simplified model of the core entities that make up taxonomy and related disciplines (e.g., systematics). The diagram is not meant to be exhaustive, nor does it attempt to rigorously define relationships in terms of one or more available ontologies. Instead, it simply serves as a way to visualise the links between taxon names, the publications (and authors and journals) where those names first appear, the application of those names to taxa, and data associated with those taxa (e.g., DNA sequence-based phylogenies).

![MODEL](https://raw.github.com/rdmpage/bionames-manuscript/master/model-annotated.png)

Fig. MODEL. Simplified diagram of the relationships between the core entities that make up taxonomy, such as authors, publications, taxon names, and taxa. Relationships between entities are represented by lines, those in black are the focus of BioNames.


## EOL Challenge
In response to the Encyclopedia of Life (EOL) [Computational Data Challenge](http://eol.org/info/323) I constructed [BioNames](http://bionames.org) [Page 2012]. Its goal is to create a database of taxonomic names linked to the primary literature and, wherever possible, to phylogenetic trees. Using existing globally unique identifiers for taxonomic names, concepts, publications, and sequences rather than cryptic text strings (for example, abbreviated bibliographic citations) simplifies the task of linking — we can rely on exact matching of identifiers rather than approximate matching between names for what may or may not be the same entity. This is particularly relevant once we start to aggregate information from different databases, where the same information (e.g., a publication) may be represented by different strings. Furthermore, if we use existing identifiers we increase the potential to connect to other databases [Page 2008a].

This paper outlines how BioNames was built, describes the user interface, and discusses future plans. 

# Materials & Methods

## Data reconciliation

BioNames integrates data on taxonomic names and classifications, literature, and phylogenies from a variety of sources. Given the inevitable differences in how different databases treat the same data (as well as internal inconsistencies within individual databases), considerable effort must be spent cleaning and reconciling data. Much of this process involves mapping "strings" to "things" [Bollacker et al. 2008], or more precisely, mapping strings to identifiers for things.

Figure 1 shows the relationships that are the focus of BioNames, namely the link between a taxonomic name and its publication...


## Taxon names

At present the taxonomic scope of BioNames is restricted to names covered by the International Code of Zoological Nomenclature. Taxonomic names were obtained from the [Index of Organism Names (ION)](http://www.organismnames.com). Each name in ION has a Life Science Identifier (LSID) [Martin et al. 2005] which uniquely identifies that name. LSIDs can be dereferenced to return metadata in RDF [Page 2008b], ION LSIDs provide basic information on a taxonomic name using the [TDWG Taxon Name LSID Ontology](http://rs.tdwg.org/ontology/voc/TaxonName), in many cases including bibliographic details for the publication where the name first appeared (Fig. RDF). 

![RDF](https://raw.github.com/rdmpage/bionames-manuscript/master/rdf.png)

Fig. RDF. The RDF retrieved by dereferencing the LSID urn:lsid:organismnames.com:name:371873, which identifies the taxonomic name *Pinnotheres atrinicola*.

The bibliographic details are encapsulated in the contents of the "PublishedIn" property. In the example in Fig. RDF this is the string "Description of a new species of Pinnotheres, and redescription of P. novaezelandiae (Brachyura: Pinnotheridae). New Zealand Journal of Zoology, 10(2) 1983: 151-162.  158 [Zoological Record Volume 120]". I used regular expressions to parse citation strings into their component parts (e.g., article title, journal, volume, pagination), and then attempted to locate the corresponding reference in an external database (see below).


## Bibliographic identifiers

When populating BioNames every effort has been made to map a bibliographic string to a corresponding identifier, such as a Digital Object identifier (DOI).  While DOIs are the best-known bibliographic identifier, there are several others that are relevant to the taxonomic literature [Page 2009]. DOIs are themselves based on Handles (http://hdl.handle.net), an identifier widely used by digital repositories such as DSpace[Smith et al. 2003]. A number of journals, such as the *Bulletins* and *Novitates* of the American Museum of Natural History are available in DSpace repositories and consequently have Handles. Other major archives such as [JSTOR](http://www.jstor.org/) and [CiNii](http://ci.nii.ac.jp/) have their own unique identifiers (typically integer numbers that are part of a URL). Having a variety of identifiers can complicate the task of finding existing identifiers for a particular publication. Whereas for some identifiers, such as DOIs and CiNii NAIDs (National Institute of Informatics Article IDs) there are OpenURL resolvers for this task [Van de Sompel and Beit-Arie 2001], for other identifiers there may be no obvious way to find the identifier other than by using a search engine.

For the example in Fig. RDF, the citation string "Description of a new species of Pinnotheres, and redescription of P. novaezelandiae (Brachyura: Pinnotheridae). New Zealand Journal of Zoology, 10(2) 1983: 151-162.  158 [Zoological Record Volume 120]" corresponds to the article with the DOI 10.1080/03014223.1983.10423904. Once we have a DOI, we can then use services such as those provided by [CrossRef](http://www.crossref.org) to retrieve author and publisher information for an article (see Fig. PUB below for one use of publisher information).

Identifiers also exist for aggregations of publications, such as journals. The historical practice of abbreviating journal titles in citations has led to a plethora of ways to refer to the same journal. For example, the BioStor database [Page 2011b] has accumulated more than ten variations on the name of the journal *Bulletin of Zoological Nomenclature* (such as "Bull Zool Nomen", "Bull Zool Nom.", "Bull. Zool. Nomencl.", etc.). This practice, presumably motivated by the desire to conserve space on the printed page, complicates efforts to match citations to identifiers. One approach to tackling this problem is to map abbreviations to journal-level globally unique identifiers, such as International Standard Serial Numbers  (ISSNs) (for the *Bulletin of Zoological Nomenclature* the ISSN is 0007-5167). In addition to reducing ambiguity, there are web services such as that provided by [WorldCat](http://www.worldcat.org) that take ISSNs and return the history of name changes for a journal, which in turn can help clarify the often complicated history of long-lived journals.

## Documents

Taxonomic publications are available under a variety of licenses, ranging from explicitly open access licenses [MacCallum 2007] to articles that are "free", to articles that are behind a paywall. Archives such as JSTOR and CiNii have a mixture of free and subscription-based content. Many smaller journals, often published by scientific societies, are providing their content online for free, if not explicitly under an open license. The Biodiversity Heritage Library (the single largest source of taxonomic articles in BioNames) makes its content available under a Creative Commons license. Where PDFs were available either "for free" or under open access, these were downloaded and locally cached. Pages were extracted and converted into bitmap images for subsequent display in a web browser.

Closed-access publications that are available online are linked to by their identifier (e.g., DOI). Access to some of these publications may be available for short-term "rent" by services such as [DeepDyve](http://www.deepdyve.com): where possible BioNames includes a link those services.

## Clustering taxonomic names

Taxonomic names may comprise a "canonical" name and the name's authorship, for example  *Homo sapiens* Linnaeus comprises the canonical name "Homo sapiens" and the authorship string "Linnaeus". Names in taxonomic databases such as ION display numerous variations in spelling of authors, and multiple instances of the same name (e.g., homonyms), so they were clustered before populating BioNames. For each set of taxon names with the same canonical name the authorship was compared. If one name lacked an author and the other had an author, the names were automatically merged into a cluster. Given more than two names a graph was constructed where the nodes were the authorship strings, and a pair of nodes were connected if their corresponding strings were sufficiently similar. String similarity was computed by converting the strings to a "finger print" comprising lower case letters with all accented characters replaced by non-accented equivalents, and all punctuation removed, then finding the longest common subsequence  of the two strings. If the length of the subsequence relative to the input strings was longer than a specified threshold (by default, 0.8, where identical strings have a similarity of 1.0) then the two author strings were connected by an edge. The components of the graph correspond to clusters of names with similar authorship strings, and were treated as being the same name. Fig. CLUSTER shows a graph for the different names that all have "Rhacophorus" as the canonical name. 

![CLUSTER](https://raw.github.com/rdmpage/bionames-manuscript/master/Rhacophorus.png)

Fig. CLUSTER. Graph depicting similarity between different authorship strings associated with the name "Rhacophorus". The components of this graph correspond to the name clusters recognised by BioNames. 


## Mapping names to taxa

BioNames includes two taxonomic classifications, sourced from GBIF http://uat.gbif.org/dataset/d7dddbf4-2cf0-4f39-9b2a-bb099caae36c and NCBI ftp://ftp.ncbi.nih.gov/pub/taxonomy, respectively. These provide the user with a way to navigate through taxonomic names, as well as view data associated with each classification (for example, phylogenies).

Matching taxon names to classifications can present problems. Ideally there would be a one-to-one mapping between a name and a taxon, but complications often arise. In addition to the well-known problems of synonymy (more than one name for the same taxon) and homonymy (the same name used for different taxa), name and taxon databases may store slightly different representations of the same name. For example, ION has four records for the name "Nystactes" (each name is followed by its LSID):

- Nystactes				      urn:lsid:organismnames.com:name:2787598
- Nystactes Bohlke		  urn:lsid:organismnames.com:name:2735131
- Nystactes Gloger 1827	urn:lsid:organismnames.com:name:4888093
- Nystactes Kaup 1829	  urn:lsid:organismnames.com:name:4888094

GBIF has three taxa with this name (the number is the GBIF species id):

- Nystactes Böhlke, 1957	 2403398
- Nystactes Gloger, 1827	 2475109
- Nystactes Kaup, 1829	   3239722

Note the differences in the name string ("o" versus "ö" in "Böhlke", presence or absence of years and commas). To automate the mapping of names to concepts in cases like this I constructed a bipartite graph where the nodes are taxon names, divided into two sets based upon which database they came from (e.g., one set of names from ION, the other from GBIF). I then connect the nodes of the graph by edges whose weights are the similarity of the two strings computed using the longest common subsequence that the two strings share. For example, [Fig. BIPART] shows the graph for "Nystactes". Computing the maximum weighted bipartite matching of this graph creates a map between the two sets of names.

![BIPART](https://raw.github.com/rdmpage/bionames-manuscript/master/Nystactes.png)

Fig. BIPART. Bipartite graph of string similarities between taxonomic names containing the string "Nystactes" in the ION and GBIF databases. Solid edges in the graph represent the maximum weighted bipartite matching, and define the mapping between ION and GBIF names.

Ideally GBIF should have only one entry for *Nystactes* as each animal name (with a few exceptions) must be unique. If a newer name has already been published before, then it should be replaced by a new name. In this case, *Nystactes* [Böhlke 1957] has since been replaced by *Nystactichthys* [Böhlke 1958], and *Nystactes* [Kaup 1829] by *Paramyotis* [Bianchi 1916]. Unfortunately these changes have not yet percolated their way from the primary literature into the GBIF taxonomy.

## Images

To help the user recognise the taxa being displayed images for as many taxa as possible were obtained using EOL's API, which provides access to both the images, and a mapping between GBIF and NCBI taxon concept identifiers and the corresponding record in EOL.


## Phylogenies

Phylogenies were obtained from the [PhyLoTA database](http://phylota.net) [Sanderson et al. 2008]. This database contains eukaryote phylogenies constructed from automatically assembled clusters of nucleotide sequences (loosely corresponding to "genes"). A MySQL data dump was downloaded from http://phylota.net (version 184, corresponding to the GenBank release of the same version number) and used to populate a local MySQL database. Metadata for the sequences in each phylogeny was obtained from the European Bioinformatics Institute (EBI), and used to populate the MySQL database with basic information such as taxon and locality information, as well as bibliographic details for the sources of the sequences.

## Database

Once aggregated, cleaned, and reconciled, the data was converted to JSON (JavaScript Object Notation) and stored in a CouchDB database. CouchDB is a "NoSQL" document database which stores objects in JSON format [Anderson et al. 2010]. Unlike typical SQL databases, CouchDB does not need a database schema and does not support ad hoc queres. Instead CouchDB accepts semi-structured documents, and the user defines fixed queries or "views".

# Results

BioNames comprises a CouchDB database and a web interface. Key features of the interface are outlined below.

## Search

BioNames features a simple search interface that takes a scientific name and returns matching taxonomic names and concepts, together with any publications and phylogenies that contain the name. Fig. SEARCH shows an example search result.

![SEARCH](https://raw.github.com/rdmpage/bionames-manuscript/master/search.png)

Fig. SEARCH. Screenshot of the search results for a query BioNames. The results include names that match the query, taxon concepts from GBIF and NCBI with thumbnail images from EOL, phylogenies containing members of the genus, and relevant taxonomic publications. 

## Document display

BioNames uses the [DocumentCloud](https://github.com/documentcloud/document-viewer) viewer to display both PDFs, and page images from digital archives such as BioStor and [Gallica](http://gallica.bnf.fr/) (Fig. DOC).

![DOC](https://raw.github.com/rdmpage/bionames-manuscript/master/document.png)

Fig. DOC. Screenshot of BioNames displaying a document from BioStor [Conle and Hennemann 2002]. The document viewer can display page images, thumbnails, and (where available) text. http://bionames.org/references/3e93d39afe5c3642e8aecfcd0cea6f92

## Journals

Much of the work in populating BioNames comprises mapping citation to string to bibliographic identifiers and, where possible, linking those citations to full text. For each journal that has a ISSN, BioNames has a corresponding web page that lists all the articles from that journal that are in the database, and provides a graphical summary of how many of those articles have been located online (Fig. ISSN).

![ISSN](https://raw.github.com/rdmpage/bionames-manuscript/master/pesw.png)

Fig. ISSN. Screenshot of the page in BioNames for the journal *Proceedings of the Entomological Society of Washington* (ISSN 0013-8797). The centre column lists the articles in a volume selected by the user using the index on the left. The right hand column displays basic data about the journal, and a graphical display of how many articles have been mapped to a globally unique identifier. [http://bionames.org/issn/0013-8797]

## Timeline

BioNames can display timelines of the numbers of taxonomic names published in higher taxonomic groups, inspired by Taxatoy [Sarkar et al. 2008] (Fig. TIMELINE). For a given node in the taxonomic hierarchy the children of that node are displayed as a treemap where the size of each cell is proportional to the log of the number of taxa in the subtree rooted on that child taxon. The number of names in that taxon published in each year is displayed as an interactive chart. Clicking on an individual year will list the corresponding publications for that year. 

![TIMELINE](https://raw.github.com/rdmpage/bionames-manuscript/master/timeline.png)

Fig. TIMELINE. Screenshot of the distribution overtime of publications of new names for birds (Aves). The treemap on the left displays taxa below Aves in the taxonomic hierarchy, the chart on the right displays the number of publications in each year that publish a new bird name. The user has clicked on "2012", resulting in a list of the papers published in that year appearing below the timeline (only two are shown). http://bionames.org/timeline/Animalia/Chordata/Vertebrata/Aves

## Taxa

Each GBIF or NCBI taxon in BioNames has a corresponding web page that lists the associated taxonomic names, publications inked to those names, and other relevant data (e.g., Fig. TAXA).

![TAXA](https://raw.github.com/rdmpage/bionames-manuscript/master/rousettus.png)

Fig. TAXA. Screenshot of the bibliography tab on a taxon page in BioNames. This example shows the publications relevant to the bat genus *Rousettus*, including those for synonyms. The user can select publications from a given time slice and/or set of synonyms. 


## Phylogenies

Phylogenies from PhyLOTA are rendered in an interactive viewer using the Scalable Vector Graphics (SVG) format. The user can zoom in and out, and change the drawing style. Terminal taxa with the same label have the same colour (Fig. TREE). This makes it easier to recognise clusters of sequences from the same taxon (e.g., conspecific samples), as well as highlight possible errors (e.g., mislabelled or misidentified sequences). At present the colours are arbitrarily chosen, other schemes could be added in future [Lespinats and Fertil 2011]. 

![TREE](https://raw.github.com/rdmpage/bionames-manuscript/master/phylota_ti10167_cl0_db184.png)

Fig. TREE. Screenshot of phylogeny from PhyLoTA as displayed in BioNames. The user can zoom in and out and pan, as well as change the layout of the tree. http://bionames.org/trees/phylota/ti10167_cl0_db184

## Dashboard

The BioNames web site features a "dashboard" which displays various summaries of the data it contains. For example, Fig. PUB shows a bubble chart of the number of articles different publishers have made available online. "Publisher" in this context is broadly defined to include digital archives such as BioStor and JSTOR, repositories using [DSpace](http://www.dspace.org), and commercial publishers such as Elsevier, Informa UK, Magnolia Press, Springer, and Wiley.

![PUB](https://raw.github.com/rdmpage/bionames-manuscript/master/publishers.png)

Fig. PUB. Bubble chart showing relative numbers of taxonomic articles made available online by different publishers.

# Discussion

The EOL Computational Data Challenge imposed a deadline on the first release of BioNames, however development of both the database and web interface is ongoing. Below I discuss some potential applications and future directions.

## Links

BioNames makes extensive use of identifiers to clean and link data, but the real value of identifiers becomes apparent when they are shared, that is, when different databases use the same identifiers for the same entities, instead of minting their own. Reusing identifiers can enable unexpected connections between databases. For example, the PubMed biomedical literature database has a record (PMID:948206) for the paper "Monograph on "*Lithoglyphopsis*" *aperta*, the snail host of Mekong River Schistosomiasis" [Davis et al. 1976]. The PubMed record contains the abstract for the paper, but not a link to where the user can obtain a digital version of the paper. However, this reference is in a volume that has been scanned by the Biodiversity Heritage Library (BHL), and the article has been extracted by BioStor (http://biostor.org/reference/102054). If PubMed was linked to BHL, users of PubMed could go straight to the content of the article. But this is just the start. The [Davis et al. 1976] also paper mentions museum specimens in the collection of the Academy of Natural Sciences of Drexel University, Philadelphia. Metadata for these specimens has been aggregated by GBIF, and the BioStor page for this article displays those links. In an ideal world we should be able seamlessly to traverse the path PubMed → BioStor → GBIF. Likewise, we should be able to traverse the path in the other direction. At present, a user of GBIF simply sees metadata for these specimens and a locality map. They are unaware that these specimens have been cited in a paper [Davis et al. 1976] which demonstrates that the snails host the Mekong River schistosome. This connection would be trivial to make if the reciprocal link was made:  GBIF → BioStor. Furthermore, a link BioStor → PubMed would give us access to Medical Subject Headings (MeSH) for the schistosome paper. Hence we could imagine ultimately searching a database of museum specimens (GBIF) using queries from a controlled vocabulary of biomedical terms (MeSH). 

Making these connections requires not only that we have digital identifiers, but also that where ever possible we reuse existing identifiers. In practice forging these links can be hard work [Page 2011a], and many links may be missing from existing databases [Miller et al. 2009]. However, if we restrict ourselves to project-specific identifiers then we stymie attempts to create a network of connected biodiversity data. 

## Text mining

Much of the value of a scientific publication lies dormant unless it is accessible to text mining, which requires access to full text. Where possible BioNames stores information on the publisher of each article (Fig. PUB), which could then be used to prioritise discussions with publishers on gaining access to full text [Van Noorden 2012]. Fortunately, the single largest "publisher" of content in BioNames is BioStor [Page 2011b], which contains scans and OCR text from the Biodiversity Heritage Library. BHL makes its content available under a Creative Commons license, and so can be readily mined. Indeed, the text has already been indexed by tools that can recognise taxonomic names [Akella et al. 2012]. There is considerable scope for further text mining, for example by looking for co-occurrences between taxonomic names that might indicate taxonomic (e.g., synonyms) or ecological relationships (e.g., hosts and parasites).


## Impact of taxonomic literature

The taxonomic community has long felt disadvantaged by the role of citation-based "impact factor" in assessing the importance of taxonomic research [Garfield 2001] [Krell 2000] [Werner 2006] especially as much of the taxonomic literature appears in relatively low-impact journals. A common proposal is to include citations to the taxonomic authority for every name mentioned in a scientific paper [Wägele et al. 2011]. Regardless of the merits of this idea, there is value in surfacing identifiers for the taxonomic literature. In addition to citations, identifiers can facilitate computing other measures of the value of a taxonomic paper.  There is a growing interest in additional measures of post-publication impact of a publication in terms of activity such as social bookmarking, and commentary on web sites ("alt-metrics") [Yan and Gerstein 2011]. Gathering these metrics is greatly facilitated by using standard bibliographic identifiers (otherwise, how do we know whether two commentators are discussing the same article or not?). If taxonomic literature is be part of this burgeoning conversation then it needs to be able to be identified unambiguously.


## Dark taxa

One of the original motivations for constructing BioNames is the rise of "dark taxa" in genomics databases [Page 2011c]. It is clear that some dark taxa do, in fact, have names. For example, consider the frog "*Gephyromantis* aff. *blanci* MV-2005" (NCBI tax_id 321743), which has a single DNA sequence AY848308 associated with it. This sequence was published as part of a DNA barcoding study [Vences et al. 2005]. If we enter the accession number AY848308 into Google we find two documents, one the supplementary table for [Vences et al. 2005], the other the a subsequent paper by [Vences and Riva 2007] that describes the frog with this sequence as a new species, *Gephyromantis runewsweeki*. Hence the taxon originally labelled "*Gephyromantis* aff. *blanci* MV-2005" is actually *Gephyromantis runewsweeki*. This example is relatively straightforward, but it still required significant time to track down the species description. A key question facing attempts to find names for dark taxa is whether the methods available can be scaled to handle the magnitude of the problem. 

Alternatively, one could argue that newer technologies such as DNA barcoding make classical taxonomy less relevant, and perhaps the effort in digitising older literature and exposing the taxonomic names it contains is misplaced. A counter argument would be that the taxonomic literature potentially contains a wealth of information on ecology, morphology and behaviour, often for taxa in areas that have been subsequently altered by human activity. Given the rarity of many taxa [Lim et al. 2011], and the uneven taxonomic and geographic distribution of taxonomic expertise [May 1998][Gaston and May 1992], for many species the only significant data on their biology may reside in the legacy literature (possibly under a different name [Solow et al. 1995]). As this legacy becomes more accessible through projects such as BHL (and services that build upon that project [Page 2011a]) there will be considerable opportunities to mine that literature for basic biological data [Thessen et al. 2012].


## Publishing platform

Recently some taxonomic journals have begun to mark up taxonomic names and descriptions [Penev et al. 2010], which is a precursor to linking names and data together. But these developments leave open the problem of what these links will point to. If we have a database of all taxonomic names and the associated literature (such as BioNames aims to be for zoological names), then such a database would provide an obvious destination for those links. Indeed, ultimately, we could envisage embedding new taxonomic publications within such a database, so that each new publication becomes simply another document within the database [Gerstein and Junker 2002]. In the same way, we could use automated methods to extend the process of tagging names, specimens and literature cited to the legacy literature [Page 2010], so that the entire body of taxonomic knowledge becomes a single interwoven web of names, citations, publications, and data.

# Availability

BioNames is accessible at http://bionames.org. The source code used to build the web site is available on GitHub http://github.com/rdmpage/bionames. Scripts used to fetch, clean, and reconcile the data are archived in http://github.com/rdmpage/bionames-data

# Acknowledgements

I thank EOL for the funding that enabled Ryan Schenk to develop the interface for BioNames, and Cyndy Parr (EOL) for managing the EOL Computational Challenge grant and providing helpful feedback on the development of BioNames. Some of the ideas in this manuscript were first explored in a talk at the "Anchoring Biodiversity Information: From Sherborn to the 21st century and beyond" symposium held at The Natural History Museum, London, October 28th 2011. I thank Ellinor Michel for the invitation to speak at that meeting.

# References

- Akella, L., Norton, C. N., & Miller, H. (2012). NetiNeti: discovery of scientific names from text using machine learning methods. BMC Bioinformatics, 13(1), 211. [doi:10.1186/1471-2105-13-211][Akella et al. 2012]

- Anderson, J. Chris, Jan Lehnardt and Noah Slater (2010). CouchDB: The Definitive Guide. O'Reilly, ISBN: 978-0-596-15589-6 [Anderson et al. 2010]

- Baird, R. (2010). Leveraging the fullest potential of scientific collections through digitisation.Biodiversity Informatics, 7(2). [https://journals.ku.edu/index.php/jbi/article/view/3987][Baird 2010]

- Benson, Dennis A., Ilene Karsch-Mizrachi, Karen Clark, David J. Lipman, James Ostell, and Eric W. Sayers
GenBank. Nucl. Acids Res. (2012) 40 (D1): D48-D53. [doi:10.1093/nar/gkr1202][Benson et al. 2012]

- Bianchi 1916. Annuaire du Musee Zoologique de l'Academie d. Sciences de St. Petersbourg 21:xxiii-xxxii (not seen)[Bianchi 1916]

- Blagoderov, V., Kitching, I., Livermore, L., Simonsen, T., & Smith, V. (2012). No specimen left behind: industrial scale digitization of natural history collections. ZooKeys, 209(0), 133–146. [doi:10.3897/zookeys.209.3178][Blagoderov et al. 2012]

- Bollacker, K., Evans, C., Paritosh, P., Sturge, T., & Taylor, J. (2008). Freebase. Proceedings of the 2008 ACM SIGMOD international conference on Management of data - SIGMOD ’08 (p. 1247). Association for Computing Machinery. [doi:10.1145/1376616.1376746][Bollacker et al. 2008]

- Böhlke, J. E. (1957). On the Occurrence of Garden Eels in the Western Atlantic, with a Synopsis of the Heterocongrinae. Proceedings of the Academy of Natural Sciences of Philadelphia, 109: 59-79. [http://www.jstor.org/stable/4064494][Böhlke 1957]

- Böhlke, J. E. (1958). Substitute Names for *Nystactes* Bohlke and *Lucaya* Bohlke, Preoccupied. Copeia, 1958(1), 59. [doi:10.2307/1439557][Böhlke 1958]

- Conle, Oskar V, and Frank H Hennemann (2002) Revision of neotropic Phasmatodea: The tribe Anisomorphini sensu Bradley & Galil 1977: (Insecta, Phasmatodea, Pseudophasmatidae). Spixiana Supplement 28: 1–141. [http://biostor.org/reference/118220][Conle and Hennemann 2002]

- Davis GM, Kitikoon V, Temcharoen P (1976) Monograph on "*Lithoglyphopsis*" *aperta*, the snail host of Mekong River schistosomiasis. Malacologia 15(2): 241-87. [http://biostor.org/reference/102054][Davis et al. 1976]

- Deans, A. R., Yoder, M. J., & Balhoff, J. P. (2012). Time to change how we describe biodiversity. Trends in Ecology & Evolution, 27(2), 78–84. [doi:10.1016/j.tree.2011.11.007][Deans et al. 2012]

- Edwards, J. L. (2000). Interoperability of Biodiversity Databases: Biodiversity Information on Every Desktop. Science, 289(5488), 2312–2314. [doi:10.1126/science.289.5488.2312][Edwards 2000]

- Faulkes, C. G., Bennett, N. C., Cotterill, F. P. D., Stanley, W., Mgode, G. F., & Verheyen, E. (2011). Phylogeography and cryptic diversity of the solitary-dwelling silvery mole-rat, genus *Heliophobius* (family: Bathyergidae). (A. Kitchener, Ed.)Journal of Zoology, 285(4), 324–338. [doi:10.1111/j.1469-7998.2011.00863.x][Faulkes et al. 2011]

- Franz, N. M., & Cardona-Duque, J. (2013). Description of two new species and phylogenetic reassessment of *Perelleschus* O’Brien & Wibmer, 1986 (Coleoptera: Curculionidae), with a complete taxonomic concept history of *Perelleschus* sec. Franz & Cardona-Duque, 2013 . Systematics and Biodiversity, 11(2), 209–236. [doi:10.1080/14772000.2013.806371][Franz and Cardona-Duque 2013]

- Garfield, E. (2001).Nature, 413(6852), 107–107. [doi:10.1038/35093267][Garfield 2001]

- Gaston, K. J., & May, R. M. (1992). Taxonomy of taxonomists. Nature, 356(6367), 281–282. [doi:10.1038/356281a0][Gaston and May 1992]

- Gerstein, M. and Jochen Junker (2002). Blurring the boundaries between scientific 'papers' and biological databases. Nature [http://www.nature.com/nature/debates/e-access/Articles/gernstein.html][Gertsien and Junker 2002]

- Hebert, P. D. N., Cywinska, A., Ball, S. L., & deWaard, J. R. (2003). Biological identifications through DNA barcodes. Proceedings of the Royal Society B: Biological Sciences, 270(1512), 313–321. [doi:10.1098/rspb.2002.2218][Hebert 2003]

- Hibbett, D., & Glotzer, D. (2011). Where are all the undocumented fungal species? A study of *Mortierella* demonstrates the need for sequence-based classification. New Phytologist, 191(3), 592–596. [doi:10.1111/j.1469-8137.2011.03819.x][Hibbett and Glotzer 2011]

- Kaup, J. J., & Stejneger, L. (1829). Skizzirte Entwickelungs-Geschichte und natürliches System der europäischen Thierwelt : Erster Theil welcher die Vogelsäugethiere und Vögel nebst Andeutung der Entstehung der letzteren aus Amphibien enthält /. Smithsonian Institution Biodiversity Heritage Library. [doi:10.5962/bhl.title.63915][Kaup 1829]

- Kennedy, J. B., Kukla, R., & Paterson, T. (2005). Scientific Names Are Ambiguous as Identifiers for Biological Taxa: Their Context and Definition Are Required for Accurate Data Integration (pp. 80–95). Springer-Verlag. [doi:10.1007/11530084_8][Kennedy et al. 2005]

- Krell, F.-T. (2000).Nature, 405(6786), 507–508. [doi:10.1038/35014664][Krell 2000]

- Lespinats, Sylvain, & Bernard Fertil. (2011). ColorPhylo: A Color Code to Accurately Display Taxonomic Classifications. Evolutionary Bioinformatics, 257. [doi:10.4137/EBO.S7565][Lespinats and Fertil 2011]

- Lim, G. S., Balke, M., & Meier, R. (2011). Determining Species Boundaries in a World Full of Rarity: Singletons, Species Delimitation Methods. Systematic Biology, 61(1), 165–169. [doi:10.1093/sysbio/syr030][Lim et al. 2011]

- MacCallum, C. J. (2007). When Is Open Access Not Open Access? PLoS Biology, 5(10), e285. [doi:10.1371/journal.pbio.0050285][MacCallum 2007]

- Maddison, D. R., Guralnick, R., Hill, A., Reysenbach, A.-L., & McDade, L. A. (2012). Ramping up biodiversity discovery via online quantum contributions. Trends in Ecology & Evolution, 27(2), 72–77. [doi:10.1016/j.tree.2011.10.010][Maddison et al. 2012]

- Martin, S., Hohman, M. M., & Liefeld, T. (2005). The impact of Life Science Identifier on informatics data. Drug Discovery Today, 10(22), 1566–1572. [doi:10.1016/S1359-6446(05)03651-2][Martin et al. 2005]

- MAY, R. M. (1988). How Many Species Are There on Earth? Science, 241(4872), 1441–1449. [doi:10.1126/science.241.4872.1441][May 1988]

- Miller, H., Norton, C. N., & Sarkar, I. N. (2009). GenBank and PubMed: How connected are they? BMC Research Notes, 2(1), 101. [doi:10.1186/1756-0500-2-101][Miller et al. 2009]

- Müller-Wille, S., & Charmantier, I. (2012). Natural history and information overload: The case of Linnaeus. Studies in History and Philosophy of Science Part C: Studies in History and Philosophy of Biological and Biomedical Sciences, 43(1), 4–15. [doi:10.1016/j.shpsc.2011.10.021][Müller-Wille and Charmantier 2012]

- Nagy, L. G., Petkovits, T., Kovács, G. M., Voigt, K., Vágvölgyi, C., & Papp, T. (2011). Where is the unseen fungal diversity hidden? A study of *Mortierella* reveals a large contribution of reference collections to the identification of fungal environmental sequences. New Phytologist, 191(3), 789–794. [doi:10.1111/j.1469-8137.2011.03707.x][Nagy et al. 2011]

- Page, R. D. M. (1983). Description of a new species of Pinnotheres , and redescription of P. novaezelandiae (Brachyura: Pinnotheridae) . New Zealand Journal of Zoology, 10(2), 151–162. [doi:10.1080/03014223.1983.10423904][Page 1983]

- Page, R. D. M. (2008a). Biodiversity informatics: the challenge of linking data and the role of shared identifiers. Briefings in Bioinformatics, 9(5), 345–354. [doi:10.1093/bib/bbn022][Page 2008a]

- Page, R. D. (2008b). LSID Tester, a tool for testing Life Science Identifier resolution services. Source Code for Biology and Medicine, 3(1), 2. [doi:10.1186/1751-0473-3-2][Page 2008b]

- Page, R. D. (2009). bioGUID: resolving, discovering, and minting identifiers for biodiversity informatics. BMC Bioinformatics, 10(Suppl 14), S5. [doi:10.1186/1471-2105-10-S14-S5][Page 2009]

- Page, R. D. M. (2010). Enhanced display of scientific articles using extended metadata. Web Semantics: Science, Services and Agents on the World Wide Web, 8(2-3), 190–195. [doi:10.1016/j.websem.2010.03.004][Page 2010]

- Page, R. D. M. (2011a). Linking NCBI to Wikipedia: a wiki-based approach. PLoS Currents, 3, RRN1228. [doi:10.1371/currents.RRN1228][Page 2011a]

- Page, R. D. (2011b). Extracting scientific articles from a large digital archive: BioStor and the Biodiversity Heritage Library. BMC Bioinformatics, 12(1), 187. [doi:10.1186/1471-2105-12-187][Page 2011b]

- Page, R. D. M. (2011c). Dark taxa: GenBank in a post-taxonomic world. [http://iphylo.blogspot.co.uk/2011/04/dark-taxa-genbank-in-post-taxonomic.html][Page 2011c]

- Page, R. D. M. 2012. EOL Computable Data Challenge. [doi 10.6084/m9.figshare.92091][Page 2012]

- Parr, C. S., Guralnick, R., Cellinese, N., & Page, R. D. M. (2012). Evolutionary informatics: unifying knowledge about the diversity of life. Trends in Ecology & Evolution, 27(2), 94–103. [doi:10.1016/j.tree.2011.11.001][Parr et al. 2012]

- Patterson, D. J., Cooper, J., Kirk, P. M., Pyle, R. L., & Remsen, D. P. (2010). Names are key to the big new biology. Trends in Ecology & Evolution, 25(12), 686–691. [doi:10.1016/j.tree.2010.09.004][Patterson et al. 2010]

- Penev, L., Agosti, D., Georgiev, T., Catapano, T., Miller, J., Blagoderov, V., Roberts, D., et al. (2010). Semantic tagging of and semantic enhancements to systematics papers: ZooKeys working examples. ZooKeys, 50(0). [doi:10.3897/zookeys.50.538][Penev et al. 2010]

- Peters WCH (1846) Über neue Säugethiergattungen aus den Ordnungen der Insectenfresser und Nagethiere. Bericht über die zur Bekanntmachung geeigneten Verhandlungen der Konigl.Preuss.Akademie der Wissenschaften zu Berlin 1846: 257-259.[http://biostor.org/reference/102396][Peters 1846]

- Sanderson, M., Boss, D., Chen, D., Cranston, K., & Wehe, A. (2008). The PhyLoTA Browser: Processing GenBank for Molecular Phylogenetics Research. Systematic Biology, 57(3), 335–346. [doi:10.1080/10635150802158688][Sanderson et al. 2008]

- Sarkar, I. N. (2007). Biodiversity informatics: organizing and linking information across the spectrum of life. Briefings in Bioinformatics, 8(5), 347–357. [doi:10.1093/bib/bbm037][Sarkar 2007]

- Sarkar, I., Schenk, R., & Norton, C. N. (2008). Exploring historical trends using taxonomic name metadata. BMC Evolutionary Biology, 8(1), 144. [doi:10.1186/1471-2148-8-144][Sarkar et al. 2008]

- Schindel DE, Miller SE (2010) Provisional nomenclature: the on-ramp to taxonomic names. In: Polaszek A (Ed) Systema Naturae 250 - The Linnaean Ark. CRC Press, 109-115 pp.

- Smith, M., Barton, M., Branschofsky, M., McClellan, G., Walker, J. H., Bass, M., Stuve, D., et al. (2003). DSpace. D-Lib Magazine, 9(1). [doi:10.1045/january2003-smith][Smith et al. 2003]

- Solow, A. R., Mound, L. A., & Gaston, K. J. (1995). Estimating the Rate of Synonymy. Systematic Biology, 44(1), 93–96. [doi:10.1093/sysbio/44.1.93][Solow et al. 1995]

- TABERLET, P., COISSAC, E., POMPANON, F., BROCHMANN, C., & WILLERSLEV, E. (2012). Towards next-generation biodiversity assessment using DNA metabarcoding. Molecular Ecology, 21(8), 2045–2050. [doi:10.1111/j.1365-294X.2012.05470.x][Taberlet et al. 2012]

- Thessen, A. E., Cui, H., & Mozzherin, D. (2012). Applications of Natural Language Processing in Biodiversity Science. Advances in Bioinformatics, 2012, 1–17. [doi:10.1155/2012/391574][Thessen et al. 2012]

- Van de Sompel, H., & Beit-Arie, O. (2001). Open Linking in the Scholarly Information Environment Using the OpenURL Framework. D-Lib Magazine, 7(3). [doi:10.1045/march2001-vandesompel][Van de Sompel and Beit-Arie 2001]

- Van Noorden, R. (2012). Trouble at the text mine. Nature, 483(7388), 134–135. [doi:10.1038/483134a][Van Noorden 2012]

- Vences M, Riva IDL (2007) A new species of *Gephyromantis* from Ranomafana National Park, south-eastern Madagascar (Amphibia, Anura, Mantellidae). Spixiana 30(1): 135-143.

- Vences, M., Thomas, M., van der Meijden, A., Chiari, Y., & Vieites, D. R. (2005).Frontiers in Zoology, 2(1), 5. [doi:10.1186/1742-9994-2-5][Vences et al. 2005]

- Wägele, H., Klussmann-Kolb, A., Kuhlmann, M., Haszprunar, G., Lindberg, D., Koch, A., & Wägele, J. W. (2011). The taxonomist - an endangered race. A practical proposal for its survival. Frontiers in Zoology, 8(1), 25. [doi:10.1186/1742-9994-8-25][Wägele et al. 2011]

- Werner, Y. L. (2006). The case of impact factor versus taxonomy: a proposal. Journal of Natural History, 40(21-22), 1285–1286. [doi:10.1080/00222930600903660][Werner 2006]

- Yan, K.-K., & Gerstein, M. (2011). The Spread of Scientific Information: Insights from the Web Usage Statistics in PLoS Article-Level Metrics. (A. Vespignani, Ed.)PLoS ONE, 6(5), e19917. [doi:10.1371/journal.pone.0019917][Yan and Gerstein 2011]

[Akella et al. 2012]: http://dx.doi.org/10.1186/1471-2105-13-211
[Baird 2010]: https://journals.ku.edu/index.php/jbi/article/view/3987
[Benson et al. 2012]: http://dx.doi.org/10.1093/nar/gkr1202
[Blagoderov et al. 2012]: http://dx.doi.org/10.3897/zookeys.209.3178
[Bollacker et al. 2008]: http://dx.doi.org/10.1145/1376616.1376746
[Böhlke 1957]: http://www.jstor.org/stable/4064494
[Böhlke 1958]: http://dx.doi.org/10.2307/1439557
[Conle and Hennemann 2002]: http://biostor.org/reference/118220
[Deans et al. 2012]: http://dx.doi.org/10.1016/j.tree.2011.11.007
[Davis et al. 1976]: http://biostor.org/reference/102054
[Edwards 2000]: http://dx.doi.org/10.1126/science.289.5488.2312
[Faulkes et al. 2011]: http://dx.doi.org/10.1111/j.1469-7998.2011.00863.x
[Franz and Cardona-Duque 2013]: http://dx.doi.org/10.1080/14772000.2013.806371
[Garfield 2001]: http://dx.doi.org/10.1038/35093267
[Gaston and May 1992]: http://dx.doi.org/10.1038/356281a0
[Gerstein and Junker 2002]: http://www.nature.com/nature/debates/e-access/Articles/gernstein.html
[Hebert 2003]: http://dx.doi.org/10.1098/rspb.2002.2218
[Hibbett and Glotzer 2011]: http://dx.doi.org/10.1111/j.1469-8137.2011.03819.x
[Kaup 1829]: http://dx.doi.org/10.5962/bhl.title.63915
[Kennedy et al. 2005]: http://dx.doi.org/10.1007/11530084_8
[Krell 2000]: http://dx.doi.org/10.1038/35014664
[Lespinats and Fertil 2011]: http://dx.doi.org/10.4137/EBO.S7565
[Lim et al. 2011]: http://dx.doi.org/10.1093/sysbio/syr030
[MacCallum 2007]: http://dx.doi.org/10.1371/journal.pbio.0050285
[Maddison et al. 2012]: http://dx.doi.org/10.1016/j.tree.2011.10.010
[Martin et al. 2005]: http://dx.doi.org/10.1016/S1359-6446(05)03651-2
[May 1988]: http://dx.doi.org/10.1126/science.241.4872.1441
[Miller et al. 2009]: http://dx.doi.org/10.1186/1756-0500-2-101
[Müller-Wille and Charmantier 2012]: http://dx.doi.org/10.1016/j.shpsc.2011.10.021
[Nagy et al. 2011]: http://dx.doi.org/10.1111/j.1469-8137.2011.03707.x
[Page 1983]: http://dx.doi.org/10.1080/03014223.1983.10423904
[Page 2008a]: http://dx.doi.org/10.1093/bib/bbn022
[Page 2008b]: http://dx.doi.org/10.1186/1751-0473-3-2
[Page 2009]: http://dx.doi.org/10.1186/1471-2105-10-S14-S5
[Page 2010]: http://dx.doi.org/10.1016/j.websem.2010.03.004
[Page 2011a]: http://dx.doi.org/10.1371/currents.RRN1228
[Page 2011b]: http://dx.doi.org/10.1186/1471-2105-12-187
[Page 2011c]: http://iphylo.blogspot.co.uk/2011/04/dark-taxa-genbank-in-post-taxonomic.html
[Page 2012]: http://dx.doi.org/10.6084/m9.figshare.92091
[Parr et al. 2012]: http://dx.doi.org/10.1016/j.tree.2011.11.001
[Patterson et al. 2010]: http://dx.doi.org/10.1016/j.tree.2010.09.004
[Penev et al. 2010]: http://dx.doi.org/10.3897/zookeys.50.538
[Sanderson et al. 2008]: http://dx.doi.org/10.1080/10635150802158688
[Peters 1846]: http://biostor.org/reference/102396
[Sarkar 2007]: http://dx.doi.org/10.1093/bib/bbm037
[Sarkar et al. 2008]: http://dx.doi.org/10.1186/1471-2148-8-144
[Smith et al. 2003]: http://dx.doi.org/10.1045/january2003-smith
[Solow et al. 1995]: http://dx.doi.org/10.1093/sysbio/44.1.93
[Taberlet et al. 2012]: http://dx.doi.org/10.1111/j.1365-294X.2012.05470.x
[Thessen et al. 2012]: http://dx.doi.org/10.1155/2012/391574
[Van de Sompel and Beit-Arie 2001]: http://dx.doi.org/10.1045/march2001-vandesompel
[Van Noorden 2012]: http://dx.doi.org/10.1038/483134a
[Vences et al. 2005]: http://dx.doi.org/10.1186/1742-9994-2-5
[Wägele et al. 2011]: http://dx.doi.org/10.1186/1742-9994-8-25
[Werner 2006]: http://dx.doi.org/10.1080/00222930600903660
[Yan and Gerstein 2011]: http://dx.doi.org/10.1371/journal.pone.0019917









