Prompt Engineering Good Practices Guide

A reference for designing clear, effective prompts for LLMs.

1. Clarity and Precision

State the objective explicitly: Instead of “Explain Python”, write “Explain Python’s list comprehensions with examples for beginners”.

Avoid ambiguity: Use specific verbs like “summarize,” “generate,” “compare,” “rewrite” rather than “talk about”.

Anchor key terms: If a concept has multiple meanings, define which sense you want (e.g., “ontology in philosophy, not computer science”).

Set scope: Mention depth (overview vs. technical deep dive) and length (short explanation vs. detailed report).

2. Context and Background

Provide necessary context: Include background details so the model doesn’t need to infer.

Define target audience: Say whether the output is for experts, beginners, executives, children.

Include constraints from reality: e.g., “using data up to 2023,” “following academic citation style”.

Explain motivation: Indicate why you’re asking. Example: “I need this for a training presentation”.

3. Structure and Formatting

Use lists, steps, or sections: Guides the model to organize output clearly.

Request structured output: JSON, markdown, tables, bullet points, or code blocks for easy parsing.

Leverage templates: Provide an example format for the model to replicate.

Separate tasks: Break complex requests into steps rather than asking for everything in one go.

4. Instruction Hierarchy

Prioritize main instruction: Place the most important goal first.

Supplement with secondary rules: Style, tone, constraints afterward.

Be explicit about exclusions: Tell the model what not to include (e.g., “Don’t repeat examples”).

Encourage reasoning: If needed, request “explain the reasoning before answering”.

5. Control Over Output

Tone and style: Specify (formal, casual, academic, technical, biblical, etc.).

Length control: e.g., “3–5 sentences,” “under 200 words,” “detailed step-by-step”.

Level of detail: “High-level overview,” “granular implementation steps”.

Perspective: e.g., “as a mentor,” “as a project manager,” “from a biblical worldview”.

6. Iteration and Refinement

Start broad, then narrow: First get an overview, then request deeper dives.

Use follow-ups to refine: Adjust tone, scope, or level of detail incrementally.

Test variations: Change phrasing to see which prompt yields the most useful results.

Chain prompts: Use previous outputs as inputs to build layered reasoning or content.

7. Constraints and Guardrails

Explicit boundaries: e.g., “Only use open-source tools,” “Don’t assume internet access”.

Time or domain limits: e.g., “Focus on 2020–2023 trends,” “Discuss only New Testament references”.

Resource constraints: “Assume low memory hardware,” “Use only vanilla JavaScript”.

8. Creativity and Exploration

Allow alternatives: Ask for “3 possible approaches” instead of a single solution.

Role-play prompts: e.g., “You are a cybersecurity auditor. Review this system.”

Perspective switching: Request the same explanation from multiple viewpoints.

Encourage analogies and examples: Useful for abstract concepts.

9. Verification and Reliability

Request sources: e.g., “Cite academic references where possible”.

Cross-check prompts: Ask for summaries, then ask the model to challenge or critique them.

Fact-check via comparison: Request pros/cons, counterarguments, or common misconceptions.

Force self-checks: e.g., “Review your answer for contradictions before finalizing”.

10. Efficiency and Usability

Reusable phrasing: Keep templates for summarization, coding, teaching, brainstorming, etc.

Prompt chaining: Feed structured intermediate outputs into later prompts.

Decompose tasks: Write prompts that isolate subtasks instead of one catch-all.

Automate consistency: Define standards (e.g., “Always respond in Markdown with headers”).

11. Advanced Techniques

Few-shot prompting: Provide examples of desired input/output pairs.

Zero-shot with role context: Define roles instead of examples: “Act as a senior Python developer…”.

Multi-step reasoning: Ask for reasoning first, then a concise final output.

Meta-prompts: Ask the model to generate an improved version of your own prompt.

Contrastive prompting: Request both what something is and what it is not.

12. Ethical and Bias Awareness

Be explicit about worldview: If you want a Christian, scientific, or neutral frame, state it.

Request limitations disclosure: Ask the model to highlight assumptions and uncertainties.

Avoid hidden bias: Specify “balanced overview” when you need objectivity.

Quick Prompt Checklist before sending:

Is the goal clear?

Is the audience defined?

Is the scope/format specified?

Are there constraints and what to avoid?

Do I want depth vs brevity?

Did I structure it for clarity?
