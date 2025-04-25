# AM-CDM Documentation for the General AM Practitioner

Additive Manufacturing - Common Data Model

## *Documentation Development Notes (delete later)*  

*Objective: Create 3 versions of documentation for different CDM users/viewpoints:*  
*1.	General AM Practitioner (this README document) – Peter to lead, people to volunteer for writing sections*  
*2.	Developer Guide (readme proper) - Ben to lead this activity*  
*3.	Standard – hold for later (express?)*  

*Use CDM Chapter from ASM Handbook as a good primary reference for information*
*https://doi.org/10.31399/asm.hb.v24A.a0006963*

## What is the AM CDM

### What is it for/Why was it created
### Where did it come from
### CDD -> ASTM F3490
### CDD Progression to CDM
### Who created it

## What is the scope of the AM CDM

(Process agnostic AM - not all concepts are AM specific, but were deemed necessary to include..)

## How to use the AM CDM

### What is the use case for a general AM practitioner?
### How a non-data person may apply the CDM in their organization, even if not implemented in a database, etc.
### Minimum viable data, enable data pedigree via data connectivity

## What is SADL

### SADL File Structure
### How to use SADL Files
### Tips for Human consumption of SADL Files

## How to reference the AM-CDM

### Citing
### Versioning

## CDM Structure

### Inheritance/Meta-Rules

## Who is using the AM CDM

### Current users
### Examples of use
### How to submit record of use

## Future Work

### Standardization
### Expansion to sub-domains (PBF, DED, specific TICs, etc.)
### How to get involved and/or provide feedback

## References

1. ASTM F3490
2. https://doi.org/10.31399/asm.hb.v24A.a0006963



*Move below to Developer Guide:*  

## Meta-Rules

* Subclasses must never add new attributes with an identical purpose as superclass attributes. When the subclass attribute is of a more specific type than the superclass attribute, the subclass should simply override the superclass attribute with the more specific type
* Each class which has at least one attribute is assigned a unique short hand name listed in shorthand.xlsx
* Each object property is prepended by the shorthand of the class it originates in
