# CMU Per Diem Meal & Incidentals Calculator

A self-service tool for Carnegie Mellon University travelers to calculate per diem meal and incidentals reimbursement amounts per the [CMU Business Travel Expense Policy](https://www.cmu.edu/policies/financial-management/business-travel-expense.html).

## Quick Start

1. Open `index.html` in any modern web browser
2. For domestic travel: select state, then city from the dropdowns
3. For international travel: select country, then city from the dropdowns
4. Enter your travel dates and generate the daily grid
5. Check off any meals to deduct (provided by conference, or not available due to travel)
6. Print the page or use **Print → Save as PDF** to attach to your reimbursement request

No API keys, no server, no internet required — all rate data is bundled in the HTML file.

## Updating Rates

All rates are embedded directly in `index.html`. Update once per year when new fiscal year rates are published.

### Domestic (CONUS) Rates
- **Source:** [GSA FY Per Diem Master Rates File](https://www.gsa.gov/travel/plan-book/per-diem-rates/per-diem-files)
- **When:** New rates published mid-August, effective October 1
- **How:** Download the Excel file, extract city/state/M&IE/lodging data, update the `domesticRates` array
- **Also update:** `mieBreakdownTable` if GSA changes the M&IE tier breakdowns
- **Standard rate:** Cities not listed use the CONUS standard rate ($68 M&IE, $110 lodging for FY2026)

### International (OCONUS) Rates
- **Source:** [State Dept Office of Allowances](https://allowances.state.gov/web920/per_diem.asp)
- **How:** Update the `internationalRates` array in the `<script>` section
- **Meal breakdown:** Uses federal formula — Breakfast 15%, Lunch 25%, Dinner 40%, Incidentals 20%

## Calculation Rules

| Rule | Detail |
|------|--------|
| First/last travel day | 75% of daily M&IE rate |
| Extended stay (>30 days) | 60% of daily M&IE rate |
| Transition day (city change) | Full rate at new city; deduct unavailable meals via checkboxes |
| Provided meals | Meal component deducted; incidentals always included |
| Non-employees | Must use actual receipts (this tool is for per diem employees only) |

## No Server Required

This is a single-page client-side application. No installation, no build step, no backend, no internet connection needed. Just open the HTML file in a browser.
