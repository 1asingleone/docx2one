# docx2one

Merge multiple Word (.docx) documents into one — right in your browser. No uploads, no servers, no installation.

合并多个 Word 文档为一个文件 — 纯浏览器端完成，不上传、不安装。

## Usage

1. **Open** `index.html` in Chrome/Edge/Firefox
2. **Drag** .docx files onto the drop zone (or click to select)
3. **Drag** file items to reorder
4. **Check** what to include: body, headers, footers, page numbers
5. **Choose** page-setting conflict strategy: use first doc's settings or keep each doc's
6. **Click** "合并并下载" to download the merged file

## How it works

.docx files are ZIP archives containing XML. The tool:

1. Uses [JSZip](https://stuk.github.io/jszip/) to unpack each document in-browser
2. Merges `document.xml` (body content with page breaks), `styles.xml`, `numbering.xml`
3. Remaps `rId` references for images and embedded files
4. Rebases `numId` references for numbered lists
5. Optionally includes headers, footers, and page-numbering settings
6. Packs everything back into a new `.docx` for download

## Compatibility

- Chrome 60+, Edge 79+, Firefox 55+, Safari 12+
- Files must be `.docx` (Office 2007+ format). Legacy `.doc` is **not** supported.
- Recommended: up to 10 documents at once (~hundreds of pages)

## License

MIT
