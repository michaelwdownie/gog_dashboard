Thumbnail images — why this folder holds no .jpg files (run 2026-10-19)
======================================================================

This sandbox has NO network egress to YouTube's image CDNs. Re-verified THIS
run: i.ytimg.com, img.youtube.com, i9.ytimg.com and yt3.ggpht.com all return
HTTP 403 on CONNECT (blocked by this environment's egress policy —
"CONNECT tunnel failed, response 403" for each host). Only www.googleapis.com
(the YouTube Data API v3) is reachable, which is how all metrics were fetched.

Consequence: thumbnail image files could NOT be downloaded to disk this run, so
a fresh pixel-level inspection (contrast, face expression, text legibility,
clutter) was NOT possible. This has been the case on every run to date.

Instead, docs/index.html embeds each thumbnail LIVE from YouTube's CDN
(https://i.ytimg.com/vi/<videoId>/hqdefault.jpg). Those URLs render normally in
any browser viewing the published GitHub Pages dashboard — only the sandbox is
blocked, not your browser. The thumbnail guidance in the dashboard is therefore
grounded in title/format/subject and metric patterns, NOT a fresh pixel read.
No visual claims are fabricated.

To enable a true visual grade on a future run, allow-list i.ytimg.com (or
img.youtube.com) in this environment's Network access settings: the cloud
environment menu in the session title bar -> Edit -> Network access -> add the
host under Allowed domains (keep the Allow package managers box ticked).
Docs: https://code.claude.com/docs/en/cloud-environments#network-access
