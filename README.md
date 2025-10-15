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
Additive Manufacturing (AM), as a fully digital process, relies heavily on data spanning input materials, process parameters, post-processing steps, and inspections. Despite its potential, AM remains a developing field, requiring collaboration among academia, corporations, national labs, professional societies, and more. These partnerships depend on extensive data sharing across the AM ecosystem, including material vendors, equipment manufacturers, part suppliers, and customers.

However, effective data management and data sharing is challenging. To address this, many organizations are adopting the FAIR Guiding Principles [[1]](#ref1) to make their data Findable, Accessible, Interoperable, and Reusable (FAIR). Interoperability, a key FAIR principle, is essential for seamless data exchange and requires community-driven vocabulary standards. To address this need, the ASTM F42.08 Subcommittee on Data developed the F3490-21 Common Data Dictionary (CDD) standard, to develop a common vocabulary around key terms in the AM space [[2]](#ref2). While CDDs help standardize how humans describe data, they rely on human interpretation of relationships, limiting machine-to-machine communication. This lack of standardized, machine-readable data relationships prevents automated data exchange between systems.

To achieve seamless data interoperability by systems, AM developers need a common data representation. A Common Data Model (CDM) solves this by defining the logical structure and relationships of the terms in the CDD [[3]](#ref3). An effective CDM must be both human-readable, enabling users to understand and utilize the data, and machine-computable, allowing systems to understand and process data automatically. The CDM is not a data schema, so organizations adopting it do not need to change their internal data storage systems. Instead, they must align, map, and translate their internal data representations to the CDM for external data sharing. In this way, the CDM acts as a "lingua franca," allowing systems to maintain their internal data structures while using a shared language for communication across boundaries [[4]](#ref4). Alternatively, the CDM can be adopted as a data model for new data systems.

While the CDM enables humans and machines to communicate about AM data, a key challenge remains--the format used for data exchange. A Common Data Exchange Format (CDEF), aligned with the CDM's structure, enables data exchange in formats like XML or JSON. This eliminates the need for creating individual mappings between each party wishing to exchange AM data [[5]](#ref5). A CDEF for AM data is planned to be produced in the near future. Information about how to access this CDEF will be added to this repository when it is available.

Overall, the CDD standardizes the AM vocabulary for human use, the CDM structures the vocabulary for machine usability, and CDEFs enable machines to exchange data based on the structure of the CDM.


## AM CDM Scope - Lead: Peter Coutts
The AM-CDM is currently AM process-agnostic, meaning that it does not include AM domain-specific information, such as data related specifically to Metallic Laser Powder Bed Fusion or Metallic Wire-Arc Directed Energy Deposition. Future efforts can focus on extensions to the AM CDM for these specific domains, relying on the domain Subject Matter Experts (SMEs) to define and organize the data of that domain. For instance, data models representing specific destructive testing types (e.g. tensile testing) or specific thermal treatments (e.g. stress relief) could be constructed that build on the AM CDM. Specific, non-AM concepts (e.g. organization, personnel, system) have been included in the AM CDM in effort to create a wholistic picture of the AM data pedigree.

## AM CDM Structure - Lead: Alex Kuan
*insert some graphics of the AM CDM to help visualize the organization and structure*
*focus on most important classes*


## How to use the AM CDM - Lead: Richard Huff, supporting Benjamin Standfield (All contribute ideas?)

### What is the use case for a general AM practitioner?
### How a non-data person may apply the CDM in their organization, even if not implemented in a database, etc.
### Minimum viable data, enable data pedigree via data connectivity
### How the CDM relates to data exchange formats
*should we define conformance to the AM CDM? If so, include loose rules*

## What is SADL - Lead: Kareem Aggour
The AM-CDM is designed and developed in the Semantic Application Design Language (SADL) [[6]](#ref6). SADL is both a language and an Eclipse plugin designed to simplify data model development. SADL uses a formal, English-like syntax and grammar, enabling users to author data models that can be automatically converted into the Web Ontology Language (OWL), the W3C standard for semantic modeling [[7]](#ref7). SADL was specifically developed to make data models accessible to non-semantic domain experts, allowing them to read and understand these models with ease. Its intuitive design makes it straightforward for domain experts such as engineers and materials scientists to collaborate with computer scientists to rapidly develop data models, without requiring those domain experts to become proficient in semantic modeling.

Each SADL file contains a collection of classes, which are comprised of zero to many attributes. These attributes can be of a primitive type, such as string, int, double, and more, or can be of a complex type, and be defined by a class name. In this way, classes can be linked to each other through attributes, creating a potentially complex network of data concepts. The cardinality of each attribute is also defined, as each attribute is specified to be single-valued (‘with a single value of type’) or multi-valued (‘with values of type’).

Each class may also have a type, allowing for the inheritance of attributes between classes.

## How to Derive Data Exchange Formats from the CDM - Lead: Shengyen Li (Hunter and Luke?)
Depending on the target database technology, it may be necessary to convert the SADL specification into alternative formats such as XML or JSON. Preliminary parsing routines implemented in Python are available within the Jupyter notebooks located in the notebooks directory. For certain technologies—such as OWL or JSON-LD—that require more advanced semantic relationships, additional modeling may be needed. Nevertheless, it is strongly advised that the original attribute definitions and core class structures be preserved throughout the conversion process to maintain semantic consistency and interoperability. Once a CDEF for the AM CDM is available, this format should be used and or extracted from to create a data exchange format for a subset of data. Guidance for extracting micro data exchange formats from the CDEF will be provided in the future.

## How to reference the AM-CDM - Lead: Kareem Aggour

If you use the AM-CDM, we would appreciate citations to the following paper:

<a href="https://rdcu.be/dEl5G" target="_blank">A Common Data Dictionary and Common Data Model for Additive Manufacturing</a>, A. Kuan, K.S. Aggour, S. Li, _et al_., _Integrating Materials and Manufacturing Innovation_ vol. 13, no. 1, pp. 105-119, 2024.

```
@article{10.1007/s40192-024-00341-x, 
year = {2024}, 
title = {{A Common Data Dictionary and Common Data Model for Additive Manufacturing}}, 
author = {Kuan, Alexander and Aggour, Kareem S and Li, Shengyen and Lu, Yan and Mohr, Luke and Kitt, Alex and Macdonald, Hunter}, 
journal = {Integrating Materials and Manufacturing Innovation}, 
issn = {2193-9764}, 
doi = {10.1007/s40192-024-00341-x}, 
pages = {105--119}, 
number = {1}, 
volume = {13}
}
```

## CDM Inheritance - Lead: Alex Kitt
The AM CDM relies on class inheritance to enforce consistency. High-level classes (such as ManufacturingProcessStep) lay out common attributes and common structures to be inherited by domain specific subclasses. Critically, the high level classes establish the foundational relationships between classses. As an example, ManufacturingProcessStep includes the relationship to:
* the manufacturing equipment used in the process,
* the specification used to prescribe the process,
* the material inputs and material ouputs should.

Further, since ManufacturingProcessStep is a child of PlannedProcessStep, all ManufacturingProcessSteps include relationships to:
* the personnel who ran the process,
* the organization which ran the process.

Finally, through inheritance consistent common attributes are also enforced. For ManufacturingProcessStep this the timestamp when the process started and stopped. Subclasses are left to define domain specific attributes within the common structure defined by their parent classes. 

### Inheritance/Meta-Rules


## Who is using the AM CDM - Lead: Yan Lu

Current and Potential Users of AM-CDM include

ASTM International - Within ASTM, the Center of Excellence and the Consortium for Materials Data Standardization (CMDS) use AM-CDM for data collection and to populate their curated database with laser powder bed fusion process data from members.

America Makes Community - Several projects within the America Makes ecosystem have incorporated AM-CDM and AM-CDD (Common Data Dictionary):
  1. Colorado School of Mines – Cross Platform Consistency Project, Focused on mechanical properties of Inconel 718 (IN718) produced on PBF-LB systems, this project aims to Establish cross-platform processing pedigree strategies, Conduct tensile property testing, Characterize mechanical behavior of PBF-LB materials, Assess the impact of process parameters, machine features, and feedstock, Evaluate heat treatment effectsand Recommend test methods and data standards for qualification and future needs

  2. Boeing – GAMAT Project
The "Generation of Additive Material Allowables for Ti-6Al-4V" aims to create a standardized, statistical method for deriving bulk material properties using L-DED (Laser Powder Feed Directed Energy Deposition).

AFRL – HyperThought and Materials Center Integration (Presentation link)

NIST – AM Bench Data Curation AM Bench offers benchmark datasets and challenges for model validation and simulation. Data are rigorously measured, well-documented, and publicly archived.
(More Info)

Penn State / Maritime Industrial Base (MIB) - Exploring AM-CDM for managing data in the maritime industrial context.

University of Maryland (UMD)- Uses AM-CDM/CDD in collaboration with DEVCOM. (Project Report link)

CCAM (Commonwealth Center for Advanced Manufacturing) - Proposing a data integration framework using AM-CDM to enable interoperability between AM systems and MES/ERP platforms.

Hexagon - Applies AM-CDM across multiple projects for curating AM material data.

Authentise - Interested in developing a CDM-based adaptor to enable standardized communication with AM systems from various vendors.

3Degrees – Their TRACEAM platform references AM-CDM/CDD for managing AM data.

ORNL (Oak Ridge National Laboratory) - Exploring AM-CDM integration to link modeling and simulation tools with process data for improved model calibration.


## Future Work - Lead: Yan Lu

Future work for AM-CDM focuses on expanding its standardization, adoption, and technical maturity. A key priority is updating the current ASTM F3490 standard or initiating a new work item to further formalize AM-CDM. Alongside this, the development of compliance rules and derivation methods for standard data exchange formats—such as JSON—is essential to ensure interoperability and consistency across platforms. Demonstrating the practical value of AM-CDM through a strong test case—such as adopting it as the core model for the Consortium for Materials Data Standardization (CMDS) and America Makes—will help drive broader adoption. A series of whitepapers are also planned, including guidance on using AM-CDM for metadata graphs in AM data management, and on applying AM-CDM for federated AM data systems. Looking ahead, the development of AM-CDM 2.0 will align the model with the Industrial Ontologies Foundry (IOF), integrate ASTM standard data curation templates, MMPDS data formats, and NIAR’s “Workbench for Additive Materials,” and extend the schema to include metadata for computational models and simulations.

### Standardization
### Expansion to sub-domains (PBF, DED, specific TICs, etc.)
### How to get involved and/or provide feedback

## Publications

* K.S. Aggour. (2023), Evolution of Data Management and Common Data Models for Additive Manufacturing. _Additive Manufacturing Design and Applications_, ASM Handbook, vol. 24A, pp. 210-218. https://doi.org/10.31399/asm.hb.v24A.a0006963
* A. Kuan, K.S. Aggour, S. Li, _et al_. (2024), A Common Data Dictionary and Common Data Model for Additive Manufacturing. _Integrating Materials and Manufacturing Innovation_, vol. 13, pp. 105-119. https://doi.org/10.1007/s40192-024-00341-x, https://rdcu.be/dEl5G
* S. Li, Y. Lu, K.S. Aggour, _et al_. (2023), Enabling FAIR Data in Additive Manufacturing to Accelerate Industrialization. _Advanced Manufacturing Series (NIST AMS)_, National Institute of Standards and Technology, Gaithersburg, MD, https://doi.org/10.6028/NIST.AMS.500-1, https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=936454

## References - Lead: ALL

1. <a id="ref1">M. Wilkinson</a>, M. Dumontier, I. Aalbersberg, _et al_. (2016), The FAIR Guiding Principles for scientific data management and stewardship. _Scientific Data_ (3), article no. 160018. https://doi.org/10.1038/sdata.2016.18
2. <a id="ref2">ASTM F3490</a>, https://store.astm.org/f3490-21.html
3. <a id="ref3">K.S. Aggour</a>. (2023), Evolution of Data Management and Common Data Models for Additive Manufacturing. _Additive Manufacturing Design and Applications_, ASM Handbook, vol. 24A, pp. 210-218. https://doi.org/10.31399/asm.hb.v24A.a0006963
4. <a id="ref4">A. Kuan</a>, K.S. Aggour, S. Li, _et al_. (2024), A Common Data Dictionary and Common Data Model for Additive Manufacturing. _Integrating Materials and Manufacturing Innovation_, vol. 13, pp. 105-119. https://doi.org/10.1007/s40192-024-00341-x, https://rdcu.be/dEl5G
5. <a id="ref5">S. Li</a>, Y. Lu, K.S. Aggour, _et al_. (2023), Enabling FAIR Data in Additive Manufacturing to Accelerate Industrialization. _Advanced Manufacturing Series (NIST AMS)_, National Institute of Standards and Technology, Gaithersburg, MD, https://doi.org/10.6028/NIST.AMS.500-1, https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=936454
6. <a id="ref6">A. Crapo</a> and A. Moitra. (2013), Toward a Unified English-like Representation of Semantic Models, Data, and Graph Patterns for Subject Matter Experts. _International Journal of Semantic Computing_, vol. 7, no. 3, pp. 215-236. http://dx.doi.org/10.1142/S1793351X13500025
7. <a id="ref7">W3C Web Ontology Language</a>, https://www.w3.org/OWL/



*Move below to Developer Guide:*  

## Meta-Rules

* Subclasses must never add new attributes with an identical purpose as superclass attributes. When the subclass attribute is of a more specific type than the superclass attribute, the subclass should simply override the superclass attribute with the more specific type
* Each class which has at least one attribute is assigned a unique short hand name listed in shorthand.xlsx
* Each object property is prepended by the shorthand of the class it originates in
