This run (2026-07-27): the sandbox generating this report has no egress to
YouTube's image CDNs (i.ytimg.com / img.youtube.com / yt3.ggpht.com all return
HTTP 403 CONNECT — blocked by this environment's network policy), so the
thumbnail image files could NOT be downloaded to disk this week, and the
analyst could not pixel-inspect them directly.

Instead, docs/index.html embeds each thumbnail live from YouTube's CDN
(https://i.ytimg.com/vi/<videoId>/hqdefault.jpg). Those URLs render normally in
any browser viewing the published GitHub Pages dashboard — only the sandbox is
blocked, not your browser. The thumbnail critiques in the dashboard are
therefore inferred from title/format/metric patterns plus the public thumbnail
compositions visible at those URLs, not from a fresh pixel-level read this run.

If a future run is granted image-CDN egress, thumbnails will be saved here as
<videoId>.jpg and referenced by relative path, and the critique will include a
direct visual grade (contrast, face presence, text legibility).
