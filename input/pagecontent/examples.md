### RFI Question
- **Resource**: [Bundle-rfi-example](Bundle-rfi-example.html)
- **Description**: RFI from a regulator about drug packaging, with paragraph, image placeholder, and paragraph.

```json
{
  "resourceType": "Bundle",
  "id": "rfi-bundle-003",
  "url": "http://hl7.org/fhir/uv/rfi-ig/Bundle/response-bundle-003",
  "type": "collection",
  "entry": [
    {
      "resource": {
        "resourceType": "Communication",
        "id": "rfi-comm-003",
        "status": "in-progress",
        "category": [
          {
            "coding": [
              {
                "system": "http://hl7.org/fhir/rfi-type",
                "code": "RFI"
              }
            ]
          }
        ],
        "sender": {
          "reference": "Organization/FDA"
        },
        "recipient": {
          "reference": "Organization/MAH-PharmaCorp"
        },
        "basedOn": [
          {
            "reference": "MedicinalProductDefinition/NDA78901"
          }
        ],
        "payload": [
          {
            "contentReference": {
              "reference": "Questionnaire/rfi-question-003"
            }
          }
        ],
        "extension": [
          {
            "url": "http://hl7.org/fhir/StructureDefinition/rfi-due-date",
            "valueDateTime": "2025-07-15T23:59:59Z"
          }
        ]
      }
    },
    {
      "resource": {
        "resourceType": "Questionnaire",
        "id": "rfi-question-003",
        "status": "active",
        "item": [
          {
            "linkId": "q1",
            "type": "group",
            "text": "Provide details on the drug product packaging.",
            "code": [
              {
                "system": "http://hl7.org/fhir/rfi-category",
                "code": "CMC"
              },
              {
                "system": "http://hl7.org/fhir/rfi-subcategory",
                "code": "DrugProduct"
              }
            ],
            "extension": [
              {
                "url": "http://hl7.org/fhir/StructureDefinition/rfi-question-id",
                "valueString": "Q003"
              }
            ],
            "item": [
              {
                "linkId": "q1.1",
                "type": "display",
                "text": "**Packaging Details**: Describe the primary packaging materials and their compatibility with the drug product."
              },
              {
                "linkId": "q1.2",
                "type": "attachment",
                "text": "Upload an image of the packaging."
              },
              {
                "linkId": "q1.3",
                "type": "display",
                "text": "Provide any additional notes on packaging stability or testing."
              }
            ]
          }
        ]
      }
    }
  ]
}
```

### RFI Response
- **Resource**: [Bundle-response-example](Bundle-response-example.html)
- **Description**: MAH response to the regulator with paragraph, image, and paragraph.

```json
{
  "resourceType": "Bundle",
  "id": "response-bundle-003",
  "url": "http://hl7.org/fhir/uv/rfi-ig/Bundle/rfi-bundle-003",
  "type": "collection",
  "entry": [
    {
      "resource": {
        "resourceType": "QuestionnaireResponse",
        "id": "rfi-response-003",
        "questionnaire": "Questionnaire/rfi-question-003",
        "status": "completed",
        "author": {
          "reference": "Practitioner/PackagingLead"
        },
        "source": {
          "reference": "Communication/rfi-comm-003"
        },
        "item": [
          {
            "linkId": "q1",
            "item": [
              {
                "linkId": "q1.1",
                "answer": [
                  {
                    "valueString": "The primary packaging uses high-density polyethylene (HDPE) bottles, which are compatible with the drug product. Compatibility tests confirm no leaching or degradation."
                  }
                ]
              },
              {
                "linkId": "q1.2",
                "answer": [
                  {
                    "valueAttachment": {
                      "contentType": "image/jpeg",
                      "data": "iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVR42mNkYAAAAAYAAjCB0C8AAAAASUVORK5CYII=",
                      "title": "HDPE Bottle Image"
                    }
                  }
                ]
              },
              {
                "linkId": "q1.3",
                "answer": [
                  {
                    "valueString": "Stability tests under 25°C/60%RH show no packaging-related issues over 24 months. Additional stress testing data is available upon request."
                  }
                ]
              }
            ]
          }
        ]
      }
    }
  ]
}
```