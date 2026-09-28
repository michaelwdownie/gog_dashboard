Thumbnail images — why this folder holds no .jpg files (run 2026-09-28)
======================================================================

The sandbox that generates this report has NO network egress to YouTube's
image CDNs. i.ytimg.com, img.youtube.com, i9.ytimg.com and yt3.ggpht.com all
return HTTP 403 on CONNECT (blocked by this environment's egress policy),
re-verified THIS run via the agent-proxy status endpoint (recentRelayFailures
shows connect_rejected / 403 for each host). Only www.googleapis.com (the
YouTube Data API v3) is reachable.

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
img.youtube.com) for this environment's egress policy (cloud environment menu
in the session title bar -> Edit -> Network access).

Data integrity (2026-09-28): the video ID -> title -> stats mapping was rebuilt
directly from the live API this run (channel 9,420 subs / 678,309 views / 33
videos; prior run 9,400 / 672,262). Every video ID referenced in index.html was
re-verified against this run's fetched titles/stats before writing.

FIXED THIS RUN: prior runs' index.html embedded the WRONG video ID for the
Wolfenstein top-performer thumbnail (tey_MJFcsoA, which is actually a 49-view
"Nine Sols video is going to take forever" Short). The correct Wolfenstein ID
is 7A9cQ86pQXM and is now used in both the trend section and the gallery.

New this run: the "Dad Game That Replaced Trauma With Tenderness" essay
(C7zyJ_MeMdA) was identified from its tags as a Pragmata video and flagged as a
top refresh candidate — its title never names the game, forfeiting all Pragmata
search traffic despite the channel's 2nd-highest engagement rate (11.7%).
