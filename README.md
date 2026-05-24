# FeedFlow Trending

Static JSON manifest of the "Trending This Week" feed list shown in the
[FeedFlow Android app](https://github.com/ttemucin/feedflow) Discover screen.

Served via GitHub Pages at:
`https://ttemucin.github.io/feedflow-trending/v1/trending.json`

## Updating

Edit `v1/trending.json`, push to `main`. The FeedFlow app refreshes its cache
once per 7 days via WorkManager, with a bundled fallback list when this URL is
unreachable.

## Schema

```jsonc
{
  "version": 1,
  "updatedAt": "YYYY-MM-DD",
  "entries": [
    {
      "name": "Feed Name",
      "url": "https://example.com/feed.xml",
      "category": "Tech",
      "iconUrl": "https://www.google.com/s2/favicons?domain=example.com&sz=64",
      "description": "Short tag line",
      "rank": 1
    }
  ]
}
```

Categories used by the app (v13): All, AI & ML, Business, Climate, Conspiracy,
Culture, Design, Dev, Entertainment, Finance, Food, Health, News, Sci-Fi,
Science, Sports, Tech, Travel.
