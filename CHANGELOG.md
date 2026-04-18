# Changelog

## All notable changes to Supermarket Simulator Profit Tracker will be documented here.

---

## [v2.9] - 2026-04-16

### Added

- Customization tab (5th tab) for store-level settings
- Store name setting: Displayed in the header below the logo
  - Store name included as metadata in CSV and JSON exports and restored automatically when importing a JSON backup
- Customizable Markup % Presets - define up to 5 personal markup buttons (+%) in the Customization tab. Buttons appear dynamically when editing a product's sell price.
  - Preset values save to localStorage and persist across sessions.
  - Preset values saved in JSON exports and imports. If no values detected (version 2.8 and older) will input default values
  - Reset to Defaults button restores presets to +2.5% / +5% / +7.5% / +10% / +15%.
- Market Price splited into "Market Price" and "Your Sell Price". The product table's price column is now three separate columns: Market Price, Your Sell Price, and Margin %. Both new columns are sortable (click header or multi-sort). Thi allows for better price visibility.
- Your Price field: Each product now tracks your actual sell price separately from the game's market price. Set it in the product detail panel when logging a price update.
- Sweet Spot Markup Indicator: A customizable coloured dot +/-xx% badge appears next to every product's margin across the app: 🟢 0-7% (safe), 🟡 7-10% (caution), 🔴 10%+ (complaint risk), 🟣 negative (below market).
- Live markup preview: While editing a product's prices, the markup badge updates in real time as you type. The profit preview box also shows a markup summary line.
- Margin % in price history: The history table in the product detail modal now shows Your Price and Margin % columns for each logged entry.
- Markup shown in Compare & Licence tabs: Product cards in the Compare and By Licence views now display Market Price, Your Price, and the markup badge.
- Sweet Spot legend in Customization tab: A new section explains the three colour zones and how the markup is calculated.
- Auto-fill: entering a new market price now automatically defaults your sell price to that value
- Missing-price warning banner (bottom-right toast) listing affected products, shown on CSV import and on page load if saved data has gaps (auto-dismisses after 20s)
- Added inline warning box inside the product detail modal when either price is missing, with a specific message indicating which price(s) are absent
- Added ⚠ no prices indicator in the Online Profit columns of the main product table for affected rows
- Added "Online Only" option in the drop down storage type filter
- Dashboard Tab:
  -- Products visible: added "matching current filter" sub-label
  -- Products with prices logged: shows logged/total format with % data coverage to show how much product's price are changed from default values. Allow better visibility if products' price need to be changed from default.
  -- 🔴 Products in red zone: count of priced products exceeding the yellow markup threshold, with % of priced products affected shown below
  -- Margin health overview + Discount activity bar
  -- Needs attention table to show top 3 unpriced items (still on default values)
  -- Avg markup %: replaces "Avg online profit/box" - shows average markup % across actively priced products in the current filter view; color adapts to sweet spot thresholds (green / yellow / red / Purple)
  -- Market type breakdown in dashboard tab next to Storage type breakdown

- Added 🍦 Ice Cream Stand tab - appears automatically when the IceCream DLC is enabled, hides when toggled off

- Dashboard Widget Visibility section to the Customization tab: Each of the 11 dashboard panels can now be individually toggled on or off using toggle switches
- Widget visibility is now included in full JSON backups and restored on import
- Default tab on load setting in Customization tab: Pick which tab the app opens on (Dashboard, Products, Top Profit, License Content, Compare Products, or Customization). Saved to localStorage and included in settings exports/imports.
- Sweet Spot zone preview bar: A live color-coded gradient bar now appears above the Zone Reference box in the Sweet Spot section, showing purple / green / yellow / red zones proportionally. Updates in real time as you adjust the thresholds - no need to save first to see the effect.
- Settings Backup section in Customization tab: New dedicated section with Export Settings and Import Settings buttons. Export Settings downloads a lightweight JSON containing only your customization settings (sweet spot thresholds, markup presets, store name, default sort, widget visibility, default tab, table density) - no product data included. Import Settings restores those settings from either a settings-only export or a full backup JSON, without touching product data or price history.

### Changed

- Optimized Tracker App .html file to reduce size from ~350KB to ~250KB
- Bakery goods default prices updated from latest version 1.2.7
- Sell price markup buttons in the product modal are now driven by your saved presets instead of hardcoded values.
- Log a price update section reorganized
- Removed KNOWN_PROFITS static lookup table (158 lines of hardcoded profit data)
- Reorganized price update window layout
- Reorganized Dashboard Tab
- Table Density section renamed to Display Preferences: Now also houses the new Default Tab on Load setting, grouped together as visual/layout controls.
- Dashboard: Top Online Earners and Top Pickup Earners charts expanded from 7 to 10 entries
- Dashboard: Recent Price Changes log expanded from 8 to 15 entries
- Dashboard: Storage Type and Market Type donut charts enlarged to better match Recent Price Changes panel height

### Fixed

- Backwards compatible: Existing saves without a Your Price automatically default to the market price (0% markup) on load.
- Discount not reflected in markup badge
- Markup stale after deleting a history entry
- Dashboard markup showed current value instead of historical
- Products with missing MarketSellPrice or OnlineBuyPrice now correctly show no profit data instead of silently falling back to potentially stale hardcoded values
- Top Profit tab missing markup
- "Online buy price (per box)" field in the item detail modal now correctly pre-fills with the latest logged buy price from history, instead of the hardcoded default value. This also applies when restoring a JSON backup.

### Removed

- "Avg online profit/box" from dashboard tab: wasn't adding real value for user as box number was unknown. Replaced by "Avg markup %"
- "Online-only products ranked (no pickup)" table and repalced by "Online Only" option in the drop down storage type filter

---

## [v2.8] - 2026-04-10

### Added

- Discount Visibility: Discount status is now visible across the entire app whenever a product has an active discount on its latest saved entry
- "Unit/slot" column to the Product List (between Units/box and Slots/box), showing how many items fit per shelf slot
- Added Multi-sort to the Product List - a "⇅ Multi-sort" button in the table header opens a priority-based sort builder. Add up to 13 levels (one per column), each with its own field and Asc/Desc direction. Sort applies live. Clicking any column header resets back to single-column sort.
- Split the "Product" column in the Product List table into two separate columns: Category and Brand, allowing independent sorting on each
- Added Category and Brand filter dropdowns to the topbar, dynamically populated from product data. Both new filters stack with existing filters (search, storage, DLC, license)
  **Fully backward compatible with existing JSON backups and CSV imports (data structure unchanged)**
- Click-for-product-details function now works across all major views - not just the Products tab
  -- Dashboard: Recent price changes, Biggest movers, Most updated products, and Online-only products ranked are all now clickable
  -- Licence Content tab: product cards are now clickable
  -- Compare Products tab: product cards are now clickable
  -- Top Profit tab: all three leaderboard columns (Online/Box, Pickup/Box, Pickup Difference) are now clickable rows
- Extended row/card hover highlight to Leaderboard (Top Profit), Licence Content, and Compare Products tabs - clickable items now consistently light up across the whole app
- When importing a CSV that contains the same product name more than once, the app now detects the conflict and shows a warning modal before doing anything.
  You can choose:
  --Keep first occurrence - later duplicates are ignored
  --Keep last occurrence - earlier duplicates are overwritten
  --Cancel - import is aborted, nothing changes
- Cancelling the duplicate modal now fully cleans up pending state, so a subsequent import starts fresh.
- CSV rows with an empty Category field are now skipped automatically. The import result message tells you how many rows were skipped and why, instead of silently creating broken products.
- You can now see how many items you can fit in a storage slot (e.g.: shelf) and how many storage slots are needed to fit the content of one box.This allows for better planning.
- Added Unit/slot and Slots/box to multi-sort options

### Changed

- Reversed Multi-sort button state - now green (active-looking) by default, dims on hover; turns grey when multi-sort is actually in use. Multi-sort button is more visible for users to notice
- Produce stall items now display Slots/box = 1 instead of "-"
- Product detail panels now show Items/slot and Slots/box for produce stall (weight-based) products
- The error message when saving a price now says "both must be greater than 0" instead of the vague "please enter both prices"
- Product table: rename "Units" --> "Units/box" and add "Slots/box" column header
- Compare tab cards: add Items/slot + Slots/box rows after Items/box
- License tab cards: add Items/box, Items/slot + Slots/box rows after Storage
- Search now also matches brand names, not just product name and category
- "License Content" tab now shows a helpful message when you're in Storage view instead of a confusing prompt
- Consistent spelling: "Strawberry Flavour" now matches the other ice cream products
- Consistent spelling: tab renamed from "Licence Content" to "License Content" to match the rest of the app
- Dark/Light mode toggle now visually behaves the standard way (on = light, off = dark)
- You can now press Escape to close any open popup

### Fixed

- Fixed backward compatibility bug where importing any saves from before the Category/Brand column split (versions prior to 2.8) would result in merging columns back, missing or undefined category and/or brand fields. Old saves are now fully backward compatible.
- Dashboard Tab "Top 7 - Pickup profit/box" chart now displays a "No pickup option available" message instead of a broken empty graph when no pickup-eligible products are visible in the current selection
- "Top 7 - Online profit/box" dashboard chart no longer glitches when no licences are selected - now shows a clean "No products available in the current selection." message, consistent with the Pickup chart behaviour.
- Fixed Slots/box column sorting (was incorrectly sorting by ShelfCap instead of the computed slots per box value)
- Dashboard charts: Hovering over a bar now shows the full product name in the tooltip, even when the axis label is truncated (e.g.: "Cutlery Set - Silver..."). Affects the Top 7 Online, Top 7 Pickup, and Profit Margin % charts
- Product details: Items per box vcalue (or Weight per box for some items) is now always visible in the stats panel, including for products without a pickup option
- Close button on product detail window is now a square with a full clickable area (no more precision clicking on the x character)
- Fixed "Pineappel" typo --> "Pineapple"; old backups are automatically corrected on restore.
- When erasing a price history entry in product details' window opened from any part of the dashboard tab the graph disapears
- Discount banner no longer overlaps the close button
- The average profit shown on the dashboard was lower than it should be because products without any price data were being counted as $0
- Products with no prices could incorrectly appear in "Top 7" and leaderboard rankings
- After typing a price in the product detail popup and then clearing it, a ghost "Preview" tick would remain stuck on the chart's timeline
- Custom storage types added via CSV import had unreadable badge colours when using Light mode
- Entering a negative or zero sell price would be silently saved without any warning
- Dashboard average profit no longer shows "NaN" when some products have no price data
- Profit progress bars in the product table no longer break on empty or negative values
- Sorting by the "Discount" column now actually works (both single-click and multi-sort)
- CSV import with duplicate product names no longer risks silently losing data mid-flow
- Product names from imported CSVs are now sanitized to prevent script injection (Malicious CSV content can't execute scripts. No visual change for normal data)
- Eggs profit data now correctly matches its product entry (was mismatched due to a naming typo)
- CSV header detection no longer accidentally skips data rows in edge cases
- After clicking "Reset All", any active sorting configuration from the multi-sort panel would survive the reset
- Toggling off a license group that was selected in the sidebar would leave the sidebar in a broken highlighted state
- Filters, license chips and DLC chips were being rebuilt twice every time the app loaded, doing unnecessary work
- On a completely fresh install (no saved data), the filter dropdowns and license/DLC bars could appear empty
- Product names containing special characters imported from a CSV could potentially break parts of the interface
- CSV Import: HasPickup column now defaults to false when blank or unrecognised, instead of silently treating the product as having pickup
- CSV Import: values containing commas are now handled correctly (quoted fields per RFC-4180 are no longer misparsed)
- CSV Import: license IDs are now consistently treated as strings, preventing filter chip mismatches after importing
- CSV Import: sidebar group selection is now reset after an import, preventing a stale/empty view
- JSON Restore: sidebar group selection is now reset after restoring a backup
- JSON Restore: license IDs are normalised to strings on restore, same as import
- Reset All: sidebar selection and view mode are fully reset (was leaving a stale active group and "By Storage/License" state)
- Duplicate price history entries are no longer created if you save the same product twice on the same day with the same prices - the existing entry is updated instead
- Storage full error now always displays even if you had previously dismissed the warning banner
- "Download CSV Template" now exports true default data, not your current edited prices (that's what "Export Current CSV" is for)
- Stars rating no longer shows stale values after an import that removes all pickup products
- License chip colours are correctly reassigned after a Reset All, CSV import, or JSON restore
- Products with no known prices showed $0.00 profit instead of "-" unconfigured products were initialized to 0 instead of null, making them appear as zero-profit items in tables and averages. They now correctly display a dash.

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
