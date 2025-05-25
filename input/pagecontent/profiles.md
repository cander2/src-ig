# Profiles

## RFICommunication
- **Base**: [Communication](http://hl7.org/fhir/R5/communication.html)
- **Constraints**:
  - `status`: Mandatory.
  - `sender`: Mandatory (`Organization`).
  - `recipient`: Mandatory (`Organization`/`Practitioner`).
  - `topic`: Mandatory (`MedicinalProductDefinition`).
- **Extensions**:
  - [rfi-due-date](StructureDefinition-rfi-due-date.html): `dateTime`.
  - [rfi-priority](StructureDefinition-rfi-priority.html): `code`.

## RFIQuestionnaire
- **Base**: [Questionnaire](http://hl7.org/fhir/R5/questionnaire.html)
- **Constraints**:
  - `item.text`: `markdown`.
  - `item.type`: `group`, `display`, `attachment`.
  - `item.code`: Binds to [ValueSet-rfi-category-subcategory](ValueSet-rfi-category-subcategory.html).
- **Extension**:
  - [rfi-question-id](StructureDefinition-rfi-question-id.html): `string`.

## RFIQuestionnaireResponse
- **Base**: [QuestionnaireResponse](http://hl7.org/fhir/R5/questionnaireresponse.html)
- **Constraints**:
  - `item.answer.value[x]`: `valueString` (markdown), `valueAttachment`.

## RFIMedia
- **Base**: [Media](http://hl7.org/fhir/R5/media.html)
- **Constraints**:
  - `content.contentType`: `image/png`, `image/jpeg`.