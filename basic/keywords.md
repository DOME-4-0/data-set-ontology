To keep things as simple as needed for the prototype, lets take the following basic examples and distil the bare minimum needed keywords for the DOME 4.0 ontology. Note, that we do not consider DCAT as an ontology yet, but a taxonomy, hence we use the terms as keywords to be otologised in EMMO.

''' 
:catalog
  a dcat:Catalog ;
  dcterms:title "Imaginary Catalog"@en ;
  dcterms:title "Catálogo imaginario"@es ;
  rdfs:label "Imaginary Catalog"@en ;
  rdfs:label "Catálogo imaginario"@es ;
  foaf:homepage <http://example.org/catalog> ;
  dcterms:publisher :transparency-office ;
  dcterms:language <http://id.loc.gov/vocabulary/iso639-1/en>  ;
  dcat:dataset :dataset-001  , :dataset-002 , :dataset-003 ;



:transparency-office
  a foaf:Organization ;
  rdfs:label "Transparency Office"@en ;
  rdfs:label "Oficina de Transparencia"@es ;
  .


:dataset-001
  a dcat:Dataset ;
  dcterms:title "Imaginary dataset"@en ;
  dcterms:title "Conjunto de datos imaginario"@es ;
  dcat:keyword "accountability"@en, "transparency"@en, "payments"@en ;
  dcat:keyword "responsabilidad"@es, "transparencia"@es, "pagos"@es ;
  dcterms:creator :finance-employee-001 ;
  dcterms:issued "2011-12-05"^^xsd:date ;
  dcterms:modified "2011-12-15"^^xsd:date ;
  dcat:contactPoint <http://example.org/transparency-office/contact> ;
  dcterms:temporal <http://reference.data.gov.uk/id/quarter/2006-Q1> ;
  dcat:temporalResolution "P1D"^^xsd:duration ;
  dcterms:spatial <http://sws.geonames.org/6695072/> ;
  dcat:spatialResolutionInMeters "30.0"^^xsd:decimal ;
  dcterms:publisher :finance-ministry ;
  dcterms:language <http://id.loc.gov/vocabulary/iso639-1/en>  ;
  dcterms:accrualPeriodicity <http://purl.org/linked-data/sdmx/2009/code#freq-W>  ;
  dcat:distribution :dataset-001-csv ;
  .

'''



From the above the following data set keywords are needed:
1. Dataset
2. title 
3. keyword
4. creator 
5. issued
6. publisher
7. license
8. source
9. URI
10. homepage 
11. path


