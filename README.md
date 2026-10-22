# NovelHi test build

Test build for lnreader/lnreader-plugins#2708 (covers blank in the
extension list and in the library after refresh).

Version 1.1.2, based on the official NovelHi 1.1.1 plugin:

- Adds `imageRequestInit` (browser User-Agent, Referer
  https://novelhi.com/, image Accept headers) for cover requests.
  img.novelhi.com answers plain app requests with 403 while a browser
  loads the same URL.
- Makes `parseNovel` cover extraction fall through `.cover img` /
  `.decorate-img img`, `data-src`, and an image with alt containing
  "novel cover", then falls back to the cover already returned by the
  list API, instead of only reading `.attr('src')` off the container.
- Adds `resolveUrl` that passes absolute URLs through unchanged.

Official live check on this version: popular 10, search 1,
parseNovel 7464 chapters, parseChapter 4405 chars, all PASS.

Install: LNReader -> Settings -> Repositories -> add
`https://raw.githubusercontent.com/RevDev909/lnreader-novelhi/main/.dist/plugins.min.json`
-> Browse -> install NovelHi. If you already had NovelHi installed,
remove and re-add the repository first, or the app will keep serving
the cached old bundle.
