# Life Islands Planner

A 2D top-down map of your life as an archipelago. Each island focuses on one
part of life and keeps its own account of entries.

## Islands

| Island | Focus | Account view |
|---|---|---|
| 💰 Financial Island | Money in and out | Gantt chart — dates on the horizontal axis, item names on the vertical axis |
| 🌿 Health Island | Body and mind | Ledger table |
| 🏔 Career Island | Work, skills, projects | Ledger table |

The three islands are connected through a central **hub node** on the map.
Click (or focus + Enter) an island to open its account in the side panel.

## Running

No build step — open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Editing entries

Use the **+ Add entry** button in an island's panel to add an item, and the
**Edit** / **Delete** buttons on each row of the entries table to change or
remove one. The quantity stepper's − / + buttons multiply the per-unit amount:
an entry's total is `amount × qty`, and balances, the Gantt labels, and
tooltips all show the total. Edits are saved to the browser's localStorage,
so they survive reloads; clearing site data restores the seed entries.

Amounts are in **yen (¥)**. Entries saved by the older dollar version are
migrated automatically at the fixed rate defined by `USD_TO_JPY` in
`index.html` (¥150 per $1).

The seed entries live in the `ISLANDS` array near the top of the `<script>`
block in `index.html`. Each entry has an `item` name, `start`/`end` dates
(`YYYY-MM-DD`), a per-unit `amount` in yen (negative for spending), a `qty`,
and an optional `note`:

```js
{
  item: "Gift: Vlaude for Ruksa",
  start: "2026-07-12",
  end: "2026-07-12",
  amount: -3300,
  qty: 1,
  note: "Gifted Ruksa vlaude — $22 ≈ ¥3,300",
}
```

The Gantt chart's time window, weekend shading, and the dashed "today" marker
adjust automatically. Light and dark mode both follow the system preference.
