# RFI FHIR Implementation Guide

This repository contains a FHIR Implementation Guide (IG) for standardizing **Requests for Information (RFIs)** from health authorities (e.g., FDA, EMA, PMDA) to market authorization holders (MAHs). The IG defines a FHIR-based structure for RFIs, supporting rich text (Markdown), images (Attachment/Media), and categorization aligned with ICH CTD headings.

## Structure
- `input/pagecontent/`: Markdown files for narrative content.
- `input/resources/`: FHIR resource definitions (ValueSets, StructureDefinitions, Extensions).
- `input/examples/`: Example RFI and response Bundles.
- `ig.yaml`: Configuration for the FHIR IG Publisher.

## Building the IG
1. **Prerequisites**:
   - Java 8+.
   - FHIR IG Publisher JAR ([download](https://confluence.hl7.org/display/FHIR/IG+Publisher+Documentation)).
2. **Run Locally**:
   ```bash
   java -jar publisher.jar -ig ig.yaml
   ```
   Output in `output/`.
3. **Run via GitHub Actions**:
   - `.github/workflows/publish-ig.yml` builds on push to `main`.
   - View at GitHub Pages.

## Testing
- Validate examples with HAPI FHIR.
- Preview with Jekyll:
  ```bash
  cd output
  jekyll serve
  ```

## Contributing
- Submit issues or pull requests.
- Contact [your-email@hl7.org] for collaboration.

## License
CC0-1.0