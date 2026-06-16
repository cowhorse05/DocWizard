# TODO — DocWizard 待办清单

## 近期 (v3.1)

### PDF 解析增强
- [ ] 引入 PDF 专项 Skill（pdf-converter-mineru / pdf-toolkit-mcp）补充扫描版 PDF OCR
- [ ] 复杂排版论文的表格/公式提取优化
- [ ] PDF 目录/书签自动生成（根据标题层级）

### 任务定义与交互优化
- [ ] task.md 支持自由文本描述任务（目前更像清单模板）
- [ ] Agent 执行前向用户确认理解的任务摘要，减少误解
- [ ] 压缩包内 Word 需求文档自动识别（已实现基础版，需完善）

### 图表处理增强
- [ ] Mermaid 本地渲染方案（mermaid-cli 可选依赖），替代 mermaid.ink 网络依赖
- [ ] 复杂图表集成 DrawIO MCP 生成能力
- [ ] 云端 mermaid 渲染 fallback 池（mermaid.ink / kroki / 自建）

### 安装体验优化
- [ ] 一键安装脚本：自动检测平台 → 安装 document-skills 插件 → clone DocWizard
- [ ] 交互式引导流程，降低新手门槛

### Markdown→Word 公式增强
- [ ] 引入 @clipg/w2w 或其他 Markdown→Word 技能，增强 LaTeX 公式 → OMML 转换质量

### 示例与测试
- [ ] demo/ 目录提供典型作业场景：论文模板、数据分析作业、实验报告
- [ ] 集成测试覆盖核心流程：解压→读取需求→分析→转换→汇报

## 中期 (v3.2+)

- [ ] 学术研究流水线：文献管理（Zotero/Mendeley BibTeX）→ 写作 → 格式转换 → 定稿
- [ ] 引入 academic-research-skills 思路，将 DocWizard 从"格式转换器"升级为"学术研究助手"
- [ ] 批量中文模板：选中模板 → 自动应用格式
- [ ] 参考文献格式化引用（GB/T 7714 / APA / MLA）
- [ ] 并发处理多个文件
- [ ] 自定义样式配置
- [ ] docconvert-cli 作为 document-skills 的本地备选方案

## 远期

- [ ] Web UI / 本地 GUI
- [ ] 一键打包：扫描目录 → 处理 → 压缩 zip → 提交
- [ ] 支持更多格式：`.odt`、`.rtf`、`.html`、`.epub`
- [ ] CI/CD 集成：GitHub Actions 自动处理
- [ ] 多语言支持（英文文档排版 CSS）
- [ ] 论文写作辅助：摘要生成、关键词提取、查重预检

## 可引入的 Skill/工具

| Skill/工具 | 用途 | 优先级 |
|-----------|------|--------|
| pdf-converter-mineru | 扫描版 PDF OCR、复杂排版解析 | 高 |
| pdf-toolkit-mcp | PDF 合并/拆分/水印/加密 | 中 |
| @clipg/w2w | Markdown→Word 增强，LaTeX 公式→OMML | 高 |
| academic-research-skills | 学术研究流水线参考 | 中 |
| Excel Analysis Skill | 数据透视表、高级图表 | 中 |
| docconvert-cli | Pandoc 本地备选方案 | 低 |

## 已修复的 Bug

- [x] DOCX 蓝色/彩色字体 → v2.0.0 激进黑体后处理
- [x] Mermaid 在 DOCX 中显示为代码 → v1.6.0 自动渲染管线
- [x] PDF 图片路径断裂 → v1.6.0 HTML 写到源文件目录
- [x] agent 读不了 .docx/.pdf → v1.6.1 预转换策略
- [x] task.md 被 agent 修改 → v1.5.0 只读规则
- [x] pandoc/Chrome/pdftotext/LaTeX 外部依赖 → v3.0.0 纯 Skill 架构
- [x] 三平台适配 → v3.0.0 platforms 配置 + 字体映射 + 命令适配
- [x] LaTeX .tex 编译 → v3.0.0 tectonic/xelatex/pdflatex 自动检测
- [x] 压缩包智能场景识别 → v3.0.0 Word 需求文档自动读取