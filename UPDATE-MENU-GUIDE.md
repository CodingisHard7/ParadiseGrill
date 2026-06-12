# How to Update the Menu — Paradise Grille Website

The website's menu can be powered by a simple Google Sheet. Once connected, anyone at the restaurant can change prices, add specials, or remove items by editing a spreadsheet — no website skills needed. Changes appear on the site the next time a visitor loads the page.

## One-time setup (about 5 minutes)

1. Go to [sheets.google.com](https://sheets.google.com) and create a new, blank spreadsheet. Name it something like "Paradise Grille Menu".
2. Rename the tab at the bottom-left from "Sheet1" to **Menu** (exact spelling, capital M).
3. Import the starting menu: File → Import → Upload → choose the `menu-data.csv` file from this folder → "Replace current sheet". This loads the entire current menu.
4. Click **Share** (top right) → under "General access" choose **Anyone with the link** → role **Viewer**.
5. Copy the sheet's ID from your browser's address bar. It's the long jumble of letters between `/d/` and `/edit`:
   `https://docs.google.com/spreadsheets/d/`**`THIS-LONG-ID-HERE`**`/edit...`
6. Open `index.html` in a text editor, find the line near the bottom that says
   `const MENU_SHEET_ID = "";`
   and paste the ID between the quotes. Save. Done — the site now reads the sheet.

## Day-to-day updates (the restaurant does this)

Just edit the spreadsheet. Each row is one menu item with five columns:

| Column | What it is | Example |
|---|---|---|
| Menu | Which tab it's on: `Food`, `Drinks`, or `Cafe & Parlor` | Food |
| Section | The heading it appears under | Appetizers |
| Item | The item's name | Coconut Shrimp |
| Price | Just the number (or leave blank) | 16 |
| Description | The ingredients line (or leave blank) | Wild caught coconut shrimp... |

- **Change a price:** edit the Price cell. That's it.
- **Add an item:** add a row anywhere, fill in the five columns. Items appear in the order they're listed in the sheet, grouped by Section.
- **Remove an item:** delete the row.
- **Add a new section:** just use a new Section name — it will appear automatically.
- **Section note** (like "All served with house cut fries"): add a row with the Menu and Section filled in, the Item and Price left empty, and the note in Description.
- A section named **Signature Tacos** (or anything with "Taco") becomes the big orange highlight banner. A section with "Add-On" in the name becomes the small pink add-ons box.

## Good to know

- If the sheet is ever deleted, unshared, or Google is unreachable, the site quietly falls back to the menu that's built into the page — visitors never see an error.
- After editing, refresh the website to see the change. (Google occasionally takes a minute or two to serve the newest version.)
- Don't rename or reorder the five column headers in row 1.
