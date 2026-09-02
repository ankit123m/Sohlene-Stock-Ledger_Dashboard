<img width="1047" height="776" alt="image" src="https://github.com/user-attachments/assets/118ff1c4-4f14-4642-98d6-23f3239662e3" />

<img width="431" height="431" alt="4wr6r7hp-qr" src="https://github.com/user-attachments/assets/df72d86f-62cb-4205-ac64-97a2feb9644e" />

[README.md](https://github.com/user-attachments/files/31724166/README.md)
# Sohlene Stock Ledger

An interactive stock dashboard for Sohlene's daily jewelry stock count, built as a single self-contained HTML page. It reads directly from a Google Sheet, so entering a new day's count in the sheet updates the dashboard automatically — no manual export or re-upload needed.

Built with **Claude AI** (Anthropic), from a raw daily-count spreadsheet through to a live, filterable dashboard.

## Data source

Pulls live from a published Google Sheet (`Daily_Stock_Count`), reading these columns: Date, Rings, Earrings, Bracelet, Bangle, Necklace, Pendant, RFS, Stone, Approval, Ring Collet, Detachable rings, Added to stock, Sent for repair, Sale, Total. If a live fetch is ever blocked (e.g. in a restricted preview), the dashboard falls back to the last successfully synced snapshot so it's never blank.

## KPIs

- **Pieces in stock (filtered)** — current total for the active categories and date range, with a +/− delta vs. the previous entry
- **Added to stock** — units added, summed over the selected range
- **Sold** — units sold, summed over the selected range
- **Sent for repair** — units sent for repair, summed over the selected range
- **Net change since [start date]** — stock change from the first to the last day in range
- **Largest category** — the highest-count category on the latest date, with its value
- **Average total stock** — mean daily total across the selected range
- **Days in range** — number of dated entries currently in view

## Charts

1. **Area chart** — total stock over time
2. **Horizontal bar chart** — stock by category, latest date
3. **Pie chart** — stock composition, latest date
4. **Grouped bar chart** — added / sold / repaired, per entry (last 15 shown)
5. **Stacked area chart** — each category's share of stock over time

## Filters

- **Date range** — quick filters for last 7, 14, 30 days, or all time
- **Category toggles** — chips to show/hide individual categories; KPIs and charts recalculate live from whichever categories are active
- **Entries table** — the 10 most recent dated rows in range, for a quick raw-numbers check alongside the charts

## Tech

Plain HTML/CSS/JS, [Chart.js](https://www.chartjs.org/) for charts, and [PapaParse](https://www.papaparse.com/) to parse the CSV pulled from Google Sheets. No build step, no backend — open the HTML file in any browser.

## Setup

1. In Google Sheets: **File → Share → Publish to web**, select the correct sheet tab, format **CSV**, and publish.
2. Drop the resulting link into the `CSV_URL` / sheet-connect step in the HTML file.
3. Host the file anywhere static (GitHub Pages works well) — Google's publish link needs `https://`, not a local file, to sync reliably.
