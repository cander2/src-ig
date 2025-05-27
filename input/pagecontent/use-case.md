### Problem Statement
Health authorities issue RFIs as DOCX/PDF documents, requiring MAHs to manually:
- Extract questions and metadata.
- Categorize questions.
- Route to teams.
- Check prior responses.

This is error-prone and inefficient.

### Solution
A FHIR-based RFI standard offers:
- **JSON Structure**: Automates parsing.
- **Metadata**: Identifies issuer, application, recipient, categories.
- **Rich Content**: Markdown for text, Attachment for images.
- **Interoperability**: FHIR-compatible.
- **Tracking**: Links responses for querying.

### Workflow
1. Health authority issues RFI as a FHIR Bundle (`Communication`, `Questionnaire`).
2. MAH parses Bundle, renders in UI, routes, and categorizes.
3. MAH responds with `QuestionnaireResponse` (text, images).
4. Authority processes response.
5. MAH queries historical RFIs/responses.