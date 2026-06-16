# docx2one

Merge multiple Word (.docx) documents into one — right in your browser. No uploads, no servers, no installation.

合并多个 Word 文档为一个文件 — 纯浏览器端完成，不上传、不安装、开箱即用。

**Try online:** https://1asingleone.github.io/docx2one/docx2one.html

---

## Usage

1. Open `docx2one.html` in Chrome/Edge/Firefox
2. Drag .docx files onto the drop zone (or click to select)
3. Drag file items to reorder
4. Check what to include: body, headers, footers, page numbers
5. Choose page-setting conflict strategy
6. Click the merge button to download

## How it works

.docx files are ZIP archives containing XML:

1. [JSZip](https://stuk.github.io/jszip/) unpacks each document in-browser
2. `document.xml` bodies are concatenated with page breaks between documents
3. `styles.xml` definitions are deduplicated by styleId
4. `numbering.xml` IDs are rebased to avoid collisions
5. `rId` references to images, embedded files, headers and footers are remapped
6. Headers, footers and page numbering are included per user preference
7. Everything is repacked into a new `.docx` for download

## Compatibility

- Chrome 60+, Edge 79+, Firefox 55+, Safari 12+
- `.docx` only (Office 2007+). Legacy `.doc` is **not** supported
- Recommended: up to 10 documents at once

## License

MIT
