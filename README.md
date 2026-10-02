# Wisebunk

Wisebunk is a personal attendance tracker built for a single student to log, visualize, and project class attendance across a semester. It was built with AI assistance (Claude, by Anthropic) for educational and personal attendance-tracking purposes only — it is not an official university product and is not affiliated with any institution.

## What it does

- Tracks attendance per subject: present, absent, or cancelled, logged against the actual calendar date.
- Automatically calculates attendance percentage per subject and overall, excluding cancelled classes from the total.
- Projects how many more absences are possible before dropping below a 75% attendance threshold, based on your semester's total teaching weeks.
- Lets you attach a note to any lecture (e.g. a rescheduled or shifted class) and edit it later.
- Separates a read-only "view mode" from an "edit mode" so day-to-day viewing stays clean, with editing tools only visible when needed.
- Adapts to mobile, tablet, and desktop screens.

## How data is stored

Wisebunk has no backend database of its own. Instead, it uses a Google Sheet as its storage layer, through a small Google Apps Script web app:

- The entire tracker state (subjects, entries, semester settings) is stored as a single JSON document in a dedicated sheet tab.
- The page reads this data on load and writes back to it automatically whenever something changes.
- This means your data lives entirely in your own Google account, under your own control, and isn't stored by or accessible to anyone else.

## Setup

1. Create a blank Google Sheet.
2. Open Extensions → Apps Script (or create a standalone Apps Script project) and paste in the provided `Code.gs`.
3. If the script isn't bound to the sheet directly, set the `SPREADSHEET_ID` constant in `Code.gs` to your sheet's ID (found in the sheet's URL).
4. Deploy it as a Web App (Execute as: Me, Who has access: Anyone), and copy the deployment URL.
5. Paste that URL into the `SCRIPT_URL` constant near the top of `index.html` (or `attendance-sheets.html`).
6. Deploy the HTML file (e.g. via Vercel) and open it.

## Disclaimer

This tool was built with the assistance of an AI model (Claude) for a student's personal use in tracking their own class attendance. It performs simple arithmetic based on data the user enters themselves and is not a substitute for official university attendance records. Always verify your actual attendance standing with your institution directly.