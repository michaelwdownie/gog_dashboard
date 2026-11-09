Thumbnail images — why this folder holds no .jpg files (run 2026-11-09)
======================================================================

This sandbox has NO network egress to YouTube's image CDNs. Re-verified THIS
run: i.ytimg.com failed CONNECT with HTTP 403 (blocked by this environment's
egress policy; "CONNECT tunnel failed, response 403" recorded by the agent
proxy). Only www.googleapis.com (YouTube Data API v3) is reachable, which is
how all metrics were fetched.

Consequence: thumbnail image files could NOT be downloaded to disk this run, so
a fresh pixel-level inspection (contrast, face expression, text legibility,
clutter, palette) was NOT possible. This has been the case on every run to date.

This run ALSO attempted to allow-list i.ytimg.com automatically via the
environment's network settings, but the change needs a person's approval and
nobody is present on an unattended scheduled run, so it was refused.

Instead, docs/index.html embeds each thumbnail LIVE from YouTube's CDN
(https://i.ytimg.com/vi/<videoId>/hqdefault.jpg). Those URLs render normally in
any browser viewing the published GitHub Pages dashboard — only the sandbox is
blocked, not your browser. Thumbnail guidance in the dashboard is therefore
grounded in title/format/subject/metric patterns, NOT a fresh pixel read, and
is labelled as such. No visual claims are fabricated.

To enable a true visual grade on a future run, either:
  (a) start this routine with "Run now" and approve the network-access request
      that appears during the run, or
  (b) allow-list i.ytimg.com in the environment's Network access settings
      (cloud environment menu -> Edit -> Network access -> Allowed domains).
Docs: https://code.claude.com/docs/en/cloud-environments#network-access
