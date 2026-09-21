Thumbnail images — why this folder holds no .jpg files (run 2026-09-21)
======================================================================

The sandbox that generates this report has NO network egress to YouTube's
image CDNs. i.ytimg.com, img.youtube.com, i9.ytimg.com, yt3.ggpht.com and
lh3.googleusercontent.com all return HTTP 403 on CONNECT (blocked by this
environment's egress policy), re-verified THIS run via the agent-proxy status
endpoint (recentRelayFailures shows connect_rejected / 403 for each host) and
via WebFetch (EGRESS_BLOCKED, domain i.ytimg.com). Only www.googleapis.com
(the YouTube Data API v3) is reachable.

Consequence: thumbnail image files could NOT be downloaded to disk, so a fresh
pixel-level inspection (contrast, face expression, text legibility, clutter)
was NOT possible this run. This has been true on every run to date.

Instead, docs/index.html embeds each thumbnail LIVE from YouTube's CDN
(https://i.ytimg.com/vi/<videoId>/hqdefault.jpg). Those URLs render normally in
any browser viewing the published GitHub Pages dashboard — only the sandbox is
blocked, not your browser. The thumbnail guidance in the dashboard is therefore
grounded in title/format/subject and metric patterns, NOT a fresh pixel read.
No visual claims are fabricated.

To enable a true visual grade on a future run, allow-list i.ytimg.com (or
img.youtube.com) for this environment's egress policy.

Data integrity (2026-09-21): the video ID -> title -> stats mapping was rebuilt
directly from the live API this run (channel 9,400 subs / 672,262 views / 33
videos; prior run 9,360 / 665,525). Every video ID referenced in index.html was
verified against this run's fetched titles and stats before writing.
