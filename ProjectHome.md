## Linking Open Germplasm Data (LOGD) ##

There is an abundance of information about plant germplasm available on the Web. Data ranges from passport data, which contains basic identification information on specific germplasm, to characterization and evaluation data (C&E) produced in field trials. These data are typically not connected together, which reduces the ease with which insights can be gained. The Linking Open Germplasm Data (LOGD) project aims to (i) survey publicly available data about germplasm, (ii) create Linked Data representations of the data sets, and (iii) identify interesting scientific questions that can be answered once the data sets are connected.

The project will also provide recommendations for the best practices of exposing germplasm data in a Linked Data representation. More on project [Deliverables and Roadmap](Roadmap.md).

Our vision is to create a web of interconnected germplasm-related data. Genesys can be used as a starting point as it provides stable and resolvable HTTP URIs in the form of https://www.genesys-pgr.org/acn/id/4206605 which also return RDF/Turtle. Consequently to further build upon this web (or graph), datasets such as the Collecting Missions (http://bioversity.github.io/geosite/) and Agtrials (http://agtrials.org/tbtrial/3267) can be used to expand the graph. Our goal is to link together as many germplasm-related datasets as possible, and also link to other useful resources in the [LOD cloud](http://lod-cloud.net/).

### Datasets ###

Here's a [VoID](https://logd-germplasm.googlecode.com/git/void.ttl) file containing all the interlinks of the hereunder datasets.

  * [Genesys](https://www.genesys-pgr.org), one of the largest accessions aggregators, publishes RDF:
    * `$curl -H "Accept:text/turtle" "https://www.genesys-pgr.org/acn/id/3483930"`
    * http://data.bioversityinternational.org/genesys-scraped/ is a SPARQL endpoint of such data.

  * Germplasm [Collecting Missions](http://bioversity.github.io/geosite/)  ([SPARQL endpoint](http://data.bioversityinternational.org/collectingmissions/), [collecting-missions-11-04-2014.nt.gz](https://logd-germplasm.googlecode.com/git/collecting-missions-11-04-2014.nt.gz))

### Interlinks ###

  * [Genesys links to Collecting Missions](GenesysLinks.md) - (40647 links, [links-genesys-missions.jsonld.gz](https://logd-germplasm.googlecode.com/git/links-genesys-missions.jsonld.gz))

![http://i.imgur.com/29ada3L.png](http://i.imgur.com/29ada3L.png)

**See also** the <a href='https://code.google.com/p/darwincore-germplasm/'>Germplasm Vocabulary</a>, the <a href='http://www.cropontology.org/'>Crop Ontology</a>, and the <a href='http://wiki.aginfra.eu/index.php/Germplasm_Working_Group'>agInfra Germplasm Working Group</a>.