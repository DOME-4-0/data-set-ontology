# DOME EMMO compliant Dataset Ontology

The data set ontology for exchange that is build step wise gradually in DOME 4.0. 

# Rationale 

The aim is to be able to create a high level data set ontology and consequently implement various tools that allow
 DOME 4.0 data sets to be managed and semantically brokered and curated while supporting the wider data community with its 
 rich choice of existing various standards, specifically those supporting W3C standards. 
 
 The ontology is developed in line with the main requirements as depicted in [D1.3: Architecture of DOME](https://github.com/DOME-4-0/DOME-Architecture).


To keep things as simple as needed for the prototype, lets take the following basic examples and distill the bare minimum needed keywords for the DOME 4.0 ontology. 

## For reference here are some DCAT examples (version 2.0) 
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
## Summary of the main keywords and concepts 


Term | Definition | RDFS Schema References
-- | -- | --
DataSet | DCAT: A collection of data, published or curated by a single agent, and available for access or download in one or more representations. | dcat:dataset (rdf:Property) with range dcat:Dataset (rdfs:Class)
Title | DCTERMS: A name given to the resource. | dcterms:title (rdf:Property) with range rdfs:literal
Keyword | DCAT: A keyword or tag describing the resource. | dcat:keyword (rdf:Property) with range rdfs:literal
Creator | DCTERMS: An entity responsible for making the resource. | dcterms:creator (rdf:Property) with range dcterms:Agent (rdfs:Class)
Publisher | DCTERMS: An entity responsible for making the resource available. | dcterms:publisher (rdf:Property) with range dcterms:Agent (rdfs:Class)
Issued | DCTERMS: Date of formal issuance of the resource. | dcterms:issued (rdf:Property) with range rdfs:literal
License | DCTERMS: A legal document giving official permission to do something with the resource. | dcterms:license (rdf:Property) with range dcterms:LicenseDocument (rdfs:Class)
Source | DCTERMS: A related resource from which the described resource is derived. | dcterms:source (rdf:Property)
URI | DCTERMS: The set of identifiers constructed according to the generic syntax for Uniform Resource Identifiers as specified by the Internet Engineering Task Force (http://www.ietf.org/rfc/rfc3986.txt) | dcterms:URI (rdf:Datatype)
Homepage | FOAF: A homepage of the catalogue (a public Web document usually available in HTML). | foaf:homepage (rdf:Property) with range foaf:Document (rdfs:Class)
Description | DCTERMS: An account of the resource. | dcterms:description (rdf:Property)


## The working principle


From the above DCAT examples,  the following **core** data set keywords are slected for the initial DOME dataset ontology. Note that updates are expected, but they are not expected to be more than 2-3 more terms (e.g., to designate the source or tools of the data, see D3.1). 


The ```-->``` denotes the EMMO classes that correspond to the DCterms. 

### `DCTERM`       -->   **`EMMO` Class/preferred label**
   
   
   WIP
   ![](doc/dataset_mapping.jpg)


### `Dataset`      -->   **`Data Class`**


![](doc/dataset.png)

A `Dataset` in DCAT refers to the actual container of the data as defined in EMMO, hence we define DCAT dataset as a subclass of `EMMO:Data` which we create is is an `EMMO:DataSet`

### `title`        -->   **`Name`**  (preferred label): arbitrary string connected to something, and its a property at the same time.  We simply use annotation for it. DOME checks an individual `myDataset`, and agents, or tools in DOME must make sure we enforce this relation to a `title` in implementation.

### `keyword`      -->   **`Keyword`**

There are a number of ways to look at this. One view claims that in essence, a keyword is, if the data is fully ontologically described down to the individual elements, is a redundant concept, as all is needed to understand and process the information is present in full within. Another view, is that, even if we have a fully ontological description, keywords designate or refer in some way to specific characteristics that we would like to highlight. Keywords say something remarkable about the dataset (or any thing actually). Its like a synopses, or summary of sorts. The question arises therefore on how to represent these keywords themselves. Questions that need to be addressed are:

- what are the keywords?
- properties of the data set?
  
Note that a dataset is a property of the measurement (in a semiotic process) in EMMO, hence keywords in this case become properties of properties.  If keywords are lateral strings then in this case we need to make sure how we can relate them to semantic concepts.

- are keywords always connected to semantic concepts?
- In EMMO we would want to have every keyword to be explicitly related to an ontological concept, e.g., if we say that a certain 
 dataset has a set of keywords e.g., *{"atomistic", "additive manufacturing", "temperature profile"},* we would need every keyword to be related to an existing concept (a single concept, or multiple ones in some logical manner). This would be straight forward if we use throughout EMMO concepts to define the keywords but this is it self not always possible (see below). 
- In dcat, and in many other applications, keywords are either completely random (user defined) strings or a combination of predefined taxonomy keywords and user defined ones. In either case they are signs. Moreover, there is one key element to such keywords, that further distinguishes them from ones that are fully ontological. These keywords are not always guaranteed to be **faithful**, in other words, the dataset above, the keyword "atomistic" though claiming the data set has something to do with atomistic, this may be only from the point of view of a specific agent, and not entirely true from other perspective. It also can be erroneous, in the sense that the data set may have nothing to do with "atomistic" at all. An ontological description will not have this issue as the "keyword" elements are actually the data itself (e.g., atoms).
- In DCAT,  as the data itself is not yet ontologically in full. Keywords  represent "strings connected to something, and are supposed, according to an agent, to represent faithfully the type, kind, or connection of a dataset to some property or something".
- keywords can be thought of as emanating from a semiotic process, and as such they are properties of the data set it self.

**In summary, we need to account for**

1. semantic keywords, those that are related to an ontology in some way (or a taxonomy that we ontologise in DOME::EMMO)
2. syntactic keywords, those that are defined arbitrary by the user.

In both cases, there is no a priori imposed truth or expectation of faithfulness of either the semantic or syntactic keywords, both are specified by an agent, which may or may not "be honest" or even have access to the actual data, or even have the knowledge  needed to assert the truth. In other words, we have to choose whether to trust or not the keywords, and we may need to devise some kind of moderation process (Either automatic or human...)

- we consider strict keywords, and those that are aligned with ontology (EMMO dataset). 



#### SemanticKeywords 
Any keyword in the ontology can be used in the SemanticKeywords(constrained annotation,  and in turn points to an IRI). This may be further subclassed into various categories, like the type of models, experiments, or even datasets. Note that the dataset itself can also be subclassed further to give meaning to the syntactic entity, rendering it semantic essentially (e.g., an excell file is a syntactic file, but is semantically defined in EMMO)..  

### TypeKeyword
say something (strong) about the type, points to an IRI to which the individual is an RDF type
  
### ProeprtyKeyword
say something about the data set, does not emply its a type but says to which entity the data set is about in some way as defined by the creator. 
  
  
### SentacticKeyword 
any keyword (label, annotation etc.) not in the ontology, is a **syntacticKeyword* (points to nothing ontologically, but a laterial, and is simple a label, available for open searches and other tools, but looses the power of ontoloyg, should be used only when no existing SemanticKeywords are available).    

![](doc/keyword.png)


### creator   -->   **Creator (preferred label)** 

(arbitrary string connected to something, and its a property at same time). In DOME it is always referring to Individual


### publisher    -->   **Publisher (preferred label)** the user (agent) that made the item available **on DOME**.   
### issued       -->   ***hasIssueDate*** **IssueDate** relation points to a class [date]
### license      -->   ***hasLicense* LicenseDocument**
### source      -->   ***hasSource* Source**.  (Source is a URI or IRI). 
### URI         -->   ***hasAdress* Adress** (data type, literal)
### homepage    -->   ***hasHomePage* HomePage**
### description -->   ***hasDescription* Description (annotation)**

# Further Elucidations 
* keyword can be a string that can be used to represent a property, or a property that refers to something specific. 
* creator: there are different types of creators, are they the ones doing the measurement, or preparing the data, or uploaing the data etc. 
* in DCterm it is: `The entity responsible for producing the resource. ` 
* in EMMO role in the holistic branch, part of the process of data creation, and 
* creator: the one responsible for creating the resource according to the publisher. i.e., it is not semantically llinked in the ontology.
* Publisher: The publisher can assign maintainer, we do not yet support this. The publisher is also the one responsible for the DOME data set consisting of the aboce metadata (the 14 elements). 
* License is given by the publisher and we only assume it is consistent with what may be defined in the actual data. 



