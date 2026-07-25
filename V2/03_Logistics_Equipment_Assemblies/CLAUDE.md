# Workflow: Creating a Compact Markdown Chapter from a LaTeX Source

Use this workflow whenever a new chapter is to be written as a `.md` file from an existing LaTeX source in this folder (e.g. `09_Art1LEA.tex`). The output goes into the corresponding `*_NEW` folder at the project root (e.g. `03_Logistics_Equipment_Assemblies_NEW/`). Formatting rules are defined in the project-root `CLAUDE.md`.

## Step 1 — Gather source material

1. Read the LaTeX source in full. Identify all sections and conceptual parts — **no concept part may be omitted**.
2. Glob the `NEW Images/` subfolder of this chapter folder to list all available images.
3. Read the first ~60 lines of an existing reference chapter (e.g. `02_Modular_Logistics_System_NEW/02_Modular_Logistics_System.md`) to confirm current formatting conventions.
4. Read `98_References/README.md` in full to know which citation shorthands already exist.
5. Read all `.bib` files in `Bib/` that are cited in the LaTeX source (check `\cite{…}` keys) to retrieve the `shorthand` value for every citation key used.

## Step 2 — Prepare the output folder

1. Determine the chapter number from the target folder name (e.g. `03_Logistics_Equipment_Assemblies_NEW` → chapter 3).
2. Copy all images from `NEW Images/` into `<output_folder>/images/` using Bash `cp`.
3. Confirm the copy succeeded with `ls`.

## Step 3 — Resolve citations before writing

For every `\cite{key}` in the LaTeX source:

1. Look up the `shorthand` field in the `.bib` file.
2. Check whether an entry with that shorthand already exists in `98_References/README.md`.
3. If **missing**: add the entry to `98_References/README.md` using the bibliographic data from the `.bib` file. Keep entries in **alphabetical order** by `### ` heading (see formatting rule 6 in the project-root `CLAUDE.md`).
4. Derive the anchor from the `### ` heading: lowercase, spaces → `-`, special characters removed.

## Step 4 — Write the markdown file

Create `<output_folder>/<descriptive_name>.md`. Apply all formatting rules from the project-root `CLAUDE.md`:

- **Heading hierarchy:** `##` chapter, `###` subchapter, `####` subsection (no number), `#####` figure/table captions.
- **Citations:** `[[shorthand]](../98_References/README.md#anchor)`
- **Images:** relative path `./images/<filename>`; `##### Figure X.Y: …` caption directly before `![…](…)` with **no blank line** between caption and image.
- **Tables:** all `<td>` and `<th>` with `align="left"`; caption with **one blank line** above `<table>`.
- **Cross-references:** in-text links to figures/tables as `[Figure X.Y](#anchor)`.

**Tone and scope:** English, technical report style. Reformulate LaTeX prose into concise sentences — omit LaTeX-specific constructs (`\label`, `\ref`, `\vspace`, etc.) but preserve every conceptual point. Do not add content not present in the source.

## Step 5 — Verify

After writing, confirm:

- Every `\cite{key}` from the LaTeX source has a corresponding `[[shorthand]](…)` link in the markdown.
- Every image path `./images/<filename>` was actually copied in Step 2.
- All anchors in citation links and figure/table cross-references resolve to real headings in the target files.
