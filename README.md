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

Categories used by the app (v13+): All, AI & ML, Business, Climate, Conspiracy,
Culture, Design, Dev, Entertainment, Finance, Food, Health, News, Sci-Fi,
Science, Sports, Tech, Travel.

## Version manifest

`v1/version.json` advertises the latest available APK. The app fetches it once
on launch and shows an "Update available" banner if `versionCode` is higher than
its own `BuildConfig.VERSION_CODE`. Tapping the banner opens `releasePageUrl` in
a Custom Tab so the user can download the APK from the GitHub Release.

```jsonc
{
  "versionCode": 15,                                            // monotonically increasing
  "versionName": "v15",                                         // user-visible
  "downloadUrl":     "https://github.com/.../releases/latest/download/feedflow-debug.apk",
  "releasePageUrl":  "https://github.com/.../releases/latest",
  "releasedAt":      "YYYY-MM-DD",
  "releaseNotes":    "Short one-line summary"
}
```

**Cadence:** updated by hand alongside each new release. The companion APK is
attached to a GitHub Release on this repo (filename must be
`feedflow-debug.apk` for the `latest/download/` redirect to work).
