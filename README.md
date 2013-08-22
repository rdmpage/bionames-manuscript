BioNames: linking taxonomy, texts, and trees
============================================

# Abstract

BioNames aims to create a biodiversity “dashboard” where at a glance we can see a summary of the taxonomic and phylogenetic information we have for a given taxon, and that information is seamlessly linked together in one place. It combines classifications from EOL with animal taxonomic names from ION, and bibliographic data from multiple sources including BHL, CrossRef, and Mendeley. The goal is to create a database where the user can drill down from a taxonomic name to see the original description, track the fate of that name through successive revisions, and see other related literature. Publications that are freely available will displayed in situ. If the taxon has been sequenced, the user can see one or more phylogenetic trees for those sequences, where each sequence is in turn linked to the publication that made those sequences available. For a biologist the site provides a quick answer to the basic question “what is this taxon?”, coupled with with graphical displays of the relevant bibliographic and genomic information.


# Introduction

Large-scale digitisation of biodiversity data is underway on at least three broad fronts. The first, and perhaps the only category that is genuinely "born digital" is DNA sequencing. DNA barcoding [] and, more recently, metagenomics [] is generating a flood of sequence data, much of it tied to a specific place and time. The contents of natural history collections are being digitised [Leveraging the fullest potential of scientific collections through digitisation], both the specimens themselves [Blagoderov et al. 2012] and metadata about those specimens. The latter is being aggregated by [GBIF](http://data.gbif.org) to provide an overview of the spatial distribution of life on Earth. Much of the biological literature is similarly being converted from physical to digital form, most notably by the Biodiversity Heritage Library []. Taxonomic publication is becoming increasingly digital through rise of "mega" journals such as Zootaxa [], and semantically enriched journals such as ZooKeys [].

The increasing use of sequence data has made taxonomic relationships computable (e.g., by building phylogenetic trees). Yet many DNA sequences are disconnected from taxonomy because they lack formal taxonomic names [Parr et al. 2012]. Barcoding has been responsible for a massive influx of these "dark taxa" into the sequence databases [http://iphylo.blogspot.co.uk/2011/04/dark-taxa-genbank-in-post-taxonomic.html]. Many of these unnamed barcode taxa have since been suppressed by Genbank. But even without the barcoding sequences, dark taxa have been steadily increasing in number in recent years. Names may have a special place in the hearts of taxonomists [Patterson et al. 2010] but the pace of biodiversity discovery is outstripping our ability to put names on taxa, as evidenced by the rise of dark taxa in GenBank. There are increasing calls to adopt less formal taxonomic naming schemes (Schindel and Miller 2010), or to focus on having describing biodiversity without necessarily naming it [10.1016/j.tree.20, 11.11.007 10.1016/j.tree.2011.10.010]. A significant challenge will be determining whether these dark taxa represent newly discovered taxa, or come from known taxa but have not been identified as such [10.1111/j.1469-8137.2011.03819.x, 10.1111/j.1469-8137.2011.03707.x]. This gap between names and genes is mirrored by biodiversity databases that reflect a long tradition of aggregating taxonomic names and data tagged with those names, but lack either links to the primary literature of taxonomy, or the genomic data that is flooding into GenBank.

The vision of "Biodiversity Information on Every Desktop" [Edwards 2000] (perhaps updated to "biodiversity on every device") rests on our ability to not only digitise life (and the documents we have generated during centuries of cataloguing and studying biodiversity) but also to integrate the wealth of data emerging from sequencing machines and optical scanners. There are numerous points of contact between these different efforts, such as specimen codes, bibliographic identifiers, and GenBank accession numbers [Page 2008] (FIG 1). The most common shared identifier that spans sequences, specimens, and publications is the taxonomic name [Sarkar 2007][Patterson et al. 2010], despite the ambiguity in what a name "means"  [Kennedy et al. 2005][Franz and Cardona-Duque 2012]. 



In response to the Encyclopedia of Life "Computational Data Challenge" [url] BioNames project 

Its goal is to create a database of taxonomic names linked to the primary literature and, wherever possible, to phylogenetic trees. Existing globally unique identifiers for taxonomic names, concepts, publications, and sequences are re-used. Using identifiers rather than cryptic text strings (for example, abbreviated bibliographic citations) simplifies the task of linking - we can rely on exact matching of identifiers rather than approximate matching between names for what may or may not be the same entity. This is particularly relevant once we start to aggregate information from different databases, where the same information (e.g., a publication) may be represented by a different string. Furthermore, if we use existing identifiers we increase the potential to connect to other databases [Page 2008]. 


- Blagoderov, V., Kitching, I., Livermore, L., Simonsen, T., & Smith, V. (2012). No specimen left behind: industrial scale digitization of natural history collections. ZooKeys, 209(0), 133–146. [DOI: 10.3897/zookeys.209.3178]

- Edwards, J. L. (2000). Interoperability of Biodiversity Databases: Biodiversity Information on Every Desktop. Science, 289(5488), 2312–2314. [DOI: 10.1126/science.289.5488.2312]

- Franz, N. M., & Cardona-Duque*, J. (2013). Description of two new species and phylogenetic reassessment of Perelleschus O’Brien & Wibmer, 1986 (Coleoptera: Curculionidae), with a complete taxonomic concept history of Perelleschus sec. Franz & Cardona-Duque, 2013 . Systematics and Biodiversity, 11(2), 209–236. [DOI:10.1080/14772000.2013.806371]

- Kennedy, J. B., Kukla, R., & Paterson, T. (2005). Scientific Names Are Ambiguous as Identifiers for Biological Taxa: Their Context and Definition Are Required for Accurate Data Integration (pp. 80–95). Springer-Verlag. [DOI:10.1007/11530084_8]

- Page, R. D. M. (2008). Biodiversity informatics: the challenge of linking data and the role of shared identifiers. Briefings in Bioinformatics, 9(5), 345–354. [DOI: 10.1093/bib/bbn022]

- Parr, C. S., Guralnick, R., Cellinese, N., & Page, R. D. M. (2012). Evolutionary informatics: unifying knowledge about the diversity of life. Trends in Ecology & Evolution, 27(2), 94–103. [DOI: 10.1016/j.tree.2011.11.001]

- Patterson, D. J., Cooper, J., Kirk, P. M., Pyle, R. L., & Remsen, D. P. (2010). Names are key to the big new biology. Trends in Ecology & Evolution, 25(12), 686–691. [DOI: 10.1016/j.tree.2010.09.004]

- Sarkar, I. N. (2007). Biodiversity informatics: organizing and linking information across the spectrum of life. Briefings in Bioinformatics, 8(5), 347–357. [doi:10.1093/bib/bbm037]

[Blagoderov et al. 2012]: http://dx.doi.org/10.3897/zookeys.209.3178
[Edwards 2000]: http://dx.doi.org/10.1126/science.289.5488.2312
[Franz and Cardona-Duque 2013]: http://dx.doi.org/10.1080/14772000.2013.806371
[Kennedy et al. 2005]: http://dx.doi.org/10.1007/11530084_8
[Page 2008]: http://dx.doi.org/10.1093/bib/bbn022
[Parr et al. 2012]: http://dx.doi.org/10.1016/j.tree.2011.11.001
[Patterson et al. 2010]: http://dx.doi.org/10.1016/j.tree.2010.09.004


# Materials & Methods

## Data reconciliation

BioNames integrates data on taxonomic names and classifications, literature, and phylogenies from a variety of sources. Given the inevitable differences in how different databases treat the same data (as well as internal inconsistencies within individual databases) means that considerable effort must be spent cleaning and reconciling data. Much of this process involves mapping "strings" to "things" [10.1145/1376616.1376746], or more precisely, mapping strings to identifiers for things.

Figure 1 shows the relationships that are the focus of BioNames, namely the link between a taxonomic name and its publication...


## Taxon names

At present the taxonomic scope of BioNames 

Taxonomic names were obtained from the Index of Organism Names (ION). Each name in ION has a Life Science Identifier (LSID) [10.1016/S1359-6446(05)03651-2] which uniquely identifies that name. LSIDs can be dereferenced to return metadata in RDF [10.1186/1751-0473-3-2], ION LSIDs provide basic information on a taxonomic name using the TDWG LSID vocabulary, in many cases including bibliographic details for the publication where the name first appear. This bibliographic string was parsed into component elements (e.g., article title, journal, volume, pagination) and 




## Bibliographic identifiers

Most taxonomic databases are little more than online collections of 5×3 index cards, a technology taxonomy's founding father Linnaeus pioneered [10.1016/j.shpsc.2011.10.021]. When taxonomic literature is cited, it is typically as a text string. In populating BioNames every effort has been made to map a bibliographic string to a corresponding identifier, such as a Digital Object identifier (DOI).  While DOIs are the best-known bibliographic identifier, there are several others that are relevant to the taxonomic literature [10.1186/1471-2105-10-S14-S5]. DOIs are themselves based on Handles (http://hdl.handle.net) an identifier widely used by digital repositories such as DSpace (http://www.dspace.org/). A number of journals, such as the Bulletins and Novitates of the American Museum of Natural History are available in DSpace repositories and consequently have Handles. Other major archives such as JSTOR (http://www.jstor.org/) and CiNii (http://ci.nii.ac.jp/) have their own unique identifiers (typically integer numbers that are part of a URL). Having a variety of identifiers complicates the task of finding existing identifiers for a particular publication. Whereas for some identifiers, such as DOIs and CiNii NAIDs) (National Institute of Informatics Article IDs) there are OpenURL resolvers for this task, for other identifiers there may be no obvious way to find the identifier other than by using a search engine.

Identifiers also exist for aggregations of publications, such as journals. The practice of abbreviating journal titles in citations has led to a plethora of ways to refer to the same journal. For example, the BioStor database [10.1186/1471-2105-12-187]  has more than ten variations on the name of the journal Bulletin of Zoological Nomenclature (such as Bull Zool Nomen, Bull Zool Nom., Bull. Zool. Nomencl., etc.). This practice of abbreviating journal names (motivated by the desire to conserve space on the printed page) complicates efforts to match citations to identifiers. One approach to tackling this problem is to map abbreviations to journal-level globally unique identifiers, such as International Standard Serial Numbers  (ISSNs) (for the Bulletin of Zoological Nomenclature the ISSN is 0007-5167). In addition to reducing ambiguity, there are web services such as that offered by WorldCat that take ISSNs and return the history of name changes for a journal, which in turn can help clarify the often complicated history of long-lived journals.

## Clustering names

ION has multiple records for the same name, so names where clustered before populating BioNames. Names 9components, etc.).


## Mapping names to taxa

Matching taxon names to classifications can present problems. Ideally there would be a one-to-one mapping between a name and a taxon, but complications often arise. In addition to the typical problems of synonymy (more than one name for the same taxon) and homonymy (the same name used for different taxa) name and taxon databases may store different name strings. For example, ION has four records for the name "Nystactes":

Nystactes				urn:lsid:organismnames.com:name:2787598
Nystactes Bohlke		urn:lsid:organismnames.com:name:2735131
Nystactes Gloger 1827	urn:lsid:organismnames.com:name:4888093
Nystactes Kaup 1829	urn:lsid:organismnames.com:name:4888094

GBIF has three taxa with this name:

Nystactes Böhlke, 1957	2403398
Nystactes Gloger, 1827	2475109
Nystactes Kaup, 1829	3239722


Note the differences in the name string ("o" versus "ö" in "Böhlke", missing year, additional ","). To automate the mapping of names to concepts in cases like this I constructed a bipartite graph where the nodes are taxon names, divided into two sets based on which database they came from. I then connect the nodes of the graph by edges, weighted by how similar the names are ([define the measure]. For example, here is the graph for "Nystactes" [FIG]. Computing the maximum weighted bipartite matching of this graph creates a map between the two sets of names.

In theory GBIF should have only one entry for Nystactes as each animal name (with a few exceptions) must be unique. If a newer name has already been published before, then it must be replaced. In this case, Nystactes B has been replaced by x, and Nystactes Kaup, 1829 [10.5962/bhl.title.63915] by Paramyotis Bianchi (1916)

[Bianchi 1916. Annuaire du Musee Zoologique de l'Academie d. Sciences de St. Petersbourg 21:xxiii-xxxii]

Nystactes


homonym (the name x has been replaced by y [10.2307/1439557]

On the Occurrence of Garden Eels in the Western Atlantic, with a Synopsis of the Heterocongrinae

James Böhlke
Proceedings of the Academy of Natural Sciences of Philadelphia , Vol. 109, (1957), pp. 59-79
Published by: Academy of Natural Sciences
Article Stable URL: http://www.jstor.org/stable/4064494







http://iphylo.blogspot.co.uk/2013/04/bionames-update-reconciliation.html




## Images

Images for taxa were obtained from EOL. Given that BioNames uses taxa from GBIF and NCBI, EOL's API was used to map the GBIF and NCBI identifiers to the corresponding record in EOL, and the EOL API used to retrieve an appropriate image to display.


## Phylogenies

Phylogenies were obtained from the PhyLoTA database  [Sanderson et al. 2008]. This database contains eukaryote phylogenies constructed from automatically assembled clusters of genes 


A MySQL data dump was downloaded from http://phylota.net (version 184, corresponding to the GenBank release of the same version number) and user to populate a local MySQL database. Metadata for the sequences in each phylogeny was obtained from EMBL, and used to populate the MySQL database with basic information such as taxon and locality information, as well as bibliographic details for the sources of the sequences. Each phylogeny was then exported in JSON format and uploaded into CouchDB.

- Sanderson, M., Boss, D., Chen, D., Cranston, K., & Wehe, A. (2008). The PhyLoTA Browser: Processing GenBank for Molecular Phylogenetics Research. Systematic Biology, 57(3), 335–346. [DOI: 10.1080/10635150802158688][Sanderson et al. 2008]

[Sanderson et al. 2008]:http://dx.doi.org/10.1080/10635150802158688

# Results


## Interface

BioNames comprises a CouchDB database, and API, and a web interface. 


Phylogenies from PhyLOTA are rendered in SVG where terminal taxa with the same label have the same colour. This makes it easier to recognise clusters of sequences from the same taxon (e.g., conspecific samples), as well as highlight possible errors (e.g., mislabelled or misidentified sequences).





Features




Dashboard

publishers





Discussion


Future

The state of taxonomy

[coverage of taxa, impact of journals and publishers, what needs to be digitised, 






Limitations (degree of connectivity)


Each phylogeny in BioNames is associated with one or more publications (i.e., those listed in the GenBank records for the sequence used to obstruct the tree). Some of these will also contain taxonomic descriptions, and so may already exist in BioNames. It would obviously be desirable to merge these records, and this could be most easily done if the GenBank records had bibliographic identifiers. However, a significant fraction of GenBank records lack such identifiers [10.1186/1756-0500-2-101], hence significant effort will need to be made to merge these two sources of bibliographic data.

Impact

The taxonomic community has long felt disadvantaged by the role of citation-based “impact factor” in assessing the importance of taxonomic research [10.1038/35093267, 10.1038/35014664, 10.1080/00222930600903660] especially as much of the taxonomic literature appears in relatively low impact journals. A common proposal is to include citations to the taxonomic authority for every name mentioned in a scientific paper [10.1186/1742-9994-8-25]. Regardless of the merits of this idea, there is value in surfacing identifiers for the taxonomic literature. In addition to citations, identifiers can facilitate other measure of the value of a taxonomic paper.  The growing “altmetrics” movement (http://altmetrics.org/manifesto/) aims to provide metrics for the post-publication impact of a publication in terms of activity such as social bookmarking, and commentary on web sites ([10.1371/journal.pone.0019917]. Gathering these metrics is greatly facilitated by using standard bibliographic identifiers (otherwise, how do we know whether two commentators are discussing the same article or not?). If taxonomic literature is be part of this burgeoning conversation it needs to be able to be identified unambiguously.


Links

BioNames makes extensive use of identifiers to clean and link data, but the real value from identifiers becomes apparent when they are shared, that is, when different databases use the same identifiers for the same entities, instead of minting their own. Reusing identifiers can enable unexpected connections between databases. For example, the PubMed biomedical literature database has a record (PMID:948206) for the paper “Monograph on "Lithoglyphopsis" aperta, the snail host of Mekong River Schistosomiasis” (Davis et al. 1976). The PubMed record contains the abstract for the paper, but no link to where the user can obtain a copy of the paper. Actually, this reference is in a volume scanned by BHL, and has been extracted by BioStor (http://biostor.org/reference/102054). If PubMed was linked to BHL, users of PubMed could go straight to the content of the article. But this is just the start. The Davis et al. (1976) also paper mentions museum specimens in the collection of the Academy of Natural Sciences of Drexel University, Philadelphia. Metadata for these specimens has been aggregated by GBIF, and the BioStor page for this article displays those links. In an ideal world we should be able to go from PubMed to BioStor to GBIF. But in many ways the real power will come from traversing these links in the other direction. At present, a user of GBIF simply sees metadata for these specimens and a locality map. They are unaware that these specimens have been cited in a paper (Davis et al. 1976) which shows that the snails host the Mekong River schistosome. This connection would be trivial to make if the reciprocal link was made from GBIF to BioStor. Furthermore, the link from BioStor to PubMed would give us access to Medical Subject Headings (MeSH http://www.nlm.nih.gov/mesh/) for the paper. Hence we could imagine ultimately searching GBIF using queries from a controlled vocabulary of biomedical terms. 

Making these connections requires not only that we have digital identifiers, but also that where ever possible we reuse existing identifiers. In practice forging these links can be hard work [10.1371/currents.RRN1228]. However, if we restrict ourselves to project-specific identifiers then we stymie attempts to create a network of connected data on biodiversity. 


Dark taxa

As a final motivation to surface deep taxonomic data, consider the rise of “dark taxa” in genomics databases (see http://iphylo.blogspot.co.uk/2011/04/dark-taxa-genbank-in-post-taxonomic.html). A growing percentage of “taxa” in GenBank lack a formal scientific name; in 2010 dark taxa comprised over 80% of invertebrate taxa added that year [10.1016/j.tree.2011.11.001]. Many of the most recent dark taxa are a product of DNA barcoding projects, and at the time of writing these sequences have been “suppressed” by GenBank, that is, they are still in the database but do not feature in search results. But there is still a background trend towards increasing numbers of unidentified sequences in GenBank. A significant challenge will be determining whether these dark taxa represent newly discovered taxa, or come from known taxa but have not been identified as such [10.1111/j.1469-8137.2011.03819.x, 10.1111/j.1469-8137.2011.03707.x].

It is clear that some dark taxa do, in fact, have names. For example, consider the frog "Gephyromantis aff. blanci MV-2005" (NCBI tax_id 321743), which has a single sequence AY848308 associated with it. This sequence was published as part of a DNA barcoding study [10.1186/1742-9994-2-5]. If we enter the accession number AY848308 into Google we find two documents, one the supplementary table for (Vences et al. 2005), the other the a subsequent paper by (Vences and Riva 2007) that describes the frog with this sequence as a new species, Gephyromantis runewsweeki. This is a relatively straightforward example, and the taxonomic description is freely available online. But it still required significant time to track down the species description for this one example.

A key question facing attempts to find names for dark taxa is whether the methods available can be scaled to handle the magnitude of the problem. One could argue that newer technologies such as DNA barcoding make classical taxonomy less relevant, and perhaps the effort in digitising older literature and exposing the taxonomic names it contains is misplaced. A counter argument would be that the taxonomic literature potentially contains a wealth of information on ecology, morphology and behaviour, often for taxa in areas that have been subsequently altered by human activity. Furthermore, as technologies such as barcoding uncover previously overlooked variation, older taxonomic names previously sunk in synonymy may yet become relevant. For example, several taxa have been synonymised with the silvery mole-rat Heliophobius argenteocinereus Peters, 1846 (Peters 1846) but DNA sequence data has revealed several clades within that species [10.1111/j.1469-7998.2011.00863.x]. Consequently, rather than coin new names for these clades we can potentially rescue older names from synonymy. Hence DNA barcoding may give a new lease of life to old names. [http://bionames.org/trees/phylota/ti10167_cl0_db184]

Publishing platform

Recently taxonomic journals have begun to mark up taxonomic names and descriptions [10.3897/zookeys.50.538], which is a precursor to linking names and data together. But these developments leave open the problem of what these links will point to. If we have a database of all taxonomic names and the associated literature, then such a database would provide an obvious destination for those links. Ultimately, we could envisage embedding new taxonomic publications within this database, so that each new publication becomes simply another document within the database. In the same way, we could use automated methods to extend the process of tagging names, specimens and literature cited to the legacy literature, so that the entire body of taxonomic knowledge becomes a single interwoven web of names, citations, publications, and data. [challenge entry]



Acknowledgements

I thank EOL for the funding that enabled Ryan Schenk to  Cyndy Parr provided adult supervision


Funding




References

Davis GM, Kitikoon V, Temcharoen P (1976) Monograph on “Lithoglyphopsis” aperta, the snail host of Mekong River schistosomiasis. Malacologia 15(2): 241-87.

Peters WCH (1846) Über neue Säugethiergattungen aus den Ordnungen der Insectenfresser und Nagethiere. Bericht über die zur Bekanntmachung geeigneten Verhandlungen der Konigl.Preuss.Akademie der Wissenschaften zu Berlin 1846: 257-259.


Vences M, Riva IDL (2007) A new species of Gephyromantis from Ranomafana National Park, south-eastern Madagascar (Amphibia, Anura, Mantellidae). Spixiana 30(1): 135-143.

