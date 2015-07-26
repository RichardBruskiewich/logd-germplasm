### Genesys links with Collecting Missions ###

[links-genesys-missions.jsonld.gz](https://logd-germplasm.googlecode.com/git/links-genesys-missions.jsonld.gz) - 40647 links,  2.5 MB

Using this SPARQL query that was done against the endpoint containing both Genesys and Collecting Missions data, **40647 links** between genesys accessions and collecting missions data were made. These are only links that matched exactly an Accession Number, the Instititue Code and the Genus. More links could be made through accession number regex.


---


```
prefix rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#> 
prefix wgs84_pos: <http://www.w3.org/2003/01/geo/wgs84_pos#> 
prefix dwc: <http://rs.tdwg.org/dwc/terms/> 
prefix germplasm: <http://purl.org/germplasm/germplasmTerm#> 
prefix germplasmType: <http://purl.org/germplasm/germplasmType#> 
PREFIX cm: <http://data.bioversityinternational.org/collectingmissions/> 
PREFIX cmMission: <http://data.bioversityinternational.org/collectingmissions/MISSIONS_SAMPLES_SITES/> 

CONSTRUCT {
    ?genesysAcc dwc:sample ?sample;
            germplasm:germplasmIdentifier ?acceNumb;
            germplasmType:wiewsInstituteID ?instCode;
            dwc:genus ?genus.

    ?sample ?samplePredicate ?sampleObject.
}
WHERE {
?acc a cm:ACCESSIONS;
      cm:ACCESSIONS\/AccessionNumber ?acceNumb;
      cm:ACCESSIONS\/INSTCODE ?ipgriCode;
      cm:ACCESSIONS\/NEW_ID_SAMPLE ?newIdSample .

?sample cm:MISSIONS_SAMPLES_SITES\/NEW_ID_SAMPLE ?newIdSample;
        cm:MISSIONS_SAMPLES_SITES\/Genus ?genus;
        ?samplePredicate ?sampleObject.

?inst cm:INSTITUTES\/INSTCODE ?ipgriCode;
      cm:INSTITUTES\/FAOCODE ?instCode.

?genesysAcc a germplasm:GermplasmAccession;
            germplasm:germplasmIdentifier ?acceNumb;
            germplasmType:wiewsInstituteID ?instCode;
            dwc:genus ?genus;
}
```

### Federated SPARQL queries ###

I've setup three SPARQL endpoints:

  * Collecting Missions SPARQL: http://data.bioversityinternational.org/collectingmissions/
  * GENESYS scraped SPARQL: http://data.bioversityinternational.org/genesys-scraped/
  * Genesys links with Collecting Mission: http://data.bioversityinternational.org/genesys-missions/

These are three separate endpoints that don't know of each other. They could be on separate servers. Check the query on http://data.bioversityinternational.org/genesys-missions/ - it's essentially running remote queries using the other two endpoints to retrieve extra information. Yes the query is a bit slow if you increase the limit but that is obvious.

I think this is really powerful as it allows people to maintain their own data independently, then all it takes is someone coming in to build the links and allow for these sort of queries without even changing the data-sources.