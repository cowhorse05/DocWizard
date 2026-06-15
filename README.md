# md2docx-pdf

> Markdown → DOCX + PDF，一键转换，完美支持中文。自动检测系统，缺依赖会提示你怎么装。

跨平台命令行工具，把 `.md` 文件转成排版精美的 Word 文档和 PDF。

---

## 快速开始

```bash
git clone https://github.com/cowhorse05/md2doc2pdf.git
cd md2doc2pdf

# 装依赖，首次运行会自动检测，没装会打印安装命令
#   pandoc（必装）
#   Chrome/Edge（只转 DOCX 的话不用装）

python md2docx_pdf.py 报告.md                 # 转 DOCX
python md2docx_pdf.py 报告.md -f pdf          # 转 PDF
python md2docx_pdf.py 报告.md -f both         # 两个都转
python md2docx_pdf.py *.md -f both            # 批量转
python md2docx_pdf.py 报告.md -f both -o ./out # 指定输出目录
```

---

## 依赖安装

首次运行会自动检测，缺什么打印什么。以下供手动参考：

### pandoc（必装）

| 系统 | 装法 |
|------|------|
| Windows | `winget install pandoc` |
| macOS | `brew install pandoc` |
| Ubuntu/Debian | `sudo apt install pandoc` |
| Fedora | `sudo dnf install pandoc` |
| Arch | `sudo pacman -S pandoc` |

### 浏览器（转 PDF 才需要，工具自动搜索 Chrome/Edge/Chromium）

| 系统 | 建议 |
|------|------|
| Windows | Chrome 或 Edge（系统自带） |
| macOS | `brew install --cask google-chrome` |
| Linux | `sudo apt install chromium-browser` |

---

## 命令说明

```
用法: md2docx_pdf.py <文件> [-f 格式] [-o 输出目录]

参数:
  inputs                要转的 md 文件，支持通配符 "*.md"
  -f docx|pdf|both      输出格式，默认 docx
  -o DIR                输出目录，默认跟源文件一起
  --version             看版本
```

---

## 运行效果

```
==================================================
  md2docx_pdf v1.0.0
  Markdown -> DOCX / PDF Converter
==================================================

[CHECK] Verifying dependencies...
  Platform detected: Windows
  pandoc: pandoc 3.9.0.2
  browser: chrome.exe
[OK] All dependencies satisfied

  Files to convert: 2
  Format: both
  Output: (same as input)

[FILE] 课桥可用性测试评估.md (18,139 bytes)
  -> DOCX: 课桥可用性测试评估.docx ... [OK] (23,000 bytes)
  -> PDF:  课桥可用性测试评估.pdf ... [OK] (652,383 bytes)

[FILE] 失物招领可用性测试评估.md (19,188 bytes)
  -> DOCX: 失物招领可用性测试评估.docx ... [OK] (23,568 bytes)
  -> PDF:  失物招领可用性测试评估.pdf ... [OK] (836,750 bytes)

==================================================
  [OK] 4 succeeded   [FAIL] 0 failed   [TOTAL] 2 file(s)
==================================================
```

---

## PDF 排版

自动注入中文排版 CSS：

| 元素 | 效果 |
|------|------|
| 标题 | h1 蓝色下划线，h2 灰色下划线 |
| 表格 | 带边框，表头加粗灰底，隔行变色 |
| 代码 | 浅灰背景，等宽字体 |
| 引用 | 蓝色左边框，浅蓝背景 |
| 字体 | Microsoft YaHei → SimSun → PingFang SC → Noto Sans SC |

Linux 缺中文字体的话：
```bash
sudo apt install fonts-noto-cjk
```

---

## 原理

```
.md ──pandoc──> .docx      （直接转）

.md ──pandoc──> HTML ──注入CSS──> 无头浏览器 ──> .pdf
```

---

## 常见问题

| 问题 | 怎么搞 |
|------|--------|
| `pandoc not found` | 装 pandoc，见上面 |
| 提示没浏览器 | 装 Chrome 或设 `BROWSER_PATH` |
| PDF 中文乱码 | Linux 缺字体，`apt install fonts-noto-cjk` |
| Permission denied | docx 被 Word 打开了，关了重试 |
| 通配符不生效 | 加引号 `"*.md"` |

---

## License

MIT — 李裕峰
