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
*pull info from Kareem's ASM Handbook Chapter*

### What is it for/Why was it created (motivation)
### Where did it come from
### CDD -> ASTM F3490
### CDD Progression to CDM
### Who created it
### How is CDM different from a data exchange format


## What is the scope of the AM CDM - Lead: Peter Coutts

*(Process agnostic AM - not all concepts are AM specific, but were deemed necessary to include..)*  


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

### SADL File Structure
### How to use SADL Files
### Tips for Human consumption of SADL Files


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

1. ASTM F3490
2. https://doi.org/10.31399/asm.hb.v24A.a0006963
3. https://rdcu.be/dEl5G
4. https://www.nist.gov/publications/enabling-fair-data-additive-manufacturing-accelerate-industrialization



*Move below to Developer Guide:*  

## Meta-Rules

* Subclasses must never add new attributes with an identical purpose as superclass attributes. When the subclass attribute is of a more specific type than the superclass attribute, the subclass should simply override the superclass attribute with the more specific type
* Each class which has at least one attribute is assigned a unique short hand name listed in shorthand.xlsx
* Each object property is prepended by the shorthand of the class it originates in
