# AI Exposure Scoring Prompt

Use this prompt to score occupations on a 0–10 AI Exposure scale. Copy it into your preferred LLM, then feed it a BLS occupation description. The model will return a score, rationale, and displacement stack.

---

## The Prompt

You are an expert analyst evaluating how exposed different media and communications occupations are to AI. You will be given a detailed description of an occupation from the Bureau of Labor Statistics.

Rate the occupation's overall AI Exposure on a scale from 0 to 10.

AI Exposure measures: how much will AI reshape this occupation? Consider both direct effects (AI automating tasks currently done by humans) and indirect effects (AI making each worker so productive that fewer are needed).

A key signal is whether the job's work product is fundamentally digital. If the job's primary output is text, translation, information synthesis, or pattern recognition — writing, editing, analyzing, communicating — then AI exposure is inherently high (7+), because AI capabilities in these domains are advancing rapidly. Even if today's AI can't handle every aspect of such a job, the trajectory is steep and the ceiling is very high. Conversely, jobs requiring physical presence, manual skill, live performance, or real-time human interaction in the physical world have a natural barrier to AI exposure.

### Scoring Anchors

Use these anchors to calibrate your score:

- **0–1: Minimal exposure.** The work is almost entirely physical, hands-on, or requires real-time human presence in unpredictable environments. AI has essentially no impact on daily work. Examples: camera operator on location, live event stage manager.

- **2–3: Low exposure.** Mostly physical or interpersonal work. AI might help with minor peripheral tasks (scheduling, paperwork) but doesn't touch the core job. Examples: sound engineer during live mixing, broadcast equipment installer.

- **4–5: Moderate exposure.** A meaningful portion of work involves information tasks that AI handles adequately, but the role also requires judgment, creativity, or presence that limits full automation. Examples: photographers (stock vs. editorial split), PR specialists (drafting vs. relationship management).

- **6–7: High exposure.** Most of the job's primary output is digital and pattern-based. AI tools are already used in production workflows. Significant compression of junior-level positions expected. Examples: graphic designers (volume work), film editors (rough-cut assembly), market research analysts.

- **8–9: Very high exposure.** The core task is text or content generation that AI can replicate at speed and scale. Multiple funded commercial products target this exact workflow. Human value shifts to oversight, taste, and exception handling. Examples: technical writers, reporters (routine coverage), translators (major language pairs).

- **10: Near-total exposure.** The entire job function can be performed by current AI systems with minimal human oversight. The occupation is in terminal decline due to automation, not market shifts. Example: proofreaders and copy markers.

### Output Format

For each occupation, provide:

1. **AI Exposure Score** (0–10, one decimal place)
2. **Rationale** — 2–3 sentences explaining the score
3. **Displacement Stack** — 3–5 specific commercial AI products that currently target this occupation's core workflow

---

## How to Use

1. Go to the [BLS Occupational Outlook Handbook](https://www.bls.gov/ooh/)
2. Find your target occupation
3. Copy the "What They Do" and "Work Environment" sections
4. Paste them into your LLM along with this prompt
5. Record the score, rationale, and displacement stack in your data file

## Adapting for Other Industries

This prompt was written for media and communications roles, but the scoring framework is industry-agnostic. To adapt:

1. Replace the examples in each scoring anchor with occupations from your target industry
2. Adjust the "key signal" paragraph if your industry has different AI-exposure patterns (e.g., in healthcare, the signal might be "whether the task involves diagnosis from structured data" rather than "whether the output is text")
3. Keep the 0–10 scale and output format the same so your data works with the visualization

## Limitations

- Scores reflect one model's judgment at one point in time
- LLMs may have training data biases about certain occupations
- AI capabilities change fast — scores should be refreshed periodically
- The prompt was calibrated for media roles; other industries may need anchor recalibration
