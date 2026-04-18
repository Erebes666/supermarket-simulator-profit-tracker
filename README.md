# 🛒 Supermarket Simulator - Profit Tracker

An unofficial fan-made profit tracking tool for [Supermarket Simulator](https://store.steampowered.com/app/2670630/Supermarket_Simulator/). Log your market prices, track your own sell prices, calculate online vs pickup profits, compare products side by side, and visualise your most profitable items - all in a single HTML file that runs directly in your browser with no installation required.

> **Disclaimer:** This is an unofficial fan-made tool, not affiliated with or endorsed by Nokta Games. All game content, product names, and trademarks belong to their respective owners.

> 🌍 _The interface is in English but the tool is straightforward to use - just open the file in your browser._

![App screenshot](https://github.com/Erebes666/supermarket-simulator-profit-tracker/blob/main/Assets/SuperMarketTracker_UI1.png)

---

## 📁 Repository contents

| File | Description |
| -------------------------------------------- | ------------------------------------------- |
| `supermarketSimulator-tracker_v2_9.html` | The app - open this in your browser |
| `supermarket-tracker-template.csv` | Default product data for game version 1.2.1 |
| `LICENSE` | MIT licence |
| `README.md` | This file |
| `Assets` | Screenshots and gifs of the UI |
| `CHANGELOG.md` | List of changes for each version |

---

## 🚀 How to use

1. Download `supermarketSimulator-tracker_v2_9.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. That's it - no install, no server, no account needed

Your data is saved automatically in your browser's local storage and persists between sessions as long as you use the same browser.

> **Private/Incognito mode:** All browsers block localStorage in private browsing: your data won't be saved in that mode. Use a normal window.

---

## ⚠️ Data & Storage Warning

All your data (prices, edits, settings, price history) is saved **locally in your browser only**.
Clearing your browser history, cache, or site data will **permanently delete everything** - there is no recovery.

**Exporting to CSV does NOT save everything.**
The CSV only backs up your product list and prices. Your price history, stars, and settings are not included in the export and will be lost if you clear your browser data.

To save your price history, stars, and settings, use the **Backup** function regularly. This creates a JSON file with everything (price history, stars, settings, etc.).
To restore it, use the **Restore** function and select the JSON file.

If your browser's 5 MB localStorage limit is ever reached, a red warning banner will appear at the top of the app prompting you to export a backup.

---

## 🔄 Keeping up with game updates

The app ships with built-in default data for **game version 1.2.7**. If the game gets updated and prices or products change, you can update the data yourself using the CSV file - no need to wait for an app update.

### How to update product data

1. Open `supermarket-tracker-data-v1.2.1.csv` in any spreadsheet app (Excel, Google Sheets, LibreOffice) or a plain text editor (preferred as Excel can silently alter your file and aesier to paste content during import)
2. Edit the values you need - prices, new products, items per box, etc.
3. In the app, click **Import CSV** and paste in your updated CSV content (not the file itself, its content)
4. The app will load your new data while preserving any price history you've already logged, as long as product names haven't changed

> ⚠️ **Important:** A product's name is built from its `Category` and `Brand` columns (e.g. `Soda - ColaCola`). If you change those columns, the product is treated as a new one and its price history will be lost. Only rename a product if it genuinely changed in the game.

### CSV column reference

| Column | Description | Example values |
| ----------------- | ------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `License` | License tier - base game: `0`-`29`, DLC: `DLC-Bakery-1` | `5`, `DLC-Clothing-2` |
| `Category` | Product category | `Soda`, `Meat`, `Cake` |
| `Brand` | Brand name, or `-` if none | `ColaCola`, `-` |
| `Storage` | Storage type | `Shelf`, `Fridge`, `Freezer`, `Produce Stall`, `Bakery Shelf`, `Pegboard`, `Hanger Rack`, `Ice Cream Stand` |
| `ItemsOrWeight` | Items per box, or kg per box for produce | `24`, `2.5` |
| `ShelfCap` | Items that fit on one shelf slot | `12` |
| `MarketSellPrice` | Default sell price per item (or per kg for produce) | `3.49` |
| `OnlineBuyPrice` | Default online buy price per full box | `49.99` |
| `LocalMarket` | Pickup market name, or `-` if no pickup | `Deli and Grocery` |
| `HasPickup` | Whether pickup is available | `true` / `false` |
| `IsWeightBased` | Whether sold by weight (produce) | `true` / `false` |
| `IsVending` | Whether vending machine compatible | `true` / `false` |
| `DLC` | DLC group name, blank for base game | `Bakery`, `Clothing`, `Electronics`, `Hardware`, `Essentials`, `IceCream` |

You can also export your current product list at any time using the **Export CSV** button - this gives you a file in the exact same format, which is a handy starting point for edits.

---

## ✨ Features

### 📊 Dashboard

Overview of all tracked products with key stats at a glance:

- **Products visible** with a "matching current filter" sub-label, and **products with prices logged** shown in `logged/total` format with a % data coverage indicator
- **Avg markup %** across actively priced products in the current filter (colour-coded to sweet spot thresholds: green / yellow / red / purple)
- **🔴 Products in red zone**: count and % of priced products exceeding the yellow markup threshold
- **Margin health overview** and **Discount activity bar**
- **Needs attention** table showing the top 3 unpriced items still on default values
- Charts for profit distribution, **storage type breakdown** and **market type breakdown** (with percentage labels), and top products by profit margin
- **Top 10 Online** and **Top 10 Pickup** profit charts - with full product name on hover even when axis labels are truncated
- **Recent price changes** panel (last 15 entries) showing all logged entries across all products, sorted newest first
- **Biggest movers from default** (top 13 entries) and **most updated products**
- All dashboard items (recent changes, movers, most updated) are **clickable** and open the product detail modal directly
- Each of the 11 dashboard panels can be individually shown or hidden via **Dashboard Widget Visibility** in the Customization tab

### 📦 Products tab

Full sortable and filterable product table with:

- **Split Category / Brand columns** - sort independently on each
- **Three price columns**: Market Price, Your Sell Price, and Margin % - all sortable
- **Sweet Spot Markup badge** (🟢 / 🟡 / 🔴 / 🟣) next to every product's margin, colour-coded by markup zone
- **Multi-sort** - click the ⇅ button to open a priority sort builder with up to 13 levels, each with its own field and direction. Clicking any column header resets back to single-column sort.
- **Category and Brand filter dropdowns** in the topbar, stacked with search, storage type, DLC, and licence filters. Includes an **Online Only** option in the storage type filter.
- Units/box, Units/slot, and Slots/box columns for shelf planning
- **Discount indicator** - products with an active discount on their latest entry are flagged across the whole app
- **⚠ missing price indicator** on products that still have no logged prices
- Click any row to open the full product detail modal

### 🏆 Top Profit (Leaderboard)

Ranks all products with logged prices by profitability across three columns: Online/box, Pickup/box, and Pickup Difference. All rows are clickable.

### 🗂️ Licence Content

Automatically loads all products for the selected licence. Displays per-product comparison cards with best ↑ / worst ↓ metric highlighting, a profit comparison bar chart, and market price, your price, and the markup badge on each card. Cards are clickable. ("All" is intentionally excluded - use Compare Products for free-form multi-product comparison.)

### ⚖️ Compare Products

Side-by-side comparison of 2 or more products, with a profit chart and key stats for each. The lowest value per metric is highlighted in red with a ↓ arrow. Products with fewer history entries extend to the full x-axis with a dotted line and endpoint dot. Each card shows market price, your price, and the markup badge. Cards are clickable.

### 🍦 Ice Cream Stand *(IceCream DLC)*

A dedicated tab for Ice Cream Stand products. Appears automatically when the IceCream DLC is enabled and hides when toggled off.

### ⚙️ Customization

Store-level settings and personalisation options:

- **Store name**: displayed in the header below the logo, included in CSV and JSON exports, and restored automatically on JSON import
- **Markup % Presets**: define up to 5 personal markup buttons that appear when editing a product's sell price. Presets save to localStorage, persist across sessions, and are included in JSON exports. A **Reset to Defaults** button restores `+2.5% / +5% / +7.5% / +10% / +15%`.
- **Sweet Spot zones**: customise the colour-coded markup thresholds (🟢 safe / 🟡 caution / 🔴 complaint risk / 🟣 negative). A live gradient preview bar updates in real time as you adjust values.
- **Dashboard Widget Visibility**: toggle each of the 11 dashboard panels on or off individually. Saved in JSON backups.
- **Default tab on load**: pick which tab the app opens on. Saved to localStorage and included in settings exports.
- **Display Preferences**: table density and default tab on load, grouped together as visual/layout controls.
- **Settings Backup section**: export a lightweight settings-only JSON (sweet spot thresholds, markup presets, store name, sort, widget visibility, default tab, table density) or import settings from either a settings-only or full backup JSON - without touching any product data.

---

## 🔍 Product detail modal

Click any product anywhere in the app to open its detail view:

- Current profit stats (online and pickup, per item and per box), including items/weight per box, items/slot, and slots/box
- **Market Price** and **Your Sell Price** fields tracked separately. Entering a new market price auto-fills your sell price to match.
- **Live markup badge** that updates in real time as you type, with a markup summary line in the profit preview box
- Profit evolution chart - updates **live as you type** to preview where the new entry would land before saving
- **Discount slider** - set a discount from 0% to 100% before saving. The entry row turns red when active. Live preview shows discounted and undiscounted profits side by side. Discounts are correctly reflected in the markup badge.
- **Discount badge** (🏷 -X%) on saved history entries that used a discount
- **Undiscounted reference lines** on the profit chart when any entry has a discount - dotted green (online) and blue (pickup) lines show what profits would have been without the discount
- **Zero line** on the chart - appears only when at least one value goes negative
- **Inline warning box** when either price is missing, specifying which price(s) are absent
- Markup % and Your Price columns in the price history table
- Sell price adjustment buttons driven by your saved presets (default: Reset · +2.5% · +5% · +7.5% · +10% · +15%)
- History is capped at 25 entries per product (1 default + 24 manual); oldest manual entry is dropped when the cap is reached
- Delete individual entries directly from the history table

---

## 🧮 How profits are calculated

| Term | Formula |
| ------------------------ | ------------------------------------------------------------------------------------------ |
| **Online profit / item** | `(Market price × items per box − online buy price) ÷ items per box` |
| **Online profit / box** | `Market price × items per box − online buy price` |
| **Pickup profit** | Same formula but using the local market buy price (`Market price × 0.5`) instead of online |
| **Markup %** | `(Your sell price − Market price) ÷ Market price × 100` |
| **Profit margin %** | `Online profit per item ÷ Market sell price × 100` |

### 🟢 Sweet Spot zones

The markup badge (🟢 / 🟡 / 🔴 / 🟣) appears next to every product's margin across the app. Default thresholds (customisable in the Customization tab):

| Badge | Zone | Meaning |
| ----- | ------------ | --------------------------------- |
| 🟣 | Negative | Selling below market price |
| 🟢 | 0% - 7% | Safe zone |
| 🟡 | 7% - 10% | Caution |
| 🔴 | 10%+ | Complaint risk |

---

## 🧩 DLC support

Toggle DLC categories on/off using the bar at the top of the page. Disabling a DLC hides corresponding products from all views and calculations. Available DLC categories: Bakery, Clothing, Electronics, Hardware, Essentials, Ice Cream.

---

## 💾 Data management

| Function | What it does |
| -------------------------- | --------------------------------------------------------------------------------------------------- |
| **Download CSV Template** | Saves the full product list with default prices to a `.csv` file (useful when starting a new game) |
| **Export CSV** | Saves your current product list with logged prices to a `.csv` file |
| **Import CSV** | Loads a product list from a CSV file (price history preserved for matching product names) |
| **Backup** | Saves everything - price history, stars, settings - to a dated `.json` file |
| **Restore** | Restores a `.json` backup, replacing all current data after confirmation |
| **Export Settings** | Saves only your customization settings (no product data) to a lightweight `.json` file |
| **Import Settings** | Restores settings from a settings-only or full backup JSON, without touching product data |
| **Reset** | Clears all price history and restores built-in default values |

> Backups from versions prior to v2.8 are fully supported - the old combined name format is automatically migrated to separate Category / Brand fields on restore. Backups from v2.8 and earlier will have markup presets defaulted to standard values on import.

---

## 🛠️ Tech

- Pure HTML + CSS + JavaScript - single file, zero dependencies to install
- [Chart.js](https://www.chartjs.org/) loaded from CDN for charts
- Data stored in browser `localStorage`
- Full backups saved as local `.json` files via the Backup function

---

## 📄 Licence

MIT - see [LICENSE](LICENSE) for details.
