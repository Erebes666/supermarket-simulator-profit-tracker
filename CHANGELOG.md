# Changelog

## All notable changes to Supermarket Simulator Profit Tracker will be documented here.

---

## [v2.7] - 2026-04-07

### Fixed

- Storage errors are no longer silent: if the browser's 5 MB localStorage limit is ever hit, a visible red warning banner now appears explaining that the last save failed and prompting you to export a backup.

### Added

- Live graph preview
  - The profit history chart now updates live as you type prices or move the discount slider - showing where the new entry would land before you save it
    Preview lines are removed automatically if you cancel or clear the inputs

- Price adjustment buttons updated: replaced -10% / -5% with Reset and +15%, buttons are now Reset · +2.5% · +5% · +10% · +15%
- Reset restores the market sell price field to the last saved value

- Discount Tracking
- Discount slider : New row in the "Log a price update" section below the ±% quick buttons. Drag from 0% (OFF) to 100% to apply a discount to the market sell price before saving. The row turns red when active and displays the selected percentage live.
- Live preview with discount. The preview panel now shows discounted profits alongside "No disc: $X" reference values so you can compare both before committing.
- Discount badge in history. Entries saved with a discount show a 🏷 -X% badge in the price history list. Entries without a discount are unchanged.
- Undiscounted reference lines in chart. When any history entry has a discount, the profit chart gains two dotted lines (green = Online/box, blue = Pickup/box) showing what profits would have been without the discount. The dotted lines merge with the solid lines at non-discounted entries and branch away at discounted ones, giving a clear visual of the discount's impact over time.
- Backward compatible - Existing history entries and backups are unaffected; the new fields (discountPct, undiscountedOnlineBoxProfit, undiscountedPickupBoxProfit) are only added when a discount is actually used.
- Zero line on the chart - a thin red dashed line is drawn at y=0, but only when at least one data point actually goes negative. If all values stay positive the line stays hidden, so it won't clutter charts with healthy margins.

### Changed

- Price history is now capped at 25 entries per product (1 default + 24 manual). When the cap is reached, the oldest manual entry is removed to make room for the new one after closing and reopening in browser. The default entry is always preserved.
- Aligned price history table - the history section is now a proper <table> with fixed columns: Date | Market $ | Buy $ | Online/box | Pickup/box (if applicable) | Discount (column only appears if any entry has a discount) | Δ Profit | delete button. Each column aligns cleanly across all rows, and the header row has a subtle background to distinguish it.
- Charts: Switched from smooth/curved lines to straight lines for more accurate data representation between data points.

---

## [v2.6] - 2026-04-06

### Fixed

- Fixed "Recent price changes" on the Dashboard not updating live after editing a product price.

### Added

- Added new Licence Content tab between Top Profit and Compare
  - Selecting a licence in the sidebar automatically loads all its products into the tab - no manual selection needed
  - Displays per-product comparison cards with best ↑ / worst ↓ metric highlighting (online profit, pickup profit, pickup advantage)
  - Includes a Profit comparison bar chart when 2+ products are present
  - Includes an Online profit/box history line chart at the bottom, with dotted extensions for products with fewer logged updates - mirrors the Compare tab behaviour
  - "All" group is intentionally excluded from this tab (use the Compare PRoduct tab for free-form multi-product comparison)

- Compare Product tab: the lowest profit figure for each metric is now highlighted in red with a ↓ arrow, matching the existing green ↑ arrow behaviour for the best value.
  This applies to all five compared metrics. Products marked as "N/A" for pickup metrics are correctly excluded from the worst-value calculation, so they won't be unfairly flagged.
  If all compared products share the same value for a metric, no arrows are shown in either direction.
- Compare Product tab: products with fewer price history entries now extend to the full x-axis with a dotted line and endpoint dot, making it easier to compare current values across all products at a glance. Hovering the endpoint dot shows the product's latest profit value.

- Storage type breakdown pie chart now displays percentage labels with thin pointer lines extending outside each slice, colour-matched to the slice. The legend below also shows the percentage alongside the product count. Slices under 2% are skipped to avoid cramped labels.

### Changed

- Compare tab was renamed to Compare Product
- Increased "Biggest movers from default" on the Dashboard from 6 to 13 entries
- Dashboard - Recent price changes: Fixed the panel to show all logged price entries across all products, sorted by true insertion order (newest entry first). Previously only the latest entry per product was shown, sorted by delta size. Now every individual change is listed chronologically, so the most recently logged update always appears at the top regardless of in-game date or change magnitude.
- Dashboard - Recent price changes: Deletions made from the product detail modal now immediately reflect in the dashboard panel while it is open.
- Increase font size in the Dashboard - Storage type breakdown legend

---

## [v2.5] - 2026-04-05

### Added

- Ability to delete price entries individually

---

## [v2.4] - 2026-04-04

### Added

- 💾 Backup button - exports a full JSON backup (products, price history, DLC settings) to your computer, named with the current date
- Added ↩ Restore button - restores a JSON backup file, replacing all current data after confirmation

### Updated

- Warning banner to reflect the new backup/restore workflow

---

## [v2.3] - 2026-04-03

### Added

- Toggle line above DLC section for every Licence. Allow for better visibility when strating a new game

---

## [v2.2] - 2026-04-02 - public

### Added

- Warning banner at the top of the app informing users about browser-only data storage
- Banner dismisses smoothly and reappears every session as a reminder

---

## [v2.1] - 2026-04-01 - not public

### Added

- Possibily to export and import CSV

---

## [v2.0] - 2026-03-13 - not public

### Added

- Toogle Light mode

---

## [v1.0] - 2026-02-1 - not public

- Initial release
