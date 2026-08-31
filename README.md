# Water Quality Log — Form & Dashboard (prototype)

Single-file web app: `index.html`. Contains a data-entry form matching the paper
Water Quality Log, plus a dashboard (date filtering, trend charts, sortable
table, CSV export). Pre-seeded with one year of synthetic sample data
(`sample-data.xlsx` has the same data set as a spreadsheet).

## Push this to GitHub

```bash
git init
git add .
git commit -m "Water quality log prototype"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

Or create the repo on github.com first and use its "upload files" button to
drag `index.html` in directly — no command line needed.

## Viewing it live (optional)

GitHub Pages will serve `index.html` as a live URL: repo Settings → Pages →
deploy from the `main` branch. Good for sharing the look and feel, or for
iterating on which metrics/charts the dashboard should show.

**Important limitation:** GitHub Pages only hosts static files. The form
currently saves each submission to the visitor's own browser (`localStorage`),
so two people opening the page don't see each other's entries — fine for
mocking up metrics, not for real multi-user capture. Turning this into a
real shared form + dashboard (everyone's readings landing in one place) needs
a small backend and database, per the rollout plan.

## Editing the dashboard metrics

All the logic is in the `<script>` block near the bottom of `index.html`:

- `FIELD_DEFS` — the list of form fields, their types, and validation ranges.
- `renderStats()` — the summary numbers at the top of the dashboard.
- `renderCharts()` — the four charts (chlorine, pH, alkalinity/hardness, bather count).
- `renderTable()` — the sortable readings table.

Add or change a metric by editing the relevant function — no build step, just
edit and reload the file in a browser.
