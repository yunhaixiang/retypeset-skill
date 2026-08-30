---
name: retypeset
description: Recreate a scanned, photographed, or PDF mathematical text as an editable, visually faithful LaTeX project, preserving the source while applying the repository's typesetting conventions.
---

# Retypeset

Create a clean, editable LaTeX rendition of the supplied mathematical reference while preserving its hierarchy, wording, and intended visual character. The final deliverable is a `.tex` source file or LaTeX project; a compiled PDF is a preview, not a replacement for the source.

## Mandatory style guide

Before inspecting, transcribing, or typesetting any source, read [references/style.md](references/style.md) completely. Its rules are mandatory and take precedence over general LaTeX habits or any conflicting guidance in this file.

In particular, work from direct visual inspection of the complete source pages: never use OCR for transcription, lookup, navigation, verification, or cross-checking. Preserve the source's meaning and wording, while applying the style guide's specified modern mathematical notation, hyperlinking, numbering, and typographic conventions.

For a book project, also read [references/book-workflow.md](references/book-workflow.md) before starting the requested stage. If the project has an `output/style.md`, read it after the packaged style guide; it records book-specific decisions and overrides the default only for that project.

## Scope and stages

Follow only the stage and chunk the user requests. Do not begin transcription after preprocessing, proceed to a later chapter, or begin a final audit without the user's request. This preserves room for the user to make book-wide style decisions between chapters.

- **Preprocessing:** prepare source page images, the lookup index, the LaTeX scaffold, bibliography, and table of contents. Read the Stage 1 instructions in [references/book-workflow.md](references/book-workflow.md).
- **Transcription:** transcribe one requested introduction, notation section, chapter, or other chunk. Read the Stage 2 instructions in [references/book-workflow.md](references/book-workflow.md), then audit that chunk before handoff.
- **Audit:** audit only the requested completed chunk. Read the Stage 3 instructions in [references/book-workflow.md](references/book-workflow.md) and record fixes in the project's `output/audit.md`.

## General workflow

1. Inspect every supplied reference visually. Transcribe text carefully and note page size, margins, columns, type hierarchy, alignment, spacing, rules, tables, and repeated elements. Re-open the complete page when text is unclear; do not use OCR.
2. Confirm requirements that affect the LaTeX project materially, such as the target TeX engine, a required document class, bibliography handling, or whether source artwork may be embedded. If unspecified, make a conventional, self-contained LaTeX project and preserve the original language without silently rewriting its content.
3. Rebuild the document natively, using semantic LaTeX structure—sections, paragraphs, lists, tables, figures, headers, and footers—where it matches the source. Do not use a full-page reference image as the document body.
4. Match the layout by proportions rather than guessing isolated font sizes. Prefer fonts that are available in the target TeX environment; if an exact font is unavailable, choose a close, legible alternative and tell the user.
5. Compile the project with an appropriate available TeX engine, resolve compilation errors, and render the resulting PDF. Compare it with the reference page by page, correcting visible differences in flow, page breaks, spacing, alignment, wrapping, and table layout before delivery.

## Fidelity rules

- Preserve the source's wording and mathematical meaning unless the user asks for an edit or translation. Apply only the notation and typography normalizations required by [references/style.md](references/style.md); flag unreadable text rather than inventing it.
- Preserve meaningful structure and repeated components consistently across pages.
- Make all internal references and bibliography citations hyperlink to their corresponding targets, following [references/style.md](references/style.md).
- Do not claim pixel-perfect equivalence when a reference is low-resolution, incomplete, or uses unavailable fonts.
- Keep the final LaTeX source editable. Raster images may be used only for source artwork that cannot reasonably be recreated as editable content.
- Use the smallest practical set of packages and record any nonstandard engine, font, package, or build step needed to compile the project.
- Do not deliver a PDF without the corresponding `.tex` source unless the user explicitly asks for PDF-only output.

## LaTeX project conventions

- Use `main.tex` as the entry point for multi-file projects. A single-file document may use a descriptive `.tex` filename instead.
- Keep source assets in a clearly named directory such as `assets/` or `figures/`, and use relative paths.
- Select the TeX engine for actual requirements rather than preference. State the build command in the handoff, for example `latexmk -pdf main.tex` or the engine-specific equivalent.
- If no LaTeX compiler is available, still produce the source, explain that compilation could not be verified, and do not claim a successful visual comparison.
