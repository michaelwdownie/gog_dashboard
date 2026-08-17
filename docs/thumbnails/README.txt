This run (2026-08-17): the sandbox that generates this report has no network
egress to YouTube's image CDNs. i.ytimg.com / img.youtube.com / yt3.ggpht.com
all return HTTP 403 on CONNECT (blocked by this environment's egress policy),
verified again this run via the agent-proxy status endpoint. Thumbnail image
files therefore could NOT be downloaded to disk, and the analyst could not do a
fresh pixel-level inspection. This has been true on every run to date
(2026-07-23 through 2026-08-17).

Instead, docs/index.html embeds each thumbnail live from YouTube's CDN
(https://i.ytimg.com/vi/<videoId>/hqdefault.jpg). Those URLs render normally in
any browser viewing the published GitHub Pages dashboard - only the sandbox is
blocked, not your browser. The thumbnail critiques in the dashboard are
therefore inferred from title/format/metric patterns and the public thumbnail
compositions, not from a fresh pixel-level read this run.

To enable a true visual grade (contrast, face presence, text legibility) on a
future run, allow-list i.ytimg.com for this environment's egress policy.
