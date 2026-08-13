---
name: write-thesis-proposal
description: Use when writing, drafting, or generating a thesis proposal (开题报告) to ensure strict adherence to length, sub-sections (立论依据, 文献综述, etc.), and academic format. Use whenever the user asks for help writing a research proposal or filling out a proposal template.
---

# Write Thesis Proposal (撰写开题报告)

## Overview
This skill enforces a highly detailed, 10,000-word academic thesis proposal (开题报告) generation process. You MUST generate the proposal iteratively, section by section. 
**CRITICAL**: You must strictly enforce word counts. LLMs naturally write short summaries, which will cause you to fail the ~10000-word requirement. To achieve the required word counts, you MUST expand deeply on every sub-point, providing extensive historical context, multiple detailed case studies, in-depth theoretical derivations, and comprehensive analysis. NEVER summarize.

## Red Flags - STOP and Start Over
If you catch yourself doing any of the following, delete your drafted text and start over:
- **Generating more than ONE major section at a time.**
- **Ignoring the detailed sub-points** (e.g., writing "1. 立论依据" without breaking it down into 1.1 to 1.6).
- **Under-generating content**. If your generated section falls significantly short of the target word count (e.g. generating 500 words for a 3000-word target), you have failed.
- **Failing to create the reference basis file.** EVERY generation must be accompanied by a separate `.md` reference file.

## The Workflow (Strictly Iterative)

### Phase 1: Prerequisite Check, Topic Alignment & Literature Gathering
1. **Prerequisite Check**: Before starting, check your available tools. You MUST verify that you have access to a literature search tool (like `arxiv-mcp-server` or equivalent web search capability). If you do not have these tools available, **STOP and immediately alert the user to install/configure them** (e.g., updating their `mcp_config.json` to include `arxiv-mcp-server`). Do not proceed until you have the capability to find real literature.
2. **Ask for Core Context**: Ask the user for their specific research topic, major, and preliminary ideas.
3. **Automated Search**: Use subagents or `arxiv-mcp-server` to gather at least **40 REAL, existing academic papers**. You must collect Author, Title, Journal, and Year for each.

### Phase 2: Iterative Drafting (Section by Section)
**CRITICAL**: You must output ONLY ONE section per turn. Wait for user approval before generating the next. 

**NEW REQUIREMENT**: For *every* section you generate, you MUST create and output a separate markdown file named `reference_basis_section_[X].md` (e.g., `reference_basis_section_1.md`). This file must explicitly detail the reference basis for all content generated in that section, explaining which papers, theories, or data support each specific claim and paragraph. 

**Section 1: 立论依据 (Argument Basis) - Target: ~2000 words**
You must strictly format and deeply expand on these 6 sub-points. Write approx. 300-400 words *per sub-point*:
- 1.1 课题来源 (Source of the project)
- 1.2 选题依据 (Basis of the chosen topic)
- 1.3 背景情况 (Background)
- 1.4 课题研究目的 (Research objectives)
- 1.5 理论意义 (Theoretical significance)
- 1.6 实际应用价值 (Practical application value)
*(Generate `reference_basis_section_1.md`. Wait for user approval)*

**Section 2: 文献综述 (Literature Review) - Target: ~3000 words**
Write approx. 1000-1500 words per major sub-point:
- 2.1 国内外研究现状 (Must be further subdivided into 2.1.1, 2.1.2, etc.)
- 2.2 所阅文献的查阅范围及手段
  - 2.2.1 查阅范围 (Scope of literature reviewed)
  - 2.2.2 查阅手段 (Methods of literature review)
*(Generate `reference_basis_section_2.md`. Wait for user approval)*

**Section 3: 研究内容 (Research Content) - Target: ~3500 words**
Write approx. 500-600 words per minor sub-point:
- 3.1 学术构想与思路、主要研究内容及拟解决的关键技术
  - 3.1.1 学术构想 (Academic ideas and thoughts)
  - 3.1.2 主要研究内容 (Main research content)
  - 3.1.3 拟解决的关键技术 (Key technologies to be solved)
- 3.2 拟采取的研究方法、技术路线、实施方案及可行性分析
  - 3.2.1 研究方法 (Research methods)
  - 3.2.2 技术路线与实施方案 (Technical route and implementation plan)
  - 3.2.3 可行性分析 (Feasibility analysis)
*(Generate `reference_basis_section_3.md`. Wait for user approval)*

**Section 4: 研究基础 (Research Foundation) - Target: ~500 words**
Write approx. 150-200 words per minor sub-point:
- 4.1 实验手段 (Experimental means)
- 4.2 研究条件 (Research conditions)
- 4.3 实验条件 (Experimental conditions)
*(Generate `reference_basis_section_4.md`. Wait for user approval)*

**Section 5: 查阅文献资料目录清单 (References)**
- Must list **strictly no less than 40 real references**. Format consistently.
*(Generate `reference_basis_section_5.md`. Wait for user approval)*

**Section 6: 工作计划 (Work Plan)**
- Create a milestone-driven timeline with concrete deliverables for each phase.

### Phase 3: DOCX Generation
Once all sections are drafted and approved, compile them into a python script that uses the `python-docx` library to populate the user's template. Since the text is extremely long (~10,000 words), the python script should write the drafted markdown parts into the template's placeholders. 
**CRITICAL FORMATTING REQUIREMENTS**: The generated DOCX script MUST strictly enforce the following page and paragraph styles:
- Page Margins: Top 2.5cm, Bottom 2cm, Left 3cm, Right 2.4cm.
- Paragraph Line Spacing: Exactly 22 pt (磅).
- Font Type & Size: SimSun (宋体), Xiaosi (小4号, 12 pt).
Execute the script and provide the final `.docx` to the user.
