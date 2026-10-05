Thumbnail images — why this folder holds no .jpg files (run 2026-10-05)
======================================================================

The sandbox that generates this report has NO network egress to YouTube's
image CDNs. i.ytimg.com and img.youtube.com both return HTTP 403 on CONNECT
(blocked by this environment's egress policy), re-verified THIS run
(connect_rejected / 403 for each host). Only www.googleapis.com (the YouTube
Data API v3) is reachable.

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
img.youtube.com) for this environment's egress policy: the cloud environment
menu in the session title bar -> Edit -> Network access -> Custom, add the host
under Allowed domains (keep the default package-manager list).
Docs: https://code.claude.com/docs/en/cloud-environments#network-access

Data integrity (2026-10-05): the video ID -> title -> stats mapping was rebuilt
directly from the live API this run (channel 9,440 subs / 683,541 views / 33
videos; prior run 2026-09-28 was 9,420 / 678,309). Every video ID referenced in
index.html was re-verified against this run's fetched titles/stats before writing.

Confirmed this run: the "Dad Game That Replaced Trauma With Tenderness" essay
(C7zyJ_MeMdA) is a Pragmata (Capcom) video — confirmed from its tags
(Pragmata, Pragmata Capcom, Pragmata Hugh and Diana). Its title never names the
game, forfeiting all "Pragmata" search traffic despite the channel's highest
essay engagement rate (11.6%). It remains the #1 refresh candidate.
