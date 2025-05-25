# Implementation Considerations

## Interoperability
- Use FHIR R4.
- Align with ICH M11 where applicable.
- Support RESTful FHIR APIs.

## UI Rendering
- **Markdown**: Render `item.text`, `answer.valueString` with `marked` (JavaScript) or `python-markdown`.
- **Images**: Display `valueAttachment` as `<img>` or fetch `Media`.
- **Layout**: Stack content (paragraph, image, paragraph).

## Security
- Use OAuth2/SMART on FHIR.
- Sanitize `Attachment.data`.

## Performance
- Use `Media` for images >1MB.
- Support Bundle pagination.

## Validation
- Validate with HAPI FHIR.
- Ensure mandatory fields.