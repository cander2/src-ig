### Introduction


### Dependencies
{% include dependency-table.xhtml %}

### Purpose
This Implementation Guide (IG) defines a FHIR-based standard for structuring **Requests for Information (RFIs)** issued by health authorities (e.g., FDA, EMA, PMDA) to market authorization holders (MAHs) during drug application assessments. It transitions RFIs from DOCX/PDF to FHIR-compliant JSON, enabling:
- Automated processing and categorization.
- Metadata-driven routing within MAHs.
- Querying prior responses.
- Interoperability across systems.

### Scope
In-scope
- Structured RFIs with questions/comments and metadata.
- Categorization: Administrative, Labeling, CMC, Clinical, Non-clinical (aligned with ICH CTD).
- Rich text (Markdown) and images (Attachment).
- Question-and-Answer response format.
- FHIR profiles and minimal extensions.
- Regulated medicinal products (prescription, Over the counter, Investigational and authorized, human and veterinary) and medical devices.

Out of scope:
- Non-RFI correspondence (e.g., approval letter).

### Solution Description 


### Use Case Examples


### Skillsets


### Target Audience
- Health authorities
- Market Authorization Holders (MAH) / Drug Manufacturer
- Health/pharma IT developers
- Contract Manufacturing Organization (CMO) 
- Clinical Research Organization (CRO)
- Healthcare institutions 
