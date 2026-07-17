# Obairo — Activity Console

🔗 **Live Site:** [chakrasgit.github.io/obairolabs](https://chakrasgit.github.io/obairolabs/)

A self-hosted, no-backend dashboard + tracker for Obairo content activity across YouTube, Instagram, Facebook, Threads, X, Reddit and LinkedIn.

## Files

```
index.html            → the whole dashboard (HTML + CSS + JS, no build step)
data/activity.json    → your daily log — one entry per video
data/categories.json  → your list of sub-niches — add/remove freely
```

## Updating daily

This tracker only logs **posted** content — there's no scheduled/pending state. Add an entry once a video is actually live somewhere.

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
- A **URL string** — posted, and the badge in the table links out to it
- **`true`** — posted, but you haven't saved a direct link yet (badge still fills, just isn't clickable)
- **`false`** — not posted to that platform

**video_type:** `"short"` or `"long"`

**source_url:** optional — leave as `""` if there's no single primary source. Used to make the title clickable in the table.

## Adding a new sub-niche/category

Just add a string to `data/categories.json`:

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

It will automatically show up in the category filter dropdown and in the category breakdown — no HTML/JS edits needed. Just make sure any activity entries use the *exact same spelling* as what's in this file.

## What the dashboard shows

- **Total Videos** — the one KPI that matters for this tracker
- **Posts / Month chart** — pick any year from 2026–2032, see your monthly volume
- **Category breakdown** — which sub-niches you're covering most
- **Videos per platform** — raw count of videos posted per platform
- **Filters** — category (multi-select dropdown), video type, platform, date range — all combinable
- **Activity log table** — sortable-by-date record, newest first, with per-platform letter badges (filled = posted, outline = not posted) and clickable links where available
