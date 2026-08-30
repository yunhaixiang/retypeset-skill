# Retypeset

Retypeset is a portable instruction set for AI agents that recreate scanned, photographed, or PDF documents as editable LaTeX projects. It prioritizes accurate text, native LaTeX structure, and visual comparison with the source.

## What it does

- Retypes and reformats reference documents without silently rewriting their content.
- Recreates layout with semantic, editable LaTeX: sections, paragraphs, lists, tables, figures, headers, and footers.
- Identifies unreadable source text instead of inventing it.
- Delivers `.tex` source and checks the compiled PDF against the supplied reference before delivery.

## Use with an AI agent

The canonical instructions are in [SKILL.md](SKILL.md), a plain Markdown skill file with YAML metadata. This repository also includes [AGENTS.md](AGENTS.md) for agents that discover project-level instruction files.

Choose the integration that your tool supports:

1. **Skill-aware agents:** Register or place this repository wherever the agent discovers `SKILL.md` skills.
2. **Project-instruction agents:** Keep this repository in the project, or copy the contents of `SKILL.md` into that agent's project-instruction file.
3. **Chat-based agents:** Attach or paste `SKILL.md` and the reference document, then ask the agent to retypeset it into a LaTeX project.

For the best result, provide every page of the reference, the required TeX engine or document class if one is mandated, and whether OCR cleanup or text edits are allowed.

## Compatibility

The workflow deliberately avoids product-specific commands and dependencies. Any capable AI agent that can read Markdown instructions and work with the supplied files can follow it. When an agent has a LaTeX compiler and PDF-rendering capability, it should use them for visual verification; otherwise it should report that limitation rather than claim a completed visual check.

## Repository layout

```text
.
├── SKILL.md            # Canonical agent instructions
├── AGENTS.md           # Project-instruction discovery entry
└── agents/openai.yaml  # Optional Codex/OpenAI UI metadata
```
