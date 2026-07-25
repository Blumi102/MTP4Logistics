# Formatting Rules

## 1. Figure Captions

- **Heading level:** `#####` (5th level)
- **Format:** `##### Figure {chapter}.{sequence}: {title}`
- **Numbering:** Chapter number + sequential number, separated by dot (e.g. `Figure 9.1`, `Figure 9.2`)
- **Position:** Directly **before** the image (`![...](...)`), no blank line between caption and image
- **Example:**
  ```markdown
  ##### Figure 9.1: Extension of the Manifest for Modeling Composed MTPs
  ![Extension of the Manifest for Modeling Composed MTPs](./images/01_Manifest.drawio.svg)
  ```

## 2. Table Captions

- **Heading level:** `#####` (5th level)
- **Format:** `##### Table {chapter}.{sequence}: {title}` (AML identifiers in the title in *italics*)
- **Numbering:** Chapter number + sequential number, separated by dot (e.g. `Table 9.1`, `Table 9.2`)
- **Position:** Directly **before** the table, with one blank line between the caption and the `<table>` tag
- **Example:**
  ```markdown
  ##### Table 9.1: Model Definition of *SUC ComposedModuleTypePackage*

  <table>
    ...
  </table>
  ```

## 3. References to Figures and Tables

- **Format:** Markdown link `[Figure X.Y](#anchor)` or `[Table X.Y](#anchor)`
- **Anchor scheme:** Lowercase, spaces replaced by `-`, special characters and dots removed — matches the auto-generated Markdown heading anchor of the `#####` heading
- **Examples:**
  ```markdown
  [Figure 9.1](#figure-91-extension-of-the-manifest-for-modeling-composed-mtps)
  [Table 9.1](#table-91-model-definition-of-suc-composedmoduletypepackage)
  ```

## 4. Section Numbering

| Heading level | Markdown | Numbering | Example |
|---|---|---|---|
| Chapter | `##` | `X.Y` | `## 9.1 MTP Extension of the Manifest` |
| Subchapter | `###` | `X.Y.Z` | `### 9.1.1 Overview` |
| Subsection | `####` | **none** (title only) | `#### Extension of the Manifest for Modeling Composed MTPs` |
| Figure/Table caption | `#####` | See rules 1 & 2 | `##### Figure 9.1: ...` |

- 4th-level sections (`####`) have **no** number — descriptive title only.

## 5. Inline Citations

- **Format:** Markdown link with the BibTeX shorthand in square brackets as display text, linking to the entry in `98_References/README.md`
- **Syntax:** `[[{shorthand}]](../98_References/README.md#{anchor})`
- **Shorthand:** taken from the `shorthand` field of the BibTeX entry (e.g. `NE 171`, `GPL23`, `BFG+21`)
- **Anchor:** derived from the `### ` heading of the reference entry — lowercase, spaces replaced by `-`, special characters removed
- **Example:**
  ```markdown
  [[NE 171]](../98_References/README.md#namur-ak-419-2020)
  [[BFG+21]](../98_References/README.md#blumenstein-et-al-design-principles)
  ```
- Before linking, verify the entry exists in `98_References/README.md`. If missing, add it first using bibliographic data from the `Bib/` folder.
- If a shorthand is shared by multiple entries (collision), list all affected entries for the user to resolve.

## 6. Reference Entries (`98_References/README.md`)

- Each entry is a `### ` heading followed by a bullet list of metadata fields
- **Heading format:** descriptive title or citation key used in the text (e.g. `### NAMUR AK 4.19, 2020`, `### Blumenstein et al., Design Principles`)
- **Required fields:** `Citation key`, `Shorthand`, `Authors`, `Year`, `Title` — add `Journal`, `Booktitle`, `Publisher`, `Address`, `DOI`, `URL` as applicable
- **Sorting:** entries must always be kept in **alphabetical order** by `### ` heading
- **Example:**
  ```markdown
  ### Blumenstein et al., Design Principles

  - Citation key: `Blumenstein.Designprinzipien`
  - Shorthand: `BFG+21`
  - Authors: Michelle Blumenstein, Alexander Fay, ...
  - Year: 2021
  - Title: Designprinzipien für den Modul- und Serviceentwurf ...
  - Booktitle: VDI-Bericht 2392 - Automation 2021
  - Publisher: VDI-Verlag
  - Address: Düsseldorf
  - DOI: 10.51202/9783181023921-101
  ```

## 7. Table Cell Alignment

- **All** cells (`<td>` and `<th>`) must have the attribute `align="left"`
- This applies to cells with `colspan` as well
- No exceptions — every cell in every table must be left-aligned
- **Example:**
  ```html
  <tr>
    <th align="left">Name</th>
    <td colspan="3" align="left"><strong>ComposedModuleTypePackage</strong></td>
  </tr>
  ```
