# Image Support

Claude's ability to process images within user messages — for analysis, comparison, counting, and description tasks.

## Image Limitations

- Max **100 images** per request
- Size/dimension restrictions apply
- Images consume tokens, charged based on pixel height/width

## Image Block Structure

A special block type within user messages holding either raw image data (base64) or a URL reference. Multiple image blocks are allowed per message.

## Critical Success Factor

**Strong prompting** is required for accurate results — simple prompts often fail.

## Prompting Techniques for Images

- Step-by-step analysis instructions
- One-shot / multi-shot examples (alternating image and text pairs)
- Clear guidelines and verification steps
- Structured analysis frameworks

## Example Use Case

Automated fire-risk assessment from satellite imagery — analyzing tree density, property access, roof overhang, and assigning a numerical risk score.

## Implementation

Base64-encode the image data, then create a message with:
```
{ type: "image", source: base64, media_type: ..., data: ... }
```
followed by a text block containing detailed prompt instructions.

## Key Takeaway

Image accuracy depends heavily on **prompt sophistication** — not just image quality.
