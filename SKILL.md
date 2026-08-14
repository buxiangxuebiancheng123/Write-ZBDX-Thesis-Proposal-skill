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
- **Using an "AI Tone" (AI味).** Do NOT append English translations in parentheses after every technical term (e.g. do not write "人工智能(Artificial Intelligence)"). Do not use flowery, overly enthusiastic, or marketing-like language. Maintain a highly objective, rigorous, plain, and third-person academic tone.
- **Lack of rigorous logic ("假大空")**. When discussing feasibility or research gaps, you must provide concrete academic and mathematical/technical reasoning. Generic claims like "We have algorithms, so it is feasible" are strictly prohibited.

## The Workflow (Strictly Iterative)

### Phase 1: Prerequisite Check, Topic Alignment & Literature Gathering
1. **Prerequisite Check**: Before starting, check your available tools. You MUST verify that you have access to the `paper-search-mcp` server. If you do not have this tool available, **STOP and immediately alert the user to configure it**. Do not proceed until you have the capability to find real literature.
2. **Ask for Core Context**: Ask the user for their specific research topic, major, and preliminary ideas.
3. **Automated Search**: Use subagents or the `paper-search-mcp` server to gather at least **40 REAL, existing academic papers**. 
   - **CRITICAL ACADEMIC REQUIREMENT**: You MUST heavily prioritize retrieving literature from **top-tier journals (顶刊)** or papers that have been **officially accepted** by reputable journals/conferences. Avoid low-quality or predatory sources. You must collect Author, Title, Journal, and Year for each.

### Phase 2: Iterative Drafting (Section by Section)
**CRITICAL**: You must output ONLY ONE section per turn. Wait for user approval before generating the next. 

**NEW REQUIREMENT 1 (Dual-Track Reference)**: For *every* section you generate, you MUST create and output a separate markdown file named `reference_basis_section_[X].md` (e.g., `reference_basis_section_1.md`). This file must explicitly detail the reference basis for all content generated in that section.

**NEW REQUIREMENT 2 (Context Preservation)**: Because this is a massive multi-part task, you risk forgetting early core constraints by the time you reach Section 6. Therefore, at the very end of EVERY section's markdown file, you MUST append a hidden `<context>` block. In this block, briefly summarize the core thesis statement, specific constraints, and key decisions made so far. This will ensure your future self maintains perfect memory across the iterative process.

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
  - **CRITICAL ACADEMIC REQUIREMENT**: At the very end of this sub-point, you MUST explicitly define the "关键科学问题 (Scientific Problem)" and "当前研究空白 (Research Gap)" using a strict "What has been done -> What is missing -> Why it matters" logical chain.
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
    - **CRITICAL ACADEMIC REQUIREMENT**: You MUST include a `Mermaid` flowchart code block here representing the step-by-step algorithm/system architecture, followed by extremely detailed text explaining the flowchart.
  - 3.2.3 可行性分析 (Feasibility analysis)
    - **CRITICAL ACADEMIC REQUIREMENT**: You MUST explicitly break this down into three strict sub-dimensions: 理论可行性 (Theoretical Feasibility), 技术可行性 (Technical Feasibility), and 实验条件可行性 (Platform/Data Feasibility). Avoid generic claims.
*(Generate `reference_basis_section_3.md`. Wait for user approval)*

**Section 4: 研究基础 (Research Foundation) - Target: ~500 words**
Write approx. 150-200 words per minor sub-point:
- 4.1 实验手段 (Experimental means)
- 4.2 研究条件 (Research conditions)
- 4.3 实验条件 (Experimental conditions)
*(Generate `reference_basis_section_4.md`. Wait for user approval)*

**Section 5: 查阅文献资料目录清单 (References)**
- Must list **strictly no less than 40 real references**. 
- **CRITICAL ACADEMIC REQUIREMENT**: You MUST format all citations strictly following the Chinese national standard **GB/T 7714-2015** (《信息与文献 参考文献著录规则》).
*(Generate `reference_basis_section_5.md`. Wait for user approval)*

**Section 6: 工作计划 (Work Plan)**
- Create a milestone-driven timeline with concrete deliverables for each phase.

The following optimizations have been injected into `write-thesis-proposal`:

1.  **Red Flag Against "假大空" (Empty Claims):** Added a rule preventing the agent from making generic claims about feasibility or research gaps without rigorous academic reasoning.
2.  **Explicit Research Gap (Section 2.1):** Enforced a strict logical chain ("What has been done -> What is missing -> Why it matters") to clearly define the "Scientific Problem" and "Research Gap."
3.  **Visual Technical Route (Section 3.2.2):** Demanded the generation of a `Mermaid` flowchart to visually explain the system architecture/algorithm step-by-step.
4.  **Tri-dimensional Feasibility Analysis (Section 3.2.3):** Forced the breakdown of feasibility into Theoretical, Technical, and Platform/Data dimensions.
5.  **GB/T 7714-2015 Citation Standard (Section 5):** Hardcoded the requirement to format the 40+ references strictly according to the Chinese national academic standard.
