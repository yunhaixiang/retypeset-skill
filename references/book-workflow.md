# Mathematical book workflow

Use this workflow for book-scale retypesetting. Preserve an existing project layout when one is already established; otherwise use the layout below. Do not advance past the stage or chunk the user requests.

## Project state

```text
book-project/
├── source/
│   ├── pdf/
│   │   └── name_of_pdf.pdf
│   ├── pages/                 # Rendered and, if needed, cropped page images
│   └── pdf_info.json          # Visual-navigation index
└── output/
    ├── name_of_pdf_retypeset.tex
    ├── name_of_pdf_retypeset.bib
    ├── style.md               # Project-specific copy of the style guide
    └── audit.md               # Created when auditing begins
```

During preprocessing, copy the packaged `references/style.md` to `output/style.md` if it does not already exist. Record a user-approved book-wide convention in that project-local file under **Specific Conventions**. Do not silently promote a book-specific decision back into the packaged default.

## Stage 1 — Preprocessing

1. Locate the source PDF at `source/pdf/name_of_pdf.pdf`. Render it to individual page images in `source/pages/`, named by source page number. When one PDF page contains multiple book pages, crop each one cleanly and use a stable suffix such as `012-a.png` and `012-b.png`.
2. Create `source/pdf_info.json` for visual navigation. Record the source-PDF page range and rendered-image range for every major part (introduction, notation, each chapter, appendices, lists, bibliography, and indexes). Include visible titles, useful keywords, source page labels, and any crop or page-number irregularities. Recheck every entry directly against the source pages.
3. Read the packaged style guide and the project-local `output/style.md`. Use the latter to retain decisions from earlier sessions.
4. Create `output/name_of_pdf_retypeset.tex` as a compile-ready book template. Define the common theorem-like environments found in the source and a flexible source-numbered theorem-like macro for labels such as “Key Lemma 1.2”. Leave unknown metadata as `Title`, `Author`, and `\date{}`. Use shared preamble macros and lengths rather than local spacing fixes.
5. Create `output/name_of_pdf_retypeset.bib`. Reproduce the source bibliography's visible style, order, and citation handles. Transcribe and TeXify bibliographic mathematics and diacritics under the style guide.
6. Recreate the source table of contents and its hierarchy in the LaTeX scaffold. Preserve source numbering, include section symbols where required by the style guide, and ensure multi-digit numbers do not collide with titles. TeXify mathematics in headings, table-of-contents entries, running heads, and metadata.

Compile the scaffold when a compiler is available. Correct structural and visual problems, but do not start transcribing body text unless the user also requested it.

## Stage 2 — Transcription

Transcribe in user-requested chunks: typically introduction, notation, then one chapter at a time. A new user request is required to move to the next chunk.

For the requested chunk:

1. Re-read `output/style.md` and the relevant source pages visually.
2. Transcribe the content as semantic LaTeX, preserving source-visible numbering, hierarchy, typography, bibliography style, and cross-reference target type.
3. Add labels and links for material in the chunk. For a target in a later untranscribed chapter, create the stable placeholder anchor required by the style guide rather than changing the reference type or number.
4. Compile and render when possible. Compare the rendered pages with the visual source, then correct transcription, layout, spacing, math, labels, and hyperlinks.
5. Audit the completed chunk against `output/style.md` before handoff. Report unreadable material and any verification that could not be performed.

## Stage 3 — Auditing

Audit only a completed chunk the user names. Before each audit, re-read `output/style.md`, because the user may have added conventions since transcription.

Check visual fidelity, source wording, mathematical notation, numbering, internal links, bibliography citations, theorem headings, spacing, and compilation. Make supported fixes, then append a concise dated record to `output/audit.md` containing the chunk audited, fixes made, unresolved issues, and any unverified condition. Do not claim a visual comparison if the project could not be compiled and rendered.
