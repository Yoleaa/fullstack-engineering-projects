# Project 001: Developer profile website

**Level 1** | **Difficulty:** Beginner | **Live site:** 
https://yoleaa.github.io/fullstack-engineering-projects/01-web-foundations/project-001-developer-profile/

A one-page profile built with only HTML and CSS: semantic structure, responsive layout, keyboard-friendly navigation.

## Run it
Open `index.html` in a browser. No build step.

## Deploy with GitHub Pages
1. Push this folder to your repository.
2. On GitHub: Settings, then Pages, then choose your branch and the folder that holds `index.html`.
3. Wait a minute, then open the URL GitHub shows and paste it above.

## What is inside
- `index.html`, `css/styles.css`, `assets/`
- `docs/lesson.md` (skills, book references, exercises), `docs/http-notes.md`, `docs/decisions.md`

## Screenshot
(add one at 375 px and one at 1280 px)

## Lessons learned
## Lessons learned

**Web and HTTP**
- A web page is a resource at a URL, and the HTML the server sends is one representation of it.
- A normal reload sends `Cache-Control: max-age=0` and conditional headers (`If-None-Match` with an ETag, `If-Modified-Since`). The server answered `304 Not Modified`, so the browser reused its saved copy. A hard reload (Ctrl+Shift+R) fetches a fresh `200`.
- Response headers such as `Cache-Control: max-age=600` tell browsers how long they may reuse a page.
- A CDN cache sat in front of GitHub Pages (`X-Cache: HIT`, `Via`), so my request wasn't answered by GitHub's main servers.

**HTML and CSS**
- Semantic elements (`header`, `nav`, `main`, `section`, `article`, `footer`) give a page structure that screen readers and search engines can use.
- CSS custom properties keep colours and spacing in one place.
- A mobile-first layout with one `@media` query, Flexbox and Grid works on phone and desktop. My page scored above 95 on Lighthouse for Accessibility and Best Practices.

**Git and GitHub**
- A branch only exists after the first commit, so `git push` fails with "src refspec main does not match any" until I commit.
- Git must be started from the top repository folder, not inside a subfolder.
- Paths with spaces need quotes in PowerShell.
- GitHub Pages can serve a page from a subfolder, and updates take a few minutes to appear.

**Tools**
- On my laptop, F12 toggles airplane mode, so I open DevTools with Ctrl+Shift+I.
- The Network tab's filter buttons can hide requests. "All" must be selected to see the page request.
- DevTools can be docked or undocked to give the request list more room.
