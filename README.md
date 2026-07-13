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

## Adding entries

Entries live in the `ISLANDS` array near the top of the `<script>` block in
`index.html`. Each entry has an `item` name, `start`/`end` dates
(`YYYY-MM-DD`), an `amount` (negative for spending), and an optional `note`:

```js
{
  item: "Gift: Vlaude for Ruksa",
  start: "2026-07-12",
  end: "2026-07-12",
  amount: -22,
  note: "Gifted Ruksa vlaude — $22",
}
```

The Gantt chart's time window, weekend shading, and the dashed "today" marker
adjust automatically. Light and dark mode both follow the system preference.
