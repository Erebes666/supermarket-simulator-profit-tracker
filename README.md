# 🛒 Supermarket Simulator - Profit Tracker

An unofficial fan-made profit tracking tool for [Supermarket Simulator](https://store.steampowered.com/app/2670630/Supermarket_Simulator/). Log your market prices, calculate online vs pickup profits, compare products side by side, and visualise your most profitable items - all in a single HTML file that runs directly in your browser with no installation required.

> **Disclaimer:** This is an unofficial fan-made tool, not affiliated with or endorsed by Nokta Games. All game content, product names, and trademarks belong to their respective owners.

> 🌍 *The interface is in English but the tool is straightforward to use - just open the file in your browser.*


![App screenshot](https://github.com/Erebes666/supermarket-simulator-profit-tracker/blob/main/Assets/SuperMarketTracker_UI1.png)

---

## 📁 Repository contents

| File | Description |
|---|---|
| `supermarketSimulator-tracker_v2_5.html` | The app - open this in your browser |
| `supermarket-tracker-data-v1.2.1.csv` | Default product data for game version 1.2.1 |
| `LICENSE` | MIT licence |
| `README.md` | This file |
| `Assets` | Some screenshots of the UI |
| `Changelog.md` | List of the changes for each version

---

## 🚀 How to use

1. Download `supermarketSimulator-tracker_v2_5.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. That's it - no install, no server, no account needed

Your data is saved automatically in your browser's local storage and persists between sessions as long as you use the same browser.

---

## ⚠️ Data & Storage Warning

All your data (prices, edits, settings, price history) is saved **locally in your browser only**.
Clearing your browser history, cache, or site data will **permanently delete everything** ! There is no recovery.

**Exporting to CSV does NOT save everything.**
The CSV only backs up your product list and prices. Your price history, stars, and settings are not included in the export and will be lost if you clear your browser data.

To save your price history, stars, and settings, use the function **Backup** from time to time. This will create a JSON file with EVERYTHING on it (price history, stars, settings , etc...).
To restore it use the function **Restore** and select the JSON file

---

## 🔄 Keeping up with game updates

The app ships with built-in default data for **game version 1.2.1**. If the game gets updated and prices or products change, you don't need to wait for the app itself to be updated - you can update the data yourself using the CSV file.

### How to update product data

1. Open `supermarket-tracker-data-v1.2.3.csv` in any spreadsheet app (Excel, Google Sheets, LibreOffice) or a plain text editor (better as Excel can change your document)
2. Edit the values you need - prices, new products, items per box, etc.
3. In the app, click **Import CSV** and paste in your updated CSV content (not the file, its content)
4. The app will load your new data while preserving any price history you've already logged, as long as product names haven't changed

> ⚠️ **Important:** A product's name is built from its `Category` and `Brand` columns (e.g. `Soda - ColaCola`). If you change those columns, the product is treated as a new one and its price history will be lost. Only rename a product if it genuinely changed in the game.

### CSV column reference

| Column | Description | Example values |
|---|---|---|
| `License` | License tier - base game: `0`–`29`, DLC: `DLC-Bakery-1` | `5`, `DLC-Clothing-2` |
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

You can also export your current product list at any time using the **Export CSV** button in the app - this gives you a file in the exact same format, which is a handy starting point for edits.

---

## ✨ Features

### 📊 Dashboard
Overview of all tracked products with key stats at a glance:
- Total products tracked and how many have prices logged
- Average online and pickup profit per box
- Charts for profit distribution, storage type breakdown, and top products by profit margin
- Profit margin % chart - shows which products give the best return relative to their sell price (unlocks once you start logging prices)

### 📦 Products tab
Full sortable and filterable product table with:
- Profit per item and per box for both online and pickup channels
- Filter by storage type, search by name
- Group by License tier or Storage type using the sidebar

### 🏆 Leaderboard
Ranks all products with logged prices by profitability. Useful for quickly spotting your best earners.

### ⚖️ Compare
Side-by-side comparison of 2 or more products, with a profit chart and key stats for each.

---

## 🔍 Product detail modal

Click any product in the "Products tab" to open its detail view:
- Current profit stats (online and pickup, per item and per box)
- Profit evolution chart if you've logged multiple price updates
- Log a price update by entering the current Market sell price and Online buy price
  - Use the **±10% quick buttons** next to the Market price to adjust by 10% at a time
  - Live profit preview updates instantly as you type
- Full price history for that product

---

## 🧮 How profits are calculated

| Term | Formula |
|---|---|
| **Online profit / item** | `(Market price × items per box − online buy price) ÷ items per box` |
| **Online profit / box** | `Market price × items per box − online buy price` |
| **Pickup profit** | Same formula but using the local market buy price instead of online |
| **Profit margin %** | `Online profit per item ÷ Market sell price × 100` |

---

## 🧩 DLC support

Toggle DLC categories on/off using the bar at the top of the page. Disabling a DLC hides those products from all views and calculations. Available categories: Bakery, Clothing, Electronics, Hardware, Essentials, Ice Cream.

---

## 💾 Data management

- **Download CSV Template** - saves the full product list with default prices to a `.csv` file (useful when strating a new game)
- **Export CSV** - saves your full product list with current prices to a `.csv` file
- **Import CSV** - loads a product list from a CSV file (price history is preserved for matching product names)
- **Backup** - saves your price history, stars, and settings to a `.JSON` file
- **Restore** - Restore your price history, stars, and settings from a selected `.JSON` file
- **Reset** - clears all price history and restores the built-in default values

---

## 🛠️ Tech

- Pure HTML + CSS + JavaScript - single file, zero dependencies to install
- [Chart.js](https://www.chartjs.org/) loaded from CDN for charts
- Data stored in browser `localStorage`
- Data saved in a local `JSON` file if used the backup function

---

## 📄 Licence

MIT - see [LICENSE](LICENSE) for details.
