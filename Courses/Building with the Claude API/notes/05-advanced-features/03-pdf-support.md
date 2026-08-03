# PDF Support

Claude can read PDF files directly, using code very similar to image processing.

## Key Implementation Changes

| Images | PDFs |
|---|---|
| `type: "image"` | `type: "document"` |
| `media_type: "image/png"` | `media_type: "application/pdf"` |
| `image_bytes` | `file_bytes` |

## Claude's PDF Capabilities

Reads text + images + charts + tables — a one-stop solution for comprehensive document analysis, including mixed content.

## Usage Pattern

The same as image input, but with document-specific parameters (`type: "document"`, `media_type: "application/pdf"`).
