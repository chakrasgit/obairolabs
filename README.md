# Obairo Labs — Activity Console

A self-hosted, no-backend dashboard + tracker for obairolabs content activity across YouTube, Instagram, Facebook, Threads, X, LinkedIn and Reddit. 

## Files

```
index.html            → the whole dashboard (HTML + CSS + JS, no build step)
data/activity.json    → your daily log — one entry per video
data/categories.json  → your list of sub-niches — add/remove freely
```

## Updating daily

Open `data/activity.json` and add a new entry to the array. Copy this block, fill it in, keep the `id` incrementing:

```json
{
  "id": 9,
  "title": "Your video title here",
  "category": "AI News",
  "video_type": "short",
  "date_posted": "2026-07-04",
  "source_url": "https://official-source-link.com",
  "platforms": {
    "youtube":   { "status": "posted", "url": "https://youtube.com/watch?v=..." },
    "instagram": { "status": "posted", "url": "https://instagram.com/p/..." },
    "facebook":  { "status": "posted", "url": "https://facebook.com/..." },
    "threads":   { "status": "posted", "url": "https://threads.net/..." },
    "twitter":   { "status": "scheduled", "url": null },
    "reddit":    { "status": "not_planned", "url": null }
  }
}
```

**Status values per platform:**
- `"posted"` — live, dot fills solid amber, links to the `url` you give
- `"scheduled"` — queued but not live yet, dot shows amber outline
- `"not_planned"` — not going up on that platform for this piece, dot stays dim/empty

**video_type:** `"short"` or `"long"` 

**source_url:** optional — leave as `""` if there's no single primary source (e.g. an explainer video). Used to make the title clickable in the table.

## Adding a new sub-niche/category

Just add a string to `data/categories.json`:

```json
[
  "AI News",
  "AI Labs",
  "AI Concepts",
  "AI Ethics & Safety",
  "Robotics News",
  "Robotic Concepts",
  "Humanoid Robots",
  "AI in Industry",
  "Your New Category Here"
]
```

It will automatically show up as a filter chip and in the category breakdown — no HTML/JS edits needed. Just make sure any activity entries use the *exact same spelling* as what's in this file.



## What the dashboard shows

- **Stats row** — total videos, active categories, platform coverage %, this month's count
- **Posts / Month chart** — pick any year from 2026–2032, see your monthly volume
- **Category breakdown** — which sub-niches you're covering most
- **Platform coverage** — per-platform posted vs. planned ratio, flags if you're consistently skipping one
- **Filters** — category (multi-select), video type, platform, date range — all combinable
- **Activity log table** — full sortable-by-date record with clickable platform dots and source links
