# Website Behaviour Tracker

A small project that records how a visitor interacts with a webpage and shows the results as a heatmap, a scatter plot, a mouse path and a set of statistics. I built it to explore how clicks, mouse movement and scrolling can be captured and visualised using nothing but the browser.

## Features

- Click heatmap drawn over the page
- Click scatter plot, coloured from first click to last
- Mouse movement tracking, with a mouse path view
- Scroll depth tracking (25%, 50%, 75% and 100% milestones)
- Click and interaction statistics
- Event log
- Element visibility tracking (time each section is in view)
- Export tracking data as JSON

## How to Run

1. Download `index.html` from this repository.
2. Open it in your browser.
3. Press **Start tracking** and interact with the page.
4. Use the tabs and the **Show on page** menu to view the results, then press **Export JSON** to save the data.

No install step and no server are needed.

## How it works

- Click and mouse positions are stored relative to the tracked page, so they stay correct when you scroll.
- Mouse movement is sampled every 40 ms and capped at 5,000 points.
- The heatmap blends soft circles for every click and mouse sample, then colours them from blue (cool) to red (hot).
- A section counts as "visible" when at least half of it is on screen, using `IntersectionObserver`.
- Everything stays in the browser tab. Nothing is sent to a server.

## Exported data

```json
{
  "meta": { "page": "...", "viewport": {}, "pageSize": {} },
  "summary": { "clicks": 0, "maxScrollPct": 0, "distancePx": 0 },
  "clicks": [{ "x": 0, "y": 0, "t": 0, "target": "button", "section": "Hero" }],
  "moves": [{ "x": 0, "y": 0, "t": 0 }],
  "visibility": { "Hero": 0 },
  "log": []
}
```

Times (`t`) are milliseconds since tracking started.

## Track your own page

Put your own content inside the `<main id="site">` element and add `data-track="Section name"` to any block you want to measure.

## Built With

- HTML
- CSS
- JavaScript
