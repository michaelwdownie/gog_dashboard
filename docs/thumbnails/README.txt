This run: thumbnail images are embedded in index.html via YouTube's live CDN
URLs (https://i.ytimg.com/vi/<id>/hqdefault.jpg) because this sandbox's egress
policy blocked direct downloads from i.ytimg.com / ytimg / ggpht (HTTP 403
CONNECT policy denial). The images render normally in any browser viewing the
dashboard. If a future run has image-CDN egress, thumbnails will be copied here
and referenced by relative path instead.
