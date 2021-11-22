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
   Dataset in DCAT refers to the actual container of the data as defined in EMMO, hence, we would define DCAT dataset as a subclass of EMMO:Data that in addition to describing the actual data, is curated, or published by a single source and available to download by multitude of formats. We can then, under dataset define more specific datasets according to thir scope. The format is addressed by the EMMO:Language subclasses that implements the DCAT requirement that a dataset can be expressed in more than one format.
3. title        -->   **Name  (preferred label)** [arbitrary string connected to something, and its a property at same time] (it is general but when applied to a data it is like a title)
   this is simple, we use annotation for it. chck the individual myDataset, agents, or tools in DOME must make sure we enforce this in implementation. 
4. keyword      -->   **Keyword  (preferred label)** [arbitrary string connected to something, and its a property at same time]  (this is before the ontology, not a reductionist property). 
   - we consider strinct keywords, and those that are aligned with ontology (EMMO dataset). 
   - we offer support for both, and we call them: 
     - any keyword in the ontology can be used in teh **SemanticKeywords** (constrained annoatation, as it is done by the external, and term points to an IRI not a term so we are future compatible). This may be further subclassed into various categories, like the type of models, experiments, or even datasets. Note that the dataset itself can also be subclassed further to give meaning to the syntactic entity, rendering it semantic essentially (e.g., an excell file is a syntactic file, abut is semantically defined in EMMO)..  
       - TypeKeyword: say something (strong) about the type, points to an IRI to which the individual is an RDF type
       - ProeprtyKeyword; say something about the data set, does not emply its a type but says to which entity the data set is about in some way as defined by the creator. 
     - any keyword (label, annotation etc.) not in the ontology, is a **syntacticKeyword* (points to nnothinh, and is simple a label, availabl for open searches and other tools, but looses the power of ontoloyg, should be used only when no existing SemanticKeywords available).    
     - dealing with the list of keywords: 
5. creator      -->   **Creator (preffered label)** [arbitrary string connected to something, and its a property at s
ame time] 
6. publisher    -->   **Publisher (preferred label)** the user (agent) that made the item available **on DOME**.   
7. issued       -->   ***hasIssueDate*** **IssueDate** relation points to a class [date]
9. license      -->   ***hasLicense* LicenseDocument**
10. source      -->   ***hasSource* Source**.  (Source is a URI or IRI). 
11. URI         -->   ***hasAdress* Adress** (data type, literal)
12. homepage    -->   ***hasHomePage* HomePage**
14. description -->   ***hasDescription* Description (annotation)**

# Elucidations 
* keyword can be a string that can be used to represent a property, or a property that refers to something specific. 
* creator: there are different types of creators, are they the ones doing the measurement, or preparing the data, or uploaing the data etc. 
* in DCterm it is: `The entity responsible for producing the resource. ` 
* in EMMO role in the holistic branch, part of the process of data creation, and 
* creator: the one responsible for creating the resource according to the publisher. i.e., it is not semantically llinked in the ontology.
* Publisher: The publisher can assign maintainer, we do not yet support this. The publisher is also the one responsible for the DOME data set consisting of the aboce metadata (the 14 elements). 
* License is given by the publisher and we only assume it is consistent with what may be defined in the actual data. 
