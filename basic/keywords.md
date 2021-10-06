To keep things as simple as needed for the prototype, lets take the following basic examples and distil the bare minimum needed keywords for the DOME 4.0 ontology. Note, that we do not consider DCAT as an ontology yet, but a taxonomy, hence we use the terms as keywords to be otologised in EMMO.


(the below, is a copy from the basic examples of DCterms)
```javascript

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

```



From the above the following data set keywords are needed:

The ` --> ` denotes the EMMO classes that correspond to the DCterms. 
0. DCTERM       -->   **EMMO Class/preffered label**
1. Dataset      -->   **Data (Class0** (https://www.dublincore.org/specifications/dublin-core/dcmi-terms/#http://purl.org/dc/terms/title)
3. title        -->   **Name  (preferred label)** [arbitrary string connected to something, and its a property at same time] (it is general but when applied to a data it is like a title)
4. keyword      -->   **Keyword  (preferred label)** [arbitrary string connected to something, and its a property at same time]  (this is before the ontology, not a reductionist property). 
5. creator      -->   **Creator (preffered label)** [arbitrary string connected to something, and its a property at same time] 
6. publisher    -->   **Publisher (preferred label)** the user (agent) that made the item available **on DOME**.   
7. issued       -->   [date]
9. license      -->   
10. source      --> 
11. URI         --> 
12. homepage    --> 
13. path        --> 
14. description -->

# Elucidations 
* keyword can be a string that can be used to represent a property, or a property that refers to something specific. 


* creator: there are different types of creators, are they the ones doing the measurement, or preparing the data, or uploaing the data etc. 

in DCterm it is: `The entity responsible for producing the resource. ` 
in EMMO role in the holistic branch, part of the process of data creation, and 
creator: the one responsible for creating the resource according to the publisher. i.e., it is not semantically llinked in the ontology.

Publisher: The publisher can assign maintainer, we do not yet support this.
