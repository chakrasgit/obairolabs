# Obairo Activity Console

Live Site: [chakrasgit.github.io/obairolabs](https://chakrasgit.github.io/obairolabs/)

A self-hosted, no-backend dashboard for tracking Obairo content activity across YouTube, Instagram, Facebook, Threads, X, Reddit and LinkedIn.

## Files

```
index.html            the whole dashboard (HTML + CSS + JS, no build step)
data/activity.json    daily log, one entry per video
data/categories.json  list of sub-niches, add/remove freely
```

## Updating daily

Open `data/activity.json` and add a new entry to the array. Copy this block, fill it in, and keep `id` incrementing in chronological order (oldest video = lowest id, newest = highest):

```json
{
  "id": 8,
  "title": "Your video title here",
  "category": "AI News",
  "video_type": "short",
  "date_posted": "2026-07-20",
  "source_url": "https://official-source-link.com",
  "platforms": {
    "youtube":   "https://youtube.com/watch?v=...",
    "instagram": true,
    "facebook":  false,
    "threads":   true,
    "x":         true,
    "reddit":    false,
    "linkedin":  true
  }
}
```

**Platform values:**
- A URL string: posted, badge links out to it
- `true`: posted, no link saved yet (badge still fills, just isn't clickable)
- `false`: not posted to that platform

**video_type:** `"short"` or `"long"`

**source_url:** optional, leave as `""` if there's no single primary source. Used to make the title clickable in the table.

## Adding a new sub-niche/category

Add a string to `data/categories.json`:

```json
[
  "AI News",
  "AI Concepts",
  "Robotic Concepts",
  "Robotics News",
  "AI Startups",
  "Robotics Startups",
  "Your New Category Here"
]
```

It shows up automatically in the category filter and category breakdown. No HTML/JS edits needed. Use the exact same spelling in activity entries as in this file.

## What the dashboard shows

- Total Videos: the one KPI tracked
- Posts / Month chart: pick any year from 2026 to 2032
- Category breakdown: which sub-niches get covered most
- Videos per platform: raw count posted per platform
- Filters: category (multi-select dropdown), video type, platform, date range, all combinable
- Activity log table: sorted newest first, per-platform letter badges (filled = posted, outline = not posted), clickable links where available
