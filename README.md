# x2one — 浏览器端文档合并工具集

Merge Word, PDF, and PowerPoint files in your browser. No uploads, no servers, no installation.

在浏览器中合并 Word、PDF、PowerPoint 文件。不上传、不安装、开箱即用。

---

## 工具 / Tools

| 工具 | 格式 | 在线使用 | 核心技术 |
|------|------|----------|----------|
| **docx2one** | .docx | [试用](https://1asingleone.github.io/docx2one/docx2one.html) | JSZip + DOM 合并 XML |
| **pdf2one** | .pdf | [试用](https://1asingleone.github.io/docx2one/pdf2one.html) | pdf-lib 逐页复制 |
| **pptx2one** | .pptx | [试用](https://1asingleone.github.io/docx2one/pptx2one.html) | JSZip + DOM 合并幻灯片 |

---

## 功能对比

| 功能 | docx2one | pdf2one | pptx2one |
|------|:--------:|:-------:|:--------:|
| 拖拽排序 | ✅ | ✅ | ✅ |
| 选择性合并正文/页眉/页脚/页码 | ✅ | — | — |
| 页面设置冲突处理 | ✅ | — | — |
| 自动分页 | 分页符 | 逐页拼接 | 追加幻灯片 |
| 图片/媒体重映射 | ✅ | — | ✅ |
| 样式/编号合并 | ✅ | — | — |

---

## 原理

所有工具遵循同一技术路线：

> **解包 → 合并内容 → 重映射引用 → 打包**

- **docx / pptx**：ZIP + XML 结构，用 JSZip 解包，DOM 操作 XML，JSZip 重新打包
- **pdf**：二进制格式，用 pdf-lib 直接操作页面对象

---

## License

MIT
