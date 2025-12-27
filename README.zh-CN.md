# 面向智能体的 arXiv ML/AI 综述论文 LaTeX 模板

[English](README.md) · 简体中文

> [!NOTE]
> 一个基于 IEEEtran（conference）格式的 LaTeX 模板，用于在 arXiv 上发布 ML/AI 综述论文，并针对智能体 IDE 工作流（例如 Cursor、Augment）进行了优化。

## 模板概览

模板主要由两个文件组成：

1. `main.template.tex` - 主 LaTeX 文档模板
2. `references.template.bib` - BibTeX 参考文献模板

这些模板针对 AI 智能体的理解与生成进行了优化：通过清晰的章节边界、显式指令以及较为完整的注释，帮助降低生成与编辑时的出错率。

## 快速开始

> [!TIP]
> 建议：先创建工作副本并编译 `main.tex`（保持 `*.template.*` 文件不被修改）。

1. 创建工作文件：

   ```bash
   cp main.template.tex main.tex
   cp references.template.bib references.bib
   ```

2. 编译（推荐使用 `latexmk`）：

   ```bash
   latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
   ```

3. 输出：`main.pdf`

> [!NOTE]
> 没有 `latexmk`？可以使用手动流程：
>
> ```bash
> pdflatex main.tex
> bibtex main
> pdflatex main.tex
> pdflatex main.tex
> ```

> [!IMPORTANT]
> 模板使用 `\bibliography{references}`，因此你的 BibTeX 文件应命名为 `references.bib`（或者将 `\bibliography{...}` 的名称改成与你的文件一致）。

## 面向 AI 智能体：如何使用此模板

### 文档结构

`main.template.tex` 按 IEEE conference 论文格式组织，包含以下关键部分：

```
- Document Class & Package Imports
- Title & Author Information
- Abstract & Keywords
- Introduction
- Related Work
- Methodology
- Experiments
- Results
- Conclusion
- References
```

每个部分都使用注释块（`%%%%%%%%%`）包裹，用于清晰标记边界，并包含对期望内容的明确说明。

### 面向 AI 智能体的关键特性

#### 1. 章节结构

AI 智能体应保持模板提供的章节层级结构（`\section{}`、`\subsection{}`）。每个章节在注释中都描述了期望包含的内容。

#### 2. 图形生成

模板包含基于 TikZ 的图形示例。生成图形时：
- 使用预定义的自定义颜色（qubitblue、controlred、aigreen、quantumpurple、errororange）
- 保持一致的 scale 与 transformation 参数
- 在不同图中保持风格一致
- 确保所有图都有描述性的 caption 与 label

#### 3. 表格格式

表格建议遵循专业排版风格：
- 使用 booktabs 宏包的 `\toprule`、`\midrule`、`\bottomrule`
- 使用 `\textbf{}` 设置清晰的列标题
- 使用正确的对齐方式（l、c、r）
- 提供描述性的 caption 与 label

#### 4. 数学记号

公式建议使用 amsmath 环境：
- 用 `\begin{equation}` 为重要公式编号
- 多行公式用 `\begin{align}`
- 定义所有变量与记号
- 全文保持一致的数学格式

#### 5. 引用模式

使用 `\cite{key}` 插入引用，其中 “key” 对应 `references.template.bib` 文件中的条目。

### 参考文献使用

`references.template.bib` 文件包含多种参考文献类型的示例。每添加一条新引用：

1. 按格式创建唯一 citation key：`firstauthorYEARfirstword`
2. 为对应类型补全所有必需字段
3. 作者格式使用 “Last Name, First Name”
4. 多位作者用 “and” 分隔
5. 在可用时包含 DOI 与 URL
6. 用 `{Brackets}` 保护标题中的缩写大小写

### 给 AI 智能体的特别说明

1. **内容生成**：将所有用 `[square brackets]` 包裹的占位文本替换为合适内容。

2. **引用**：始终确认 .tex 中的 `\cite{key}` 与 .bib 中的条目 key 精确匹配。

3. **单位**：使用 SI 单位并保留正确空格（例如 `10~\text{GB}`，而不是 `10GB`）。

4. **图形**：生成 TikZ 图时建议逐步构建，并在每一步验证语法正确性。

5. **LaTeX 特性**：
   - 数学环境中的文本默认会被斜体化
   - 在公式中插入非数学文本使用 `\text{}`
   - LaTeX 中空行会创建新段落

6. **常见错误避免**：
   - 花括号或环境分隔符不匹配
   - 未转义的 % 字符（除非作为注释）
   - 环境嵌套不正确
   - 忘记关闭数学环境

## 重要的 IEEE 格式指南

- 论文长度：通常 8–10 页（包括图表与参考文献）
- 页边距与双栏排版：由 IEEEtran 类维护
- 字号：由 document class 控制（不要自行覆盖）
- 图表放置：优先使用 [t]（顶部）或 [b]（底部）

## AI 智能体示例工作流程

1. 复制模板文件
2. 替换标题、作者信息与关键词
3. 按说明填充各章节内容
4. 创建必要的图与表
5. 向 .bib 文件添加参考文献
6. 确保文中所有引用在 .bib 中都有对应条目
7. 最终编译前移除说明性注释

## arXiv 提交的特别注意事项

1. 将所有文件放在同一目录
2. 避免在 `\include{}` / `\input{}` / `\includegraphics{}` 中使用绝对路径
3. 尽量减少对非标准宏包的依赖
4. 尽可能使用矢量图
5. 确保所有字体正确嵌入

该模板的结构旨在在遵循 IEEE 排版格式与 arXiv 提交要求的同时，方便 AI 辅助的内容生成与编辑。
