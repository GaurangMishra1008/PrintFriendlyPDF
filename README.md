# Print-Friendly PDF Maker

Turns dark, colorful slide PDFs into white pages with dark text, so they cost far less ink to print.

**Try it:** open `index.html` in a browser, or use the GitHub Pages site for this repository.

## What it does

- Whitens dark slide backgrounds and colored boxes.
- Makes text dark on white, including text that was white on a dark background.
- Keeps diagrams and pictures, but lighter.
- Three looks: **Color** (light tints), **Grayscale** (for black-and-white printers) and **Black only** (least ink).
- Live before/after preview with an ink estimate for each page.
- Converts several PDFs at once and saves them as a ZIP.

Everything runs in your browser. Your PDFs are never uploaded.

## Notes

- Slide PDFs like these are usually pictures of slides, so the output is pictures too. Text prints sharp, but you can't select or search it.
- If a page loses faint text, lower **Background removal**.

## How it works

Each page is rendered with [pdf.js](https://mozilla.github.io/pdf.js/). The app estimates the local background color in small blocks, then compares every pixel with the nearby background: pixels close to it become white, and pixels that stand out become ink (light-on-dark ink is flipped to dark). The cleaned pages are written to a new PDF with [pdf-lib](https://pdf-lib.js.org/), and [JSZip](https://stuk.github.io/jszip/) packs multiple files.

It's a single static HTML file with no build step, so you can host it anywhere.
