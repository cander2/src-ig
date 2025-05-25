# FHIR Implementation Guide: Request for Information (RFI) Standard

## Introduction

### Purpose
This Implementation Guide (IG) defines a FHIR-based standard for structuring **Requests for Information (RFIs)** issued by health authorities (e.g., FDA, EMA, PMDA) to market authorization holders (MAHs) during drug application assessments. It transitions RFIs from DOCX/PDF to FHIR-compliant JSON, enabling:
- Automated processing and categorization.
- Metadata-driven routing within MAHs.
- Querying prior responses.
- Interoperability across systems.

### Scope
- Structured RFIs with questions/comments and metadata.
- Categorization: Administrative, Labeling, CMC, Clinical, Non-clinical (aligned with ICH CTD).
- Rich text (Markdown) and images (Attachment/Media).
- Question-and-Answer response format.
- FHIR profiles and minimal extensions.

Out of scope:
- Non-RFI communications.
- Detailed security (use FHIR standards).

### Audience
- Health authorities.
- MAHs.
- Health IT developers.
- Standards organizations (e.g., HL7, ICH).

## Navigation
- [Use Case](use-case.html)
- [Resource Mapping](resource-mapping.html)
- [Profiles](profiles.html)
- [Value Sets](value-sets.html)
- [Examples](examples.html)
- [Implementation](implementation.html)