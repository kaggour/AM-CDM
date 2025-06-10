# AM-CDM Documentation for the General AM Practitioner

Additive Manufacturing - Common Data Model

## *Documentation Development Notes (delete later)*  

*Objective: Create 3 versions of documentation for different CDM users/viewpoints:*  
*1.	General AM Practitioner (this README document) – Peter to lead, people to volunteer for writing sections*    
*2. Wiki Pages (more detailed versions of certain important sections of the README, we decide which sections, page for each module, etc.) - Benjamin to lead outline for this*  
*3.	Developer Guide (readme proper) - Benjamin Standfield to lead this activity*  
*4.	Standard – hold for later (express?)*  

*Use CDM Chapter from ASM Handbook as a good primary reference for information*
*https://doi.org/10.31399/asm.hb.v24A.a0006963*

*Keep writing in each section down to a few sentences - goal is to allow people to understand quickly (10-15 minute read time) what this is and direct them to other sources (ASM handbook, Wiki Pages) for more context.*  

*More detailed information, graphics, links, etc. could be contained in the Wiki pages - see for reference: https://github.com/idaholab/Deep-Lynx/wiki*  

*This content could be put into a PPT/PDF for sharing outside of the Github environment*  

## What is the AM CDM - Lead: Kareem Aggour
Additive manufacturing (AM), as a fully digital process, relies heavily on data spanning input materials, process parameters, post-processing steps, and inspections. Despite its potential, AM remains a developing field, requiring collaboration among academia, corporations, national labs, professional societies, and more. These partnerships depend on extensive data sharing across the AM ecosystem, including material vendors, equipment manufacturers, part suppliers, and customers.

However, effective data management and data sharing is challenging. To address this, many organizations are adopting the FAIR Guiding Principles (ref1) to make their data Findable, Accessible, Interoperable, and Reusable (FAIR). Interoperability, a key FAIR principle, is essential for seamless data exchange and requires community-driven vocabulary standards. To address this need, the ASTM F42.08 Subcommittee on Data developed the F3490-21 standard Common Data Dictionary (CDD), to develop a common vocabulary around the key terms in the AM space (ref2). While CDDs help standardize how humans describe data, they rely on human interpretation of relationships, limiting machine-to-machine communication. This lack of standardized, machine-readable data relationships prevents automated data exchange across systems.

To achieve seamless data interoperability by systems, AM developers need a common data representation. A Common Data Model (CDM) solves this by defining the logical structure and relationships of the terms in the CDD (ref3). An effective CDM must be both human-readable, enabling users to understand and utilize the data, and machine-computable, allowing systems to process data automatically. Semantic models (ontologies) are the preferred technology for creating such CDMs. The CDM is not a data schema, so organizations adopting it do not need to change their internal data storage systems. Instead, they must map and translate their internal data representations to the CDM for external data sharing. In this way, the CDM acts as a "lingua franca," allowing systems to maintain their internal data structures while using a shared language for communication across boundaries (ref4).

While the CDM enables humans and machines to communicate about AM data, a key challenge remains--the format used for data exchange. A Common Data Exchange Format (CDEF), aligned with the CDM's structure, enables data exchange in formats like XML or JSON. This eliminates the need for creating individual mappings between each party wishing to exchange AM data (ref5).

Overall, the CDD standardizes the AM vocabulary for human use, the CDM structures the vocabulary for machine usability, and CDEFs enable machines to exchange data based on the structure of the CDM.


## AM CDM Scope - Lead: Peter Coutts
The AM-CDM is currently AM process-agnostic, meaning that it does not include AM domain-specific information, such as data related specifically to Metallic Laser Powder Bed Fusion or Metallic Wire-Arc Directed Energy Deposition. Future efforts can focus on the creation of extensions to the AM CDM for these specific domains, relying on the domain Subject Matter Experts (SMEs) to define and organize the data of that domain.  By creating a process-agnositic AM data model, the framework for extension to more specific domains should be enabled. For instance, SADL data models representing specific destructive testing types (e.g. tensile testing) or specific thermal treatments (e.g. stress relief) could be constructed that build on the AM CDM. It is worth noting that certain non-AM concepts (e.g. organization, personnel, system) needed to be included in the AM CDM in order to create a wholistic picture of the AM data pedigree.

## AM CDM Structure - Lead: Alex Kuan
*insert some graphics of the AM CDM to help visualize the organization and structure*
*focus on most important classes*


## How to use the AM CDM - Lead: Richard Huff, supporting Benjamin Standfield (All contribute ideas?)

### What is the use case for a general AM practitioner?
### How a non-data person may apply the CDM in their organization, even if not implemented in a database, etc.
### Minimum viable data, enable data pedigree via data connectivity
### How the CDM relates to data exchange formats
*should we define conformance to the AM CDM? If so, include loose rules*


## How to Derive Data Exchange Formats from the CDM - Lead: Shengyen Li (Hunter and Luke?)


## What is SADL - Lead: Kareem Aggour
The AM-CDM is designed and developed in the Semantic Application Design Language (SADL) (ref6). SADL is both a language and an Eclipse plugin designed to simplify ontology creation. SADL uses a formal, English-like syntax and grammar, enabling users to author ontologies that are automatically converted into the Web Ontology Language (OWL), the W3C standard for semantic modeling (ref7). SADL was specifically developed to make ontologies accessible to non-semantic domain experts, allowing them to read and understand these models with ease. Its intuitive design makes it straightforward for domain experts such as additive engineers and materials scientists to collaborate with computer scientists to rapidly develop ontologies, without requiring those domain experts to become proficient in semantic modeling.

Each SADL file contains a collection of classes, which are comprised of zero to many attributes. These attributes can be of a primitive type, such as string, int, double, and more, or can be of a complex type, and be defined by a class name. In this way, classes can be linked to each other through attributes, creating a potentially complex graph network. The cardinality of each attribute is also defined, as each attribute is specified to be single-valued (‘with a single value of type’) or multi-valued (‘with values of type’).

Each class may also have a type, allowing for the inheritance of attributes between classes.

## How to reference the AM-CDM - Lead: Kareem Aggour

### Citing
### Versioning


## CDM Structure - Lead: Alex Kitt
*This section may need a rename to avoid confusion with Alex Kuan's section with graphics.*  

### Inheritance/Meta-Rules


## Who is using the AM CDM - Lead: Yan Lu

### Current users
### Examples of use
### How to submit record of use


## Future Work - Lead: Yan Lu

### Standardization
### Expansion to sub-domains (PBF, DED, specific TICs, etc.)
### How to get involved and/or provide feedback


## References - Lead: ALL

1. M. Wilkinson, M. Dumontier, I. Aalbersberg, _et al_. (2016), The FAIR Guiding Principles for scientific data management and stewardship. _Scientific Data_ (3), article no. 160018. https://doi.org/10.1038/sdata.2016.18
2. [ASTM F3490](https://store.astm.org/f3490-21.html)
3. K.S. Aggour. (2023), Evolution of Data Management and Common Data Models for Additive Manufacturing. _Additive Manufacturing Design and Applications_, ASM Handbook, vol. 24A, pp. 210-218. https://doi.org/10.31399/asm.hb.v24A.a0006963
4. A. Kuan, K.S. Aggour, S. Li, _et al_. (2024), A Common Data Dictionary and Common Data Model for Additive Manufacturing. _Integrating Materials and Manufacturing Innovation_, vol. 13, pp. 105-119. https://doi.org/10.1007/s40192-024-00341-x, https://rdcu.be/dEl5G
5. S. Li, Y. Lu, K.S. Aggour, _et al_. (2023), Enabling FAIR Data in Additive Manufacturing to Accelerate Industrialization. _Advanced Manufacturing Series (NIST AMS)_, National Institute of Standards and Technology, Gaithersburg, MD, https://doi.org/10.6028/NIST.AMS.500-1, https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=936454
6. A. Crapo and A. Moitra. (2013), Toward a Unified English-like Representation of Semantic Models, Data, and Graph Patterns for Subject Matter Experts. _International Journal of Semantic Computing_, vol. 7, no. 3, pp. 215-236. http://dx.doi.org/10.1142/S1793351X13500025
7. W3C Web Ontology Language: https://www.w3.org/OWL/



*Move below to Developer Guide:*  

## Meta-Rules

* Subclasses must never add new attributes with an identical purpose as superclass attributes. When the subclass attribute is of a more specific type than the superclass attribute, the subclass should simply override the superclass attribute with the more specific type
* Each class which has at least one attribute is assigned a unique short hand name listed in shorthand.xlsx
* Each object property is prepended by the shorthand of the class it originates in
