# Agent-Friendly LaTeX Template for arXiv ML/AI Review Papers

English · [简体中文](README.zh-CN.md)

> [!NOTE]
> An IEEEtran (conference) LaTeX template for ML/AI review papers on arXiv, optimized for agentic IDE workflows (e.g., Cursor, Augment).

## Template Overview

The template consists of two main files:

1. `main.template.tex` - The main LaTeX document template
2. `references.template.bib` - The BibTeX references template

These templates are optimized for AI agent understanding and generation, with clear section demarcations, explicit instructions, and comprehensive commenting.

## Quickstart

> [!TIP]
> Recommended: create working copies and compile `main.tex` (leave the `*.template.*` files untouched).

1. Create working files:

   ```bash
   cp main.template.tex main.tex
   cp references.template.bib references.bib
   ```

2. Compile (recommended: `latexmk`):

   ```bash
   latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
   ```

3. Output: `main.pdf`

> [!NOTE]
> No `latexmk`? Use the manual sequence:
>
> ```bash
> pdflatex main.tex
> bibtex main
> pdflatex main.tex
> pdflatex main.tex
> ```

> [!IMPORTANT]
> The template uses `\bibliography{references}`, so your BibTeX file should be named `references.bib` (or change the `\bibliography{...}` name to match).

## For AI Agents: How to Use This Template

### Document Structure

The `main.template.tex` file follows IEEE conference paper format with the following key sections:

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

Each section is wrapped with comment blocks (`%%%%%%%%%`) to clearly delineate boundaries and includes explicit instructions about expected content.

### Key Features for AI Agents

#### 1. Section Structure

AI agents should maintain the hierarchical structure of sections (`\section{}`) and subsections (`\subsection{}`) as provided in the template. Each section has specific expected content described in comments.

#### 2. Figure Generation

The template includes TikZ-based figure examples. When creating figures:
- Use the predefined custom colors (qubitblue, controlred, aigreen, quantumpurple, errororange)
- Maintain the scale and transformation parameters
- Use consistent styling across figures
- Ensure all figures have descriptive captions and labels

#### 3. Table Formatting

Tables should follow the professional formatting with:
- `\toprule`, `\midrule`, and `\bottomrule` from the booktabs package
- Clear column headers with `\textbf{}` formatting
- Proper alignment specifications (l, c, r)
- Descriptive captions and labels

#### 4. Mathematical Notation

Use the amsmath environment for equations:
- Number important equations with `\begin{equation}`
- Use `\begin{align}` for multi-line equations
- Define all variables and notation
- Use consistent mathematical formatting throughout

#### 5. Citation Pattern

Citations should be inserted using `\cite{key}` where "key" corresponds to an entry in the references.template.bib file.

### Working with References

The `references.template.bib` file contains examples of different reference types. For each new reference:

1. Create a unique citation key following the format: `firstauthorYEARfirstword`
2. Include all required fields for the specific reference type
3. Format author names as "Last Name, First Name"
4. Separate multiple authors with "and"
5. Include DOIs and URLs when available
6. Use `{Brackets}` to protect capitalization in titles for acronyms

### Special Instructions for AI Agents

1. **Content Generation**: Replace all placeholder text surrounded by `[square brackets]` with appropriate content.

2. **Citations**: Always verify that any `\cite{key}` commands in the .tex file match exactly with a corresponding entry in the .bib file.

3. **Units**: Use SI units with proper spacing (e.g., `10~\text{GB}` rather than `10GB`).

4. **Figures**: When generating TikZ diagrams, build them incrementally and verify syntax at each step.

5. **LaTeX-Specific Behaviors**:
   - Text within mathematical environments is automatically italicized
   - Use `\text{}` for non-mathematical text within equations
   - Blank lines in LaTeX create new paragraphs

6. **Common Errors to Avoid**:
   - Unmatched braces or environment delimiters
   - Using % character without escaping it (unless intended as a comment)
   - Improper nesting of environments
   - Forgetting to close math environments

## Important IEEE Format Guidelines

- Paper length: typically 8-10 pages (including figures and references)
- Margins and column formatting: maintained by the IEEEtran class
- Font sizes: controlled by the document class (do not override)
- Figure and table placement: prefer [t] (top) or [b] (bottom) placement

## Example Usage Pattern for AI Agents

1. Copy the template files
2. Replace title, author information, and keywords
3. Fill each section with appropriate content following the instructions
4. Create necessary figures and tables
5. Add references to the .bib file
6. Ensure all citations in the text have corresponding entries
7. Remove instruction comments before final compilation

## Special Considerations for arXiv Submissions

1. Keep all files in the same directory
2. Avoid using absolute paths for included files
3. Minimize dependencies on non-standard packages
4. Use vector graphics where possible
5. Ensure all fonts are embedded properly

This template is specifically structured to facilitate AI-based content generation while adhering to IEEE formatting standards and arXiv submission requirements. 
