# gods-work-media

Static image host for the Gods Work TikTok engine (`~/ClaudeCode/gods-work-tiktok`). Serves carousel
slides at `https://media.godsworkclothing.com/slides/<post-id>/<n>.jpg` so TikTok's Content Posting
API can pull them — `PULL_FROM_URL` requires images on a verified domain, and `godsworkclothing.com`
is verified under the TikTok dev app (covers this subdomain).

- `media.godsworkclothing.com` → GitHub Pages via the `CNAME` file (subdomain CNAME → `noahvideo.github.io`).
- Slides are uploaded by `tiktok/publish_carousel.py`, then **auto-deleted once TikTok has pulled them**
  (it polls publish status, then removes the folder). Stale folders are also pruned on each run.
- Public by necessity: TikTok fetches the URLs anonymously. No directory listing; `noindex` + `robots.txt`.
