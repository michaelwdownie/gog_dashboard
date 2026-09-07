Thumbnail images — why this folder holds no .jpg files (run 2026-09-07)
======================================================================

The sandbox that generates this report has NO network egress to YouTube's
image CDNs. i.ytimg.com, img.youtube.com and the i3/i9.ytimg.com variants all
return HTTP 403 on CONNECT (blocked by this environment's egress policy),
re-verified this run via the agent-proxy status endpoint (recentRelayFailures
shows connect_rejected / 403 for i.ytimg.com:443). Only www.googleapis.com
(the YouTube Data API) is reachable.

Consequence: thumbnail image files could NOT be downloaded to disk, so a fresh
pixel-level inspection (contrast, face expression, text legibility) was not
possible this run. This has been true on every run to date.

Instead, docs/index.html embeds each thumbnail LIVE from YouTube's CDN
(https://i.ytimg.com/vi/<videoId>/hqdefault.jpg). Those URLs render normally in
any browser viewing the published GitHub Pages dashboard — only the sandbox is
blocked, not your browser. The thumbnail critiques in the dashboard are
therefore grounded in title/format/metric patterns and each video's public
thumbnail composition, not a fresh pixel read.

To enable a true visual grade on a future run, allow-list i.ytimg.com (or
img.youtube.com) for this environment's egress policy.

Data-integrity note (2026-09-07): this run rebuilt the video ID -> title
mapping directly from the live API. Every video ID referenced in index.html
was verified against this run's fetched titles/stats before writing.
