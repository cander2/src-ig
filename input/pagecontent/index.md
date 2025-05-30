### Introduction
This Implementation Guide (IG) introduces a standard for structuring key regulatory correspondence between health authorities and mMarket Authroization Holders. This includes: list of questions (also known as Requests for Information or RFI), response to list of qestions, and regulatory decision letters. 

### Background
List of questions are a critical aspect of the regulatory assesment process for medicinal products and medical devices. Health authorities, such as the FDA, EMA, and PMDA, issue Lists of Questions to market authorization holders to seek clarification, request additional data, or raies issues. 

Traditionally, List of Questions are exchanged as unstructured DOCX or PDF documents, which pose significant challenges: 
- **Manual processing**: Companies operating globally can receive thousands of List of Questions from around the world per year. It is common for many List of Questions to be received on the same day. Since this is a largely manual and effort intensive process, companies can only handle a limited number of List of Questions at a time. They must also limit the number of simultaneous filings to health authorities to ensure they do not get overwhelmed by incoming List of Questions.
- **Manual categorization**: List of Questions are sometimes over 200 pages and can contain tens or hundreds of questions. Each question can be categorized by subject area (I.e., administrative, labeling, safety, clinical, non-clinical, or manufacturing/quality). Each category has additional layers of sub-category. After categorization, the relevant questions are routed to the appropriate department or subject matter expert to develop a response. Categorization is time and effort intensive if done manually and can be prone to error if automated.
- **Redundancy**: International Health authorities sometimes ask the same or similar questions. Since the RFI and the List of Questions response are unstructured (I.e., DOCX or PDF), it can be difficult to index all incoming questions and the associated response. Which in turn makes it difficult to identify if a particular question has been asked and answered before. Companies therefore spend unnecessary extra effort recreating the same or similar responses.

These inefficiencies increase operational costs, and hinder a company’s ability to file more simultaneous regulatory applications at scale. This results in delayed time to gain regulatory approval or to implement global regulatory changes.

By replacing DOCX/PDF formats with FHIR-compliant JSON, this standard enables:
- **Automation**: Structured JSON enables systems to automatically parse questions, extract metadata, and use metadata-driven routing to send whole RFIs, or subsets of questions, to the appropriate teams within MAHs, reducing manual effort. Generative AI can also leverage this structured data to generate a first draft of an RFI response.
- **Interoperability**: FHIR ensures compatibility with global IT systems, supporting a harmonized international approach, and integration with existing platforms.
- **Traceability**: Linking RFIs (`Communication`) to responses (`QuestionnaireResponse`) via FHIR references allows MAHs to query historical data, improving response consistency and efficiency.
- **Speed**: companies will be able to file more simultaneous applications since this automated process will be faster and require significantly less effort.

### Scope
- Questions from regulators (e.g., List of Questions, List of Issue, Rquest for Information) and the associated metadata.
- Market authorization holder's response to questions
- Regulatory decision letters and associated metadata
- Question categorization and sub-categorization across regulatory domains: Administrative, Labeling, Quality, Clinical, Non-clinical, and Safety.
- Support for rich text (Markdown) and embedded images.
- Regulated medicinal products and medical devices.

### Audience
This IG is designed for:
- **Health Authorities**: Regulatory bodies (e.g., FDA, EMA, PMDA) issuing List of Questions.
- **Market Authorization Holders (MAHs) / Drug Manufacturers**: Entities responding to RFIs.
- **Health/Pharma IT Developers**: Building systems to author, process, and manage List of Questions content.
- **Contract Manufacturing Organizations (CMOs)**: Supporting manufacturing-related List of Questions responses for themselves or clients.
- **Clinical Research Organizations (CROs)**: Supporting clinical related List of Questions responses for themselves or clients.
- **Healthcare Institutions**: Responding to List of Questions related to clinical trial applications/Investigational New Drug Applications (IND).

### Solution Description
The List of Questions IG leverages FHIR R5 to create a standardized, interoperable framework for List of Questions workflows, addressing the inefficiencies of traditional document-based processes. The solution is built on a core set of FHIR resources, profiles, and extensions, designed to support structured data exchange while maintaining flexibility for diverse regulatory use cases.

INSERT GRAPHIC OF QUESTIONNAIRE 

INSERT GRAPHIC OF QUESTIONNAIRE RESPONSE

INSERT GRAPHIC OF DECISION LETTER

### Key Components
- **FHIR Resources**:
  - **Communication**: Captures List of Questions metadata, including issuer (`sender`), recipient (`recipient`), and drug/device application context (`basedOn` referencing `MedicinalProductDefinition`).
  - **Questionnaire**: Represents List of Questions questions, supporting rich text (Markdown) and images (via `Attachment`) in a structured format.
  - **QuestionnaireResponse**: Encodes MAH responses, allowing text and image attachments in a question-and-answer format.
  - **Bundle**: Packages `Communication` and `Questionnaire` for List of Questions issuance, and `QuestionnaireResponse` for responses, ensuring a cohesive transaction.

- **FHIR Profiles**:
  - `RFICommunication`: Constrains `Communication` to enforce mandatory fields (e.g., `status`, `sender`) and link to `MedicinalProductDefinition`.
  - `RFIQuestionnaire`: Ensures `Questionnaire` items use Markdown for text and support `group`, `display`, or `attachment` types.
  - `RFIQuestionnaireResponse`: Allows `QuestionnaireResponse` answers to include Markdown text or `Attachment` images.

- **Extensions**:
  - `rfi-due-date`: Adds a deadline (`dateTime`) to `Communication`.
  - `rfi-priority`: Assigns priority levels (`high`, `medium`, `low`) to List of Questions.
  - `rfi-question-id`: Provides a unique identifier for `Questionnaire` items.

- **Value Sets**:
  - `RFICategoryAndSubcategory`: Aligns List of Questions categorization with ICH CTD headings (e.g., Administrative, CMC) and sub-categories (e.g., DrugSubstance, Bioequivalence).

### Implementation
The IG provides detailed guidance on implementing List of Questions workflows, including:
- **Data Exchange**: Use FHIR RESTful APIs to transmit List of Questions `Bundle` resources between health authorities and MAHs.
- **UI Rendering**: Render Markdown text and `Attachment` images in user interfaces using libraries like `marked` (JavaScript) or `python-markdown`.
- **Validation**: Validate resources against profiles using tools like HAPI FHIR or the FHIR Validator.
- **Performance**: Support pagination for large `Bundle` transactions to optimize processing.

For detailed technical specifications, see [Resource Mapping](resource-mapping.html), [Profiles](profiles.html), and [Examples](examples.html).
