# The Media Displacement Index

**An open-source, interactive visualization mapping AI displacement risk across 22 media and communications occupations.**

![Screenshot](screenshot.png)

**[See it live →](https://crestwood.digital/media-displacement-index)**

---

## What is this?

The Media Displacement Index maps 22 Bureau of Labor Statistics occupations — representing 2.8 million workers in media and communications — against four data layers:

- **AI Exposure** — a 0–10 score measuring how much AI is reshaping each role
- **10-Year Job Change** — actual employment change from 2013–2023
- **BLS Outlook** — projected change from 2022–2032
- **Median Wage** — annual median wage for each occupation

Each occupation also includes a **Displacement Stack**: the specific commercial AI products currently targeting that role's core workflow. Not theoretical — products with funding, users, and traction.

Inspired by [Andrej Karpathy's US Job Market Visualizer](https://karpathy.github.io/bm/).

## The Three-Act Structure

The visualization tells its story in three acts:

**Act I: The Collapse Already Happened.** A timeline showing that newspaper employment dropped 77% — from 375K jobs to 87K — *before* generative AI arrived. The disruption everyone fears already played out, driven by the internet, not AI.

**Act II: The Treemap.** An interactive treemap sized by employment, colored by your chosen data layer. Click any occupation to see its AI Exposure rationale, displacement stack, and BLS data. Toggle between layers to see the story shift.

**Act III: What's Growing.** Not everything is declining. Producers & Directors (+14%), Multimedia Artists (+16%), and Market Research Analysts (+18%) are growing — because AI augments the orchestrator, not replaces them.

## Data Sources

| Source | What it provides |
|--------|-----------------|
| [BLS Occupational Outlook Handbook](https://www.bls.gov/ooh/) | 10-year projections (2022–2032), job descriptions |
| [BLS Occupational Employment & Wage Statistics](https://www.bls.gov/oes/) | Employment counts, median wages (May 2023) |
| [Pew Research Center](https://www.pewresearch.org/) | Newspaper employment trends |
| [Northwestern Medill State of Local News 2024](https://localnewsinitiative.northwestern.edu/) | Local news decline data |

## AI Exposure Methodology

Each occupation was scored on a 0–10 AI Exposure scale by [Claude](https://claude.ai) (Anthropic) using a structured prompt that evaluates four factors:

1. **Output overlap** — Is the job's primary output something AI can produce? (text, translation, analysis, pattern recognition)
2. **Commercial products** — Do funded, shipping AI products already target this workflow?
3. **Verification difficulty** — How hard is it for a non-expert to verify AI output quality?
4. **Physical presence** — Does the job require being somewhere, touching something, or performing live?

The full scoring prompt is published in [`scoring-prompt.md`](scoring-prompt.md) so you can inspect, critique, or adapt it.

### Honest limitations

- These scores represent one model's judgment at one point in time. They are directional, not definitive.
- The prompt was designed for media/communications roles. Applying it to other industries may require recalibration.
- AI capabilities are moving fast. A score of 4 today could be a 7 in 18 months.
- We publish the prompt precisely so you can disagree with us and do it better.

## Tech Stack

- [React](https://react.dev/) + [TypeScript](https://www.typescriptlang.org/)
- [D3.js](https://d3js.org/) (treemap layout)
- [Tailwind CSS](https://tailwindcss.com/) (styling)
- [Framer Motion](https://www.framer.com/motion/) (animations)

## Run Locally

```bash
git clone https://github.com/crestwood-digital/media-displacement-index.git
cd media-displacement-index
npm install
npm run dev
```

## Remix It

This project is designed to be forked and adapted. Here's how:

### Add or edit occupations
Edit `data/occupations.json`. Each occupation needs an `id`, `title`, `employment`, `medianWage`, `jobChange10yr`, `outlook10yr`, `aiScore`, `aiRationale`, `blsUrl`, `category`, and `displacers` array. The treemap, key panel, and tooltips adapt automatically.

### Update the AI scores
Copy the prompt from `scoring-prompt.md` into your preferred LLM. Feed it a BLS occupation description. Paste the score and rationale back into `occupations.json`.

### Adapt for a different industry
This is the one we're most excited about. The scoring framework is industry-agnostic. You could build:

- **Healthcare Displacement Index** — nurses, radiologists, medical coders, therapists
- **Legal Displacement Index** — paralegals, contract attorneys, compliance officers
- **Finance Displacement Index** — analysts, auditors, loan officers, traders
- **Education Displacement Index** — tutors, instructional designers, administrators

**To do it:**

1. Fork this repo
2. Replace the occupations in `data/occupations.json` with BLS occupations from your target industry
3. Update `data/categories.json` with your industry's natural groupings
4. Run each occupation through the scoring prompt (swap in your industry context)
5. Ship it

The visualization code doesn't care what industry the data represents. It reads the JSON and renders.

## License

[MIT](LICENSE) — do whatever you want with it.

## Credits

Built by [Crestwood Digital](https://crestwood.digital). Inspired by [Andrej Karpathy](https://karpathy.ai/).

Data from the U.S. Bureau of Labor Statistics. AI Exposure scores generated by Claude (Anthropic).

---

*If you build a version for your industry, we'd love to see it. Open an issue or tag [@cabornemedia](https://x.com/cabornemedia).*
