---
name: retypeset
description: Recreate a reference document as an editable, visually faithful LaTeX project when the user asks to retype, reformat, or modernize a scanned, photographed, or PDF document.
---

# Retypeset

Create a clean, editable LaTeX rendition of the supplied reference while preserving the source's hierarchy, wording, and intended visual character. The final deliverable is a `.tex` source file or LaTeX project; a compiled PDF is a preview, not a replacement for the source.

## Workflow

1. Inspect every supplied reference. Extract the text carefully and note page size, margins, columns, type hierarchy, alignment, spacing, rules, tables, and repeated elements.
2. Confirm requirements that affect the LaTeX project materially, such as the target TeX engine, a required document class, bibliography handling, or whether source artwork may be embedded. If unspecified, make a conventional, self-contained LaTeX project and preserve the original language without silently rewriting its content.
3. Rebuild the document natively, using semantic LaTeX structure—sections, paragraphs, lists, tables, figures, headers, and footers—where it matches the source. Do not use a full-page reference image as the document body.
4. Match the layout by proportions rather than guessing isolated font sizes. Prefer fonts that are available in the target TeX environment; if an exact font is unavailable, choose a close, legible alternative and tell the user.
5. Compile the project with an appropriate available TeX engine, resolve compilation errors, and render the resulting PDF. Compare it with the reference page by page, correcting visible differences in flow, page breaks, spacing, alignment, wrapping, and table layout before delivery.

## Fidelity rules

- Preserve text exactly unless the user asks for editing, translation, or OCR cleanup. Flag unreadable text rather than inventing it.
- Preserve meaningful structure and repeated components consistently across pages.
- Do not claim pixel-perfect equivalence when a reference is low-resolution, incomplete, or uses unavailable fonts.
- Keep the final LaTeX source editable. Raster images may be used only for source artwork that cannot reasonably be recreated as editable content.
- Use the smallest practical set of packages and record any nonstandard engine, font, package, or build step needed to compile the project.
- Do not deliver a PDF without the corresponding `.tex` source unless the user explicitly asks for PDF-only output.

## LaTeX project conventions

- Use `main.tex` as the entry point for multi-file projects. A single-file document may use a descriptive `.tex` filename instead.
- Keep source assets in a clearly named directory such as `assets/` or `figures/`, and use relative paths.
- Select the TeX engine for actual requirements rather than preference. State the build command in the handoff, for example `latexmk -pdf main.tex` or the engine-specific equivalent.
- If no LaTeX compiler is available, still produce the source, explain that compilation could not be verified, and do not claim a successful visual comparison.
