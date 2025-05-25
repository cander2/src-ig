# RFI FHIR Implementation Guide

This repository contains a FHIR Implementation Guide (IG) for standardizing **Requests for Information (RFIs)** from health authorities (e.g., FDA, EMA, PMDA) to market authorization holders (MAHs). The IG defines a FHIR-based structure for RFIs, supporting rich text (Markdown), images (Attachment/Media), and categorization aligned with ICH CTD headings.

https://build.fhir.org/ig/cander2/rfi-ig

## Structure
- `input/pagecontent/`: Markdown files for narrative content.
- `input/resources/`: FHIR resource definitions (ValueSets, StructureDefinitions, Extensions).
- `input/examples/`: Example RFI and response Bundles.
- `ig.yaml`: Configuration for the FHIR IG Publisher.

