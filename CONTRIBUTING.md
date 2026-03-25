# Contributing

Thanks for your interest in the Media Displacement Index. This is a small project and contributions are welcome.

## Adding a New Occupation

1. Find the occupation on the [BLS Occupational Outlook Handbook](https://www.bls.gov/ooh/)
2. Run it through the scoring prompt in `scoring-prompt.md` to get an AI Exposure score, rationale, and displacement stack
3. Look up employment and wage data from [BLS OES](https://www.bls.gov/oes/)
4. Add a new entry to `data/occupations.json` with all required fields:

```json
{
  "id": "your_occupation_id",
  "title": "Occupation Title",
  "employment": 50000,
  "medianWage": 65000,
  "jobChange10yr": 5,
  "outlook10yr": 3,
  "aiScore": 6.0,
  "aiRationale": "Your 2-3 sentence rationale.",
  "blsUrl": "https://www.bls.gov/ooh/...",
  "category": "Category Name",
  "displacers": ["Product 1", "Product 2", "Product 3"]
}
```

5. If your occupation belongs to a new category, add it to `data/categories.json` with a color
6. Update the `totalOccupations` and `totalWorkers` fields in the metadata

## Updating Scores

AI capabilities change. If you think a score is outdated:

1. Re-run the occupation through the scoring prompt with current context
2. Update the `aiScore`, `aiRationale`, and `displacers` in `occupations.json`
3. Note what changed and why in your PR description

## Adapting for a Different Industry

See the "Adapting to other industries" section in the README. The short version:

1. Fork the repo
2. Replace occupations in `data/occupations.json` with BLS occupations from your industry
3. Update categories in `data/categories.json`
4. Modify the scoring prompt anchors in `scoring-prompt.md` to reference your industry
5. Update the timeline if your industry has a different disruption history

## Code Style

- Keep it simple. Vanilla where possible.
- Data files are JSON. Keep them clean and consistently formatted.
- If you're modifying the visualization code, match the existing patterns.

## Submitting Changes

1. Fork the repo
2. Create a branch (`git checkout -b add-healthcare-occupations`)
3. Make your changes
4. Open a pull request with a clear description of what you changed and why
