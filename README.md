# EPUB Fixer for Kindle

A single-page web app that repairs the problems that make **Send to Kindle** drop an EPUB's table of contents, then verifies the result against the original.

**Use it:** open the GitHub Pages site for this repository and drop in one or more `.epub` files. Everything runs in your browser, so books are never uploaded anywhere.

## What it fixes

- File names with characters converters mishandle (such as `!` or spaces), renamed to plain names
- Links whose spelling doesn't exactly match the file (`%21` instead of `!`, wrong letter case)
- Table-of-contents entries that are broken, out of reading order or mis-numbered (NCX `playOrder`)
- A missing table of contents, built from the chapter headings
- EPUB 2 books, upgraded to EPUB 3 with a navigation document (optional)
- Block elements nested inside inline elements, made valid without changing how they look (optional)

A book that has no problems is left exactly as it is.

## How it verifies

Before offering the download, it re-opens the output and compares it with the original:

- every chapter's text, character for character
- every image, font and other file, byte for byte
- every element and attribute of the markup, allowing only the changes listed above
- the reading order, every contents entry, and the main metadata

These are the app's own checks, not Amazon's converter or the full EPUBCheck validator.

## Limits

- DRM-protected books are refused.
- ZIP64 archives aren't supported.
- Needs a current browser: Chrome or Edge 103+, Safari 16.4+, Firefox 113+.

The whole app is `index.html`, with no dependencies and no build step.
