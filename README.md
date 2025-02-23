# AM-CDM
Additive Manufacturing - Common Data Model

## Meta-Rules
* Subclasses must never add new attributes with an identical purpose as superclass attributes. When the subclass attribute is of a more specific type than the superclass attribute, the subclass should simply override the superclass attribute with the more specific type
* Each class which has at least one attribute is assigned a unique short hand name listed in shorthand.xlsx
* Each object property is prepended by the shorthand of the class it originates in