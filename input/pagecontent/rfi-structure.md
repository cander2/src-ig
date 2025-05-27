## Core Resources
- **Communication**: RFI metadata (issuer, recipient, application).
- **Questionnaire**: Questions with rich text (Markdown) and images (Attachment).
- **QuestionnaireResponse**: Responses with text and images.
- **Bundle**: Packages RFI/response resources.

## RFI Structure
- **Bundle** (`type: collection`):
  - Contains `Communication`, `Questionnaire`.
- **Communication**:
  - `status`: `active` (issued).
  - `sender`: `Organization` (e.g., FDA).
  - `recipient`: `Organization`/`Practitioner` (MAH).
  - `topic`: `RegulatedAuthorization`.
  - `payload`: References `Questionnaire`.
  - Extensions: [rfi-due-date](StructureDefinition-rfi-due-date.html), [rfi-priority](StructureDefinition-rfi-priority.html).
- **Questionnaire**:
  - `item.text`: Markdown.
  - `item.type`: `group` (mixed content), `display` (text), `attachment` (images).
  - `item.code`: [ValueSet-rfi-category-subcategory](ValueSet-rfi-category-subcategory.html).
  - Extension: [rfi-question-id](StructureDefinition-rfi-question-id.html).

## Response Structure
- **Bundle** (`type: collection`):
  - Contains `QuestionnaireResponse`.
- **QuestionnaireResponse**:
  - `questionnaire`: Links to `Questionnaire`.
  - `item.answer`: `valueString` (Markdown), `valueAttachment` (images).