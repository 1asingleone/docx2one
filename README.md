# docx2one

Merge multiple Word (.docx) documents into one — right in your browser. No uploads, no servers, no installation.

**Try online:** https://1asingleone.github.io/docx2one/docx2one.html

合并多个 Word 文档为一个文件 — 纯浏览器端完成，不上传、不安装、开箱即用。

**在线使用:** https://1asingleone.github.io/docx2one/docx2one.html

---

## 中文介绍

### 用法

1. 用 Chrome / Edge / Firefox 打开 `docx2one.html`
2. 拖拽 .docx 文件到虚线区域，或点击「选择文件」
3. 拖拽文件项可调整合并顺序
4. 勾选要保留的内容：正文、页眉、页脚、页码
5. 选择页面设置冲突时的处理方式
6. 点击「合并并下载」即得合并后的文档

### 原理

.docx 本质是 ZIP 压缩包，内部是 XML。程序在浏览器中完成全部操作：

1. 用 [JSZip](https://stuk.github.io/jszip/) 解包每个文档
2. 合并 `document.xml`（正文内容，文档间自动插入分页符）
3. 合并 `styles.xml`（样式表，按 styleId 去重）
4. 合并 `numbering.xml`（编号定义，自动重编号避免 ID 冲突）
5. 重映射 `rId` 引用（图片、嵌入文件、页眉页脚等资源）
6. 按用户选项过滤页眉/页脚/页码设置
7. 重新打包为新的 .docx 并下载

### 兼容性

- 浏览器：Chrome 60+、Edge 79+、Firefox 55+、Safari 12+
- 文件格式：仅支持 .docx（Office 2007+）。**不支持** 旧版 .doc
- 建议单次合并不超过 10 个文档（受浏览器内存限制）

---

## English

### Usage

1. Open `docx2one.html` in Chrome/Edge/Firefox
2. Drag .docx files onto the drop zone (or click to select)
3. Drag file items to reorder
4. Check what to include: body, headers, footers, page numbers
5. Choose page-setting conflict strategy
6. Click the merge button to download

### How it works

.docx files are ZIP archives containing XML:

1. [JSZip](https://stuk.github.io/jszip/) unpacks each document in-browser
2. `document.xml` bodies are concatenated with page breaks between documents
3. `styles.xml` definitions are deduplicated by styleId
4. `numbering.xml` IDs are rebased to avoid collisions
5. `rId` references to images, embedded files, headers and footers are remapped
6. Headers, footers and page numbering are included per user preference
7. Everything is repacked into a new `.docx` for download

### Compatibility

- Chrome 60+, Edge 79+, Firefox 55+, Safari 12+
- `.docx` only (Office 2007+). Legacy `.doc` is **not** supported
- Recommended: up to 10 documents at once

---

## License

MIT
