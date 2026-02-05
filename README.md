# Additive Manufacturing-Common Data Model (AM-CDM) Introduction

## What is the AM-CDM
Additive Manufacturing (AM) relies heavily on data describing the input materials, processing parameters, post-processing steps, and inspection results to be successful, just to name a few. Despite its potential, AM remains a developing field, requiring collaboration among academia, corporations, national labs, professional societies, and more. These partnerships depend on extensive data sharing across the AM ecosystem, including material vendors, equipment manufacturers, part suppliers, and customers. However, effective data sharing is challenging because most organizations use their own internal definitions (vocabulary) and representations (structure) to manage their data, making data exchange between parties a challenge.

The Additive Manufacturing-Common Data Model (AM-CDM) was developed to address this challenge. The AM-CDM is written in the Semantic Application Design Language (SADL) [[6]](#ref6).

## What is SADL
SADL is both a design language and an Eclipse plug-in created to simplify data model development. SADL uses a formal, English-like syntax and grammar, enabling users to author data models that can be automatically converted into the Web Ontology Language (OWL), the defacto W3C standard for semantic modeling [[7]](#ref7). SADL was developed specifically to make data modeling more accessible to non-semantic domain experts, allowing them to read and understand these models with ease. SADL's intuitive design makes it straightforward for domain experts such as engineers and materials scientists to collaborate with computer scientists to rapidly develop data models, without requiring those domain experts to become proficient in semantic modeling.

Each AM-CDM SADL file contains a collection of classes, which are comprised of zero to many properties. These properties can be of a primitive data type, such as string, int, double, and more, or can be of a complex type, and be defined by a class name. In this way, classes can be linked to each other through properties, creating a potentially complex network of relationships. The cardinality of each property is also defined, as each property is specified to be single-valued (‘with a single value of type’) or multi-valued (‘with values of type’).

Each class may also have a type, allowing for the inheritance of properties between classes. A simple example of an extract of SADL is shown below.

# SADL EXAMPLE
<img width="50%" alt="SADL example" src="https://github.com/user-attachments/assets/21947534-53a7-48fe-8d01-4ce4ad640e25" />

## CDD vs. CDM vs. CDEF
Today, many organizations are adopting the FAIR Guiding Principles [[1]](#ref1) to make their data Findable, Accessible, Interoperable, and Reusable (FAIR). Interoperability, a key FAIR principle, is essential for seamless data exchange and requires community-driven vocabulary standards. To address this need, the ASTM F42.08 Subcommittee on Data developed the F3490-21 Common Data Dictionary (CDD) standard, to develop a common vocabulary around key terms in the AM space [[2]](#ref2). While CDDs standardize how humans describe data, they rely on human interpretation of relationships, limiting machine-to-machine communication. This lack of standardized, machine-readable data relationships prevents automated data exchange between systems.

To achieve seamless data interoperability by systems, AM developers need a common data representation. A Common Data Model (CDM) solves this by defining the logical structure and relationships of the terms in the CDD [[3]](#ref3). An effective CDM must be both human-readable, enabling users to understand and utilize the data, and machine-computable, allowing systems to understand and process data automatically. The CDM is not a data schema, so organizations adopting it do not need to change their internal data storage systems. Instead, they can simply map their internal data representations to the CDM for external data sharing. In this way, the CDM acts as a "lingua franca," allowing systems to maintain their internal data structures while using a shared language for communication across boundaries [[4]](#ref4). Alternately, the CDM can be adopted as a data model for new data systems, if users so desire.

While the CDM enables humans and machines to communicate about AM data, a key challenge remains--the format used for data exchange. A Common Data Exchange Format (CDEF), aligned with the CDM's structure, enables data exchange in popular file formats such as XML (eXtensible Markup Language) or JSON (JavaScript Object Notation). This eliminates the need for creating individual mappings between each party wishing to exchange AM data [[5]](#ref5). A CDEF for AM data is planned to be produced in the near future. Information about how to access this CDEF will be added to this repository when it is available.

The figure below shows an example snippet of three attributes in an AM-CDD, how they can be modeled in two classes in the AM-CDM, and how that can be turned into a JSON CDEF structure using the exact syntax and structure of the AM-CDM. Overall, the CDD standardizes the AM vocabulary for human use, the CDM structures that vocabulary to enable data interoperability by machines, and CDEFs enable machines to physically exchange data based on the structure of the CDM.

<img width="90%" alt="CDD-CDM-CDEF example" src="https://github.com/user-attachments/assets/24d24507-9bfe-4f85-ad39-449f061d056e"/>

Figure 2 - Three example entries from the AM-CDD, modeled in two classes of the AM-CDM, and turned into a JSON CDEF populated with dummy instance data.

## AM-CDM Scope
The AM-CDM is currently AM process-agnostic, meaning it does not include AM domain-specific information, such as data related specifically to Metallic Laser Powder Bed Fusion or Metallic Wire-Arc Directed Energy Deposition. Future efforts can focus on extensions to the AM-CDM for these specific domains, relying on the domain Subject Matter Experts (SMEs) to define and organize the data of that domain. For instance, data models representing specific destructive testing types (e.g. tensile testing) or specific thermal treatments (e.g. stress relief) could be constructed that build on the AM-CDM. Specific, non-AM concepts (e.g. organization, personnel, system) have been included in the AM-CDM in effort to create a holistic picture of the AM data pedigree.

## AM-CDM Structure
*insert some graphics of the AM-CDM to help visualize the organization and structure*
*focus on most important classes*


## How to use the AM-CDM
The Common Data Model can be adopted into a variety of situations where the Additive Manufacturing data is being collected in accordance with FAIR principles (Findable, Accessible, Interoperable, and Repeatable).  Some example users include powder manufacturers, AM system OEMs, and coupon testing houses.  While there are certainly use cases that will depend on and utilize a full implementation of the data model, each of the examples above may only be interested in a subset of data.  The benefits of each group adopting the CDM are twofold.  First, they ensure their data internally follows best practices.  Second, they can communicate that data to each other or a larger project.
When referencing the SADL files, Classes are sets of things (or data object types), such as PlannedProcessStep in the below diagram, and Properties are attributes or relationships of those things.  Properties therefore generally connect the data objects.  There are several considerations for individuals to adopt all or a portion of the CDM in a way that adds value to the dataset:

### Required Properties/Classes
There are several classes in the CDM .sadl files that contain minimum required properties to establish the data object, usually defined as a name or ID.  These properties must be both unique and common across all implementations of the dataset.  In many cases, these unique IDs are essential in collating datasets gathered from multiple sources.  For example, a test house communicating the results of testing is not necessarily aware of the specimenProcessHistory, but including the specimenID attribute will allow for the Specimen class to link up with the ProcessHistory class.
Other required properties could be ones that establish the relationship.  Their required status depends on the use case and the role of the person or organization that is representing the data.  For example, if the dataset contains both Specimen and ProcessHistory classes, the link that connects them is the specimenProcessHistory property in the Specimen class.  This link is established by referencing the specimenID in the previous example, but ultimately it is the property that creates a pedigree between the data objects.  In this example the classes being linked are considered neighbors.
Finally, there are cases where an entire class, along with ID and relationship properties, is required to connect two non-neighboring classes.  If both Specimen and PowderStock classes are being used to communicate data, the link between them is the ProcessHistory class.  Like the first example above, an ID can be utilized on each of these objects as a reference to collate the dataset.  However, as in the second example, if the person or organization is responsible for collating the dataset then the specimenProcessHistory is also required to link the Specimen.  The link between ProcessHistory and PowderStock is a bit more complicated and follows the diagram in Figure 1.

<img width="90%" alt="AM-CDM use case" src="https://github.com/user-attachments/assets/b2d95a78-a48d-4a17-b100-86cc27978369" />

Figure 3 - CDM use case linking a PowderStock class object to a Specimen class object.  Red boxes indicate parent classes and light blue boxes indicate required name/ID properties.

### Parent Classes
Many elements in the CDM are defined as subclasses (ie., ManufacturingProcessStep is a type of PlannedProcessStep).  In these cases, the required ID/name properties should be in the parent class.  However, reference properties can exist in either the parent or child.  Child classes inherit all properties from the parent and replaces the parent in the data model when utilized.  In the example above, the PlannedProcessStep class is not required since ManufacturingProcessStep is being used instead.  

## How to Derive Data Exchange Formats from the AM-CDM
Depending on the target database technology, it may be necessary to convert the SADL specification into alternative formats such as XML or JSON. Preliminary parsing routines implemented in Python are available within the Jupyter notebooks located in the notebooks directory. For certain technologies—such as OWL or JSON-LD—that require more advanced semantic relationships, additional modeling may be needed. Nevertheless, it is strongly advised that the original attribute definitions and core class structures be preserved throughout the conversion process to maintain semantic consistency and interoperability. Once a CDEF for the AM-CDM is available, this format should be used and or extracted from to create a data exchange format for a subset of data. Guidance for extracting micro data exchange formats from the CDEF will be provided in the future.

## AM-CDM Inheritance
The AM-CDM relies on class inheritance to enforce consistency and reduce redundant concepts. High-level classes (such as ManufacturingProcessStep) lay out common attributes and common structures to be inherited by domain-specific subclasses. Critically, the high level classes establish the foundational relationships between classses. As an example, ManufacturingProcessStep includes the relationship to:
* the manufacturing equipment used in the process,
* the material inputs and material ouputs.

Further, since ManufacturingProcessStep is a child of PlannedProcessStep, all ManufacturingProcessSteps include relationships to:
* the personnel who ran the process,
* the organization which ran the process.
* the specification used to prescribe the process.

One special circumstance of note in the SADL syntax is the use of "only has values of". For example, mfgProcessMachine of Build *only has values* of type AMSystem. Here, the attributes associated within AMSystem append (as opposed to overwritte) to the attributes within mfgProcessMachine, but only in the case of a ManufacturingProcessStep of type Build. On the contrary, it would not make sense for the attributes of an AMSystem to be applicable to other types of mfgProcessMachine, such as in the case of a thermal treatment process where the mfgProcessMachine of ManufacturingProcessStep MaterialHT "only has values of" HTSystem.

## Who is using the AM-CDM

Current known users of AM-CDM include;

ASTM International - Within ASTM, <a href="https://amcoe.org/" target="_blank">the Center of Excellence</a> and <a href="https://amcoe.org/" target="_blank">the Consortium for Materials Data Standardization (CMDS)</a> are aligning their database that is for curating Laser Powder Bed Fusion data for its members to the AM-CDM.

America Makes Community - Several projects within the America Makes community have incorporated AM-CDM and AM-CDD:
  1. CORE Data Repository - A project led by The Penn State Applied Research Lab and supported by Edison Welding Institute (EWI) has adopted the AM-CDM as the foundation for the data model that will be employed by the CORE Project Data Repository. A proof-of-concept has been completed and remains to be implemented on CORE. This project has also produced an AM-CDM compliant data template that is currently available on the CORE Data Repository to America Makes members: <a href="https://core.americamakes.us/deliverables/overview/cd6ef85c-e9a6-4ac3-8fa9-005d7d78d040" target="_blank">CORE Data Template Available Here</a>
  2. Colorado School of Mines – <a href="https://www.americamakes.us/wp-content/uploads/2023/09/PS-5546.pdf" target="_blank">Cross Platform Consistency Project</a> - Focused on curating mechanical properties of Inconel 718 (IN718) produced on PBF-LB systems. This project aims to establish cross-platform processing pedigree strategies, conduct tensile property testing, characterize mechanical behavior of PBF-LB materials, assess the impact of process parameters, machine features, and feedstock, evaluate heat treatment effects, and recommend test methods and data standards for qualification.
*How is CSOM using the AM-CDM?*
  3. Boeing – <a href="https://www.americamakes.us/wp-content/uploads/2023/02/PS-GAMAT-5534.1.30.23.FINAL_.pdf" target="_blank">GAMAT Project</a> - The "Generation of Additive Material Allowables for Ti-6Al-4V" aims to create a standardized, statistical method for deriving bulk material properties using L-DED (Laser Powder Feed Directed Energy Deposition). GAMAT is using Hexagon's Material Center softaware to capture AM process data, which has been mapped to the AM-CDM.

AFRL – <a href="https://www.youtube.com/watch?v=Zur1yX-t2ow" target="_blank">HyperThought</a> is integrating with Materials Center and is employing the AM-CDM 

NIST – <a href="https://ambench2022.nist.gov/" target="_blank">AM Bench</a> - A data curation activity that is leveraging the AM-CDM which offers benchmark datasets and challenges for model validation and simulation. Data are rigorously measured, well-documented, and publicly archived.

<a href="https://www.secnav.navy.mil/rda/mib/Pages/default.aspx", target="_blank">The Maritime Industrial Base (MIB)</a> & <a href="https://www.arl.psu.edu/" target="_blank">The Penn State Applied Research Lab</a> - Are adopting the AM-CDM as the foundation for the MIB Ontolgoy for Advanced Manufacturing (MIBO-ADVM) that will be utilized to connect Advanced Manufacturing data accross the MIB.

University of Maryland (UMD) - Uses AM-CDM/CDD in a collaboration with DEVCOM: <a href="https://apps.dtic.mil/sti/trecms/pdf/AD1156858.pdf" target="_blank">Data Management and Data Curation for Additive Manufacturing: Annual Report</a>. 

<a href="https://ccam-va.com/" target="_blank">CCAM</a> (Commonwealth Center for Advanced Manufacturing) - Is proposing a data integration framework using AM-CDM to enable interoperability between AM systems and MES/ERP platforms.

<a href="https://hexagon.com/" target="_blank">Hexagon</a> - Applies the AM-CDM in their software for curating AM material data across multiple projects.

<a href="https://www.authentise.com/" target="_blank">Authentise</a> - Interested in developing a CDM-based adaptor to enable standardized communication with AM systems from various vendors.

<a href="https://www.3degreescompany.com/" target="_blank">3Degrees</a> – Their TRACEAM platform references AM-CDM/CDD for managing AM data.

<a href="https://www.ornl.gov/technology/90000193" target="_blank">ORNL (Oak Ridge National Laboratory)</a> - Exploring AM-CDM integration to link modeling and simulation tools with process data for improved model calibration.


## Future Work

Future work for the AM-CDM focuses on expanding its standardization, adoption, and technical maturity. Key priorities will include; (1) updating the current <a href="https://store.astm.org/f3490-21.html" target="_blank">ASTM F3490</a> standard for consistency with the AM-CDM and to reflect improved understanding of data concepts and (2) initiating a new work item to further formalize the AM-CDM. Alongside this, the development of compliance rules and derivation methods for standard data exchange formats (such as JSON) is essential to ensure interoperability between data platforms. Demonstrating the practical value of AM-CDM through strong test cases, such as adopting it as the core model for <a href="https://amcoe.org/" target="_blank">the Consortium for Materials Data Standardization (CMDS)</a>, <a href="https://www.americamakes.us/projects/5566-001-proliferation-of-additive-manufacturing-material-datasets/" target="_blank" >the America Makes CORE Data Repository</a>, and within the <a href="https://www.secnav.navy.mil/rda/mib/Pages/default.aspx", target="_blank">MIB</a> — will help drive broader adoption. A series of whitepapers are also planned, including guidance on using AM-CDM for metadata graphs in AM data management, and on applying AM-CDM for federated AM data systems. Looking ahead, the development of AM-CDM 2.0 will align the model with <a href="https://oagi.org/pages/industrial-ontologies" target="_blank">the Industrial Ontologies Foundry (IOF)</a>, integrate standard data curation templates, and extend the data model to other related domains and sub-domains, such as Powder Bed Fusion, Directed Energy Deposition, and specific testing types.

## How to Get Involved, Provide Feedback, or Share Record of Use

This project is part of a growing open-source ecosystem dedicated to advancing digital manufacturing. Contributions of all kinds — code, documentation, testing, or ideas — are welcome! Our only rule: be kind, be curious, and help us make this better for everyone. If you’d like to get started see our [contributions guide](./CONTRIBUTING.md)

Together, we can build something meaningful.
 

## Publications

* K.S. Aggour. (2023), Evolution of Data Management and Common Data Models for Additive Manufacturing. _Additive Manufacturing Design and Applications_, ASM Handbook, vol. 24A, pp. 210-218. https://doi.org/10.31399/asm.hb.v24A.a0006963
* A. Kuan, K.S. Aggour, S. Li, _et al_. (2024), A Common Data Dictionary and Common Data Model for Additive Manufacturing. _Integrating Materials and Manufacturing Innovation_, vol. 13, pp. 105-119. https://doi.org/10.1007/s40192-024-00341-x, https://rdcu.be/dEl5G
* S. Li, Y. Lu, K.S. Aggour, _et al_. (2023), Enabling FAIR Data in Additive Manufacturing to Accelerate Industrialization. _Advanced Manufacturing Series (NIST AMS)_, National Institute of Standards and Technology, Gaithersburg, MD, https://doi.org/10.6028/NIST.AMS.500-1, https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=936454

## References

1. <a id="ref1">M. Wilkinson</a>, M. Dumontier, I. Aalbersberg, _et al_. (2016), The FAIR Guiding Principles for scientific data management and stewardship. _Scientific Data_ (3), article no. 160018. https://doi.org/10.1038/sdata.2016.18
2. <a id="ref2">ASTM F3490</a>, https://store.astm.org/f3490-21.html
3. <a id="ref3">K.S. Aggour</a>. (2023), Evolution of Data Management and Common Data Models for Additive Manufacturing. _Additive Manufacturing Design and Applications_, ASM Handbook, vol. 24A, pp. 210-218. https://doi.org/10.31399/asm.hb.v24A.a0006963
4. <a id="ref4">A. Kuan</a>, K.S. Aggour, S. Li, _et al_. (2024), A Common Data Dictionary and Common Data Model for Additive Manufacturing. _Integrating Materials and Manufacturing Innovation_, vol. 13, pp. 105-119. https://doi.org/10.1007/s40192-024-00341-x, https://rdcu.be/dEl5G
5. <a id="ref5">S. Li</a>, Y. Lu, K.S. Aggour, _et al_. (2023), Enabling FAIR Data in Additive Manufacturing to Accelerate Industrialization. _Advanced Manufacturing Series (NIST AMS)_, National Institute of Standards and Technology, Gaithersburg, MD, https://doi.org/10.6028/NIST.AMS.500-1, https://tsapps.nist.gov/publication/get_pdf.cfm?pub_id=936454
6. <a id="ref6">A. Crapo</a> and A. Moitra. (2013), Toward a Unified English-like Representation of Semantic Models, Data, and Graph Patterns for Subject Matter Experts. _International Journal of Semantic Computing_, vol. 7, no. 3, pp. 215-236. http://dx.doi.org/10.1142/S1793351X13500025
7. <a id="ref7">W3C Web Ontology Language</a>, https://www.w3.org/OWL/

## How to reference the AM-CDM

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
