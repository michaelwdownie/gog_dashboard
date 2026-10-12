Thumbnail images — why this folder holds no .jpg files (run 2026-10-12)
======================================================================

The sandbox that generates this report has NO network egress to YouTube's
image CDNs. i.ytimg.com and img.youtube.com both return HTTP 403 on CONNECT
(blocked by this environment's egress policy), re-verified THIS run
(CONNECT tunnel failed, response 403 for each host). Only www.googleapis.com
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
img.youtube.com) for this environment's egress policy: the cloud environment
menu in the session title bar -> Edit -> Network access -> Custom, add the host
under Allowed domains (keep the default package-manager list).
Docs: https://code.claude.com/docs/en/cloud-environments#network-access

Data integrity (2026-10-12): the video ID -> title -> stats mapping was rebuilt
directly from the live API this run (channel 9,450 subs / 688,503 views / 33
videos; prior run 2026-10-05 was 9,440 / 683,541). Every video ID referenced in
index.html was re-verified against this run's fetched titles/stats before writing.

This run's top refresh candidate remains the Pragmata essay (C7zyJ_MeMdA), titled
"The Dad Game That Replaced Trauma With Tenderness" — tags confirm it is a
Pragmata (Capcom) video, yet the game is never named in the title, forfeiting all
Pragmata search/browse traffic despite the channel's highest essay engagement
(11.5%). Channel-wide signal reconfirmed: titles containing "||" average 3.6
views/day vs 10.0 for titles without one. Cadence note: only 1 upload in the last
90 days (Sept 3 "Deep State" essay), which is itself the channel's 2nd-best
views-per-day performer — momentum is there but cooling for want of new uploads.
