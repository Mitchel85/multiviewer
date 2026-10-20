# multiviewer

5-module viewer: HTML, Markdown, Mermaid, PlantUML & BPMN in one page.

**→ [Open multiviewer](https://mitchel85.github.io/multiviewer/)** (live on GitHub Pages)

## Usage

1. Open a `.bpmn` (or `.xml`) process file via the BPMN module's **📂 Öffnen** button
2. For HTML / Markdown / Mermaid / PlantUML: paste the content into the corresponding module
3. See it rendered live

## Requirements

- **Runs entirely in the browser** — no server, no install. Open `index.html` locally or via GitHub Pages.
- **Internet connection required at load time:** the rendering libraries (mermaid.js, marked.js, plantuml-encoder, bpmn-js) are loaded from the jsDelivr CDN. Without a connection the HTML editor still works, the other modules show an error message and a visible warning banner.
- **Privacy:** PlantUML diagrams are rendered by the public server at `plantuml.com` — the PlantUML source code you enter is sent there (encoded in the URL). Mermaid, Markdown, HTML and BPMN stay in your browser.

## Export

- Mermaid: `.svg` (standalone, mit Maßen und eingebetteten Styles) und `.png` (2×, weißer Hintergrund)
- BPMN: `.bpmn`, `.svg`, `.png`
- Markdown: `.md`, `.html`, `.doc`

Beide Bild-Exporte nutzen dieselbe Raster-Funktion: Die SVG-Maße werden aus
`viewBox`/`width` gelesen (nicht aus `img.width`, das bei SVG-Bildern 0 ist) und
das SVG wird als `data:`-URL geladen — Blob-URLs tainten den Canvas und brechen
den PNG-Export mit `SecurityError`.

**Mermaid-Version ist gepinnt** (`mermaid@11.17.2`). Nicht auf `@latest` umstellen:
ab mermaid 12 ist die synchrone API `mermaid.render()` entfernt.

## Modules

| Module | Format | Based on |
|--------|--------|----------|
| HTML | Raw HTML/CSS/JS | Browser native |
| Markdown | `.md` formatted text | marked.js 11 |
| Mermaid | `.mmd` diagram syntax | mermaid.js 11.17.2 |
| PlantUML | `.puml` diagram syntax | plantuml-encoder 1.4 |
| BPMN | `.bpmn` process model | bpmn-js 17.11 |

### Markdown Features
- GitHub Flavored Markdown (GFM) with tables, task lists, code blocks
- Live preview with auto-update
- Export as `.md`, standalone `.html`, or **Word `.doc`** (opens in Word, LibreOffice, Google Docs)
