# HTTP notes (Project 001)

Fill this in after you deploy (see the HTTP exercise in `lesson.md`).

| Item | What I saw |
|---|---|
| Request method and URL |GET  https://yoleaa.github.io/fullstack-engineering-projects/01-web-foundations/project-001-developer-profile/ |
| Status code | 304 on a normal reload, 200 after Ctrl+Shift+R |
| Content-Type |text/html; charset=utf-8|
| Cache-Control / ETag | max-age=600 and W/"6afd8464-10cd"|
| Content length |1562 |
| What changed on the second reload |The reload sent If-None-Match and If-Modified-Since, so the server answered 304 |

## What the browser did
My browser sent a GET request to my page's address. The reload added `Cache-Control: max-age=0`, so the browser had to check with the server before reusing its saved copy. Because it already held a copy, it also sent `If-None-Match` with the ETag `W/"6afd8464-10cd"` and `If-Modified-Since` with the last-modified date. When the server answered 304, the browser displayed its saved copy of the page. It then requested `styles.css`, which the page needs.
## What the server did
The server compared the ETag and date from my request with the current version of the page. Nothing had changed, so it replied `304 Not Modified` with no page body, which saved bandwidth. The response said `Cache-Control: max-age=600`, so browsers may reuse the page for 10 minutes without asking again. A caching server in front of GitHub Pages answered (the `X-Cache: HIT` and `Via` headers show this).
## Resource and representation (RESTful Web Services)
The resource is my developer profile page, identified by its URL. The representation is the HTML document the server sends for that URL (a CSS file, `styles.css`, is a second resource the page needs). The same URL always names the same resource, even though the browser may receive a saved copy instead of a fresh one.