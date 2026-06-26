# docx2one

Merge multiple Word (.docx) documents into one — right in your browser. No uploads, no servers, no installation.

在浏览器中合并多个 Word 文档，无需上传、无需安装、开箱即用。

**Try online:** https://1asingleone.github.io/docx2one/docx2one.html

---

## 详细介绍

### 这是什么？

docx2one 是一个纯前端工具，让你在浏览器中直接合并多个 Word 文档（.docx）。所有文件在本地处理，**不会上传到任何服务器**，隐私安全有保障。

### 适用场景

- 需要将多份周报/月报合并为一份文档
- 收集了多个同事的 Word 文档需要汇总
- 把几个章节的草稿合并成完整的文稿
- 合并多份合同、协议、报告等

### 功能特性

- **拖拽排序** — 文件列表支持拖拽调整顺序
- **选择性合并** — 可独立控制是否保留正文、页眉、页脚、页码
- **页面设置冲突处理** — 支持"以第一个文档为准"或"保留各自设置"两种模式
- **样式合并** — 自动去重样式表，保留文档的字体和格式
- **编号重映射** — 不同文档的编号列表自动重新编号，避免冲突
- **图片/资源重映射** — 文档中的图片、嵌入文件自动合并

### 用法

1. 用 Chrome、Edge 或 Firefox 打开 `docx2one.html`
2. 拖拽 .docx 文件到虚线区域，或点击「选择文件」按钮
3. 拖拽文件项调整合并顺序
4. 勾选要保留的内容：正文、页眉、页脚、页码
5. 选择页面设置冲突时的处理方式
6. 点击「合并并下载」即可得到合并后的文档

### 兼容性

- 浏览器：Chrome 60+、Edge 79+、Firefox 55+、Safari 12+
- 文件格式：仅支持 `.docx`（Office 2007+ 格式），不支持旧版 `.doc`
- 建议单次合并不超过 10 个文档（受浏览器内存限制）

### 技术原理

`.docx` 文件本质上是 ZIP 压缩包，内部是 XML 格式。docx2one 在浏览器中完成全部操作：

1. 用 [JSZip](https://stuk.github.io/jszip/) 解包每个文档
2. 合并 `word/document.xml` 正文内容，文档间自动插入分页符
3. 合并 `word/styles.xml` 样式表（按 styleId 去重）
4. 合并 `word/numbering.xml` 编号定义（自动重编号避免 ID 冲突）
5. 重映射 `rId` 引用（图片、嵌入文件、页眉页脚等资源）
6. 按用户选项过滤页眉/页脚/页码设置
7. 重新打包为新的 `.docx` 并下载

整个过程完全在浏览器本地完成，文件不会离开你的设备。

---

## Usage (English)

1. Open `docx2one.html` in Chrome/Edge/Firefox
2. Drag .docx files onto the drop zone (or click to select)
3. Drag file items to reorder
4. Check what to include: body, headers, footers, page numbers
5. Choose page-setting conflict strategy
6. Click the merge button to download

### How it works

.docx files are ZIP archives containing XML. The tool:

1. Uses [JSZip](https://stuk.github.io/jszip/) to unpack each document in-browser
2. Merges `document.xml` (body content with page breaks), `styles.xml`, `numbering.xml`
3. Remaps `rId` references for images and embedded files
4. Rebases `numId` references for numbered lists
5. Optionally includes headers, footers, and page-numbering settings
6. Packs everything back into a new `.docx` for download

### Compatibility

- Chrome 60+, Edge 79+, Firefox 55+, Safari 12+
- `.docx` only (Office 2007+). Legacy `.doc` is **not** supported
- Recommended: up to 10 documents at once

## See also

| 同类工具 | 格式 |
|----------|------|
| [pdf2one](https://github.com/1asingleone/pdf2one) | PDF 合并 |
| [pptx2one](https://github.com/1asingleone/pptx2one) | PPT 幻灯片合并 |

## License

MIT
