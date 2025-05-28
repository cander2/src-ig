## Introduction
This Implementation Guide (IG) introduces a standard for structuring Requests for Information (RFIs) issued by health authorities to market authorization holders during assessment of regulatory applications related to medicinal products (prescription, over-the-counter, investigational, and authorized, for human and veterinary use) and medical devices.

### Background
RFIs are a critical component of the regulatory review process for medicinal products and medical devices. Health authorities, such as the FDA, EMA, and PMDA, issue RFIs to market authorization holders to seek clarification, additional data, or specific details during drug or device application assessments. 

Traditionally, RFIs are exchanged as unstructured DOCX or PDF documents, which pose significant challenges: 
- **Manual processing**: Companies operating globally can receive thousands of RFIs from around the world per year. It is common for many RFIs to be received on the same day. Since this is a largely manual and effort intensive process, companies can only handle a limited number of RFIs at a time. They must also limit the number of simultaneous filings to health authorities to ensure they do not get overwhelmed by incoming RFIs.
- **Manual categorization**: RFIs are sometimes over 200 pages and can contain tens or hundreds of questions. Each question can be categorized by subject area (I.e., administrative, labeling, safety, clinical, non-clinical, or manufacturing/quality). Each category has additional layers of sub-category. After categorization, the relevant questions are routed to the appropriate department or subject matter expert to develop a response. Categorization is time and effort intensive if done manually and can be prone to error if automated.
- **Redundancy**: International Health authorities sometimes ask the same or similar questions. Since the RFI and the RFI response are unstructured (I.e., DOCX or PDF), it can be difficult to index all incoming questions and the associated response. Which in turn makes it difficult to identify if a particular question has been asked and answered before. Companies therefore spend unnecessary extra effort recreating the same or similar responses.

These inefficiencies increase operational costs, and hinder a company’s ability to file more simultaneous regulatory applications at scale. This results in delayed time to gain regulatory approval or to implement global regulatory changes (Refer to section 2.1 of [Anderson, Algorri, Abernathy](https://www.sciencedirect.com/science/article/pii/S0378517323007627?via%3Dihub) for further detail on this topic).

By replacing DOCX/PDF formats with FHIR-compliant JSON, this standard enables:
- **Automation**: Structured JSON enables systems to automatically parse questions, extract metadata, and use metadata-driven routing to send whole RFIs, or subsets of questions, to the appropriate teams within MAHs, reducing manual effort. Generative AI can also leverage this structured data to generate a first draft of an RFI response.
- **Interoperability**: FHIR ensures compatibility with global IT systems, supporting a harmonized international approach, and integration with existing platforms.
- **Traceability**: Linking RFIs (`Communication`) to responses (`QuestionnaireResponse`) via FHIR references allows MAHs to query historical data, improving response consistency and efficiency.
- **Speed**: companies will be able to file more simultaneous applications since this automated process will be faster and require significantly less effort.

### Scope
**In-Scope**:
- Structured RFIs with questions/comments and associated metadata.
- RFI Categorization and sub-categorization across regulatory domains: Administrative, Labeling, Quality, Clinical, Non-clinical, and Safety.
- Support for rich text (Markdown) and embedded images.
- Question-and-Answer response format using FHIR resources.
- Regulated medicinal products and medical devices.

**Out of Scope**:
- Non-RFI related correspondence (e.g., approval letters or notifications).

### Audience
This IG is designed for:
- **Health Authorities**: Regulatory bodies (e.g., FDA, EMA, PMDA) issuing RFIs.
- **Market Authorization Holders (MAHs) / Drug Manufacturers**: Entities responding to RFIs.
- **Health/Pharma IT Developers**: Building systems to author, process, and manage RFI content.
- **Contract Manufacturing Organizations (CMOs)**: Supporting manufacturing-related RFI responses for themselves or clients.
- **Clinical Research Organizations (CROs)**: Supporting clinical related RFI responses for themselves or clients.
- **Healthcare Institutions**: Responding to RFIs related to clinical trial applications/Investigational New Drug Applications (IND).

## Solution Description
The RFI IG leverages FHIR R5 to create a standardized, interoperable framework for RFI workflows, addressing the inefficiencies of traditional document-based processes. The solution is built on a core set of FHIR resources, profiles, and extensions, designed to support structured data exchange while maintaining flexibility for diverse regulatory use cases.

INSERT GRAPHIC OF RFI 

INSERT GRAPHIC OF RFI RESPONSE

### Key Components
- **FHIR Resources**:
  - **Communication**: Captures RFI metadata, including issuer (`sender`), recipient (`recipient`), and drug/device application context (`basedOn` referencing `MedicinalProductDefinition`).
  - **Questionnaire**: Represents RFI questions, supporting rich text (Markdown) and images (via `Attachment`) in a structured format.
  - **QuestionnaireResponse**: Encodes MAH responses, allowing text and image attachments in a question-and-answer format.
  - **Bundle**: Packages `Communication` and `Questionnaire` for RFI issuance, and `QuestionnaireResponse` for responses, ensuring a cohesive transaction.

- **FHIR Profiles**:
  - `RFICommunication`: Constrains `Communication` to enforce mandatory fields (e.g., `status`, `sender`) and link to `MedicinalProductDefinition`.
  - `RFIQuestionnaire`: Ensures `Questionnaire` items use Markdown for text and support `group`, `display`, or `attachment` types.
  - `RFIQuestionnaireResponse`: Allows `QuestionnaireResponse` answers to include Markdown text or `Attachment` images.

- **Extensions**:
  - `rfi-due-date`: Adds a deadline (`dateTime`) to `Communication`.
  - `rfi-priority`: Assigns priority levels (`high`, `medium`, `low`) to RFIs.
  - `rfi-question-id`: Provides a unique identifier for `Questionnaire` items.

- **Value Sets**:
  - `RFICategoryAndSubcategory`: Aligns RFI categorization with ICH CTD headings (e.g., Administrative, CMC) and sub-categories (e.g., DrugSubstance, Bioequivalence).

### Implementation
The IG provides detailed guidance on implementing RFI workflows, including:
- **Data Exchange**: Use FHIR RESTful APIs to transmit RFI `Bundle` resources between health authorities and MAHs.
- **UI Rendering**: Render Markdown text and `Attachment` images in user interfaces using libraries like `marked` (JavaScript) or `python-markdown`.
- **Validation**: Validate resources against profiles using tools like HAPI FHIR or the FHIR Validator.
- **Performance**: Support pagination for large `Bundle` transactions to optimize processing.

For detailed technical specifications, see [Resource Mapping](resource-mapping.html), [Profiles](profiles.html), and [Examples](examples.html).
