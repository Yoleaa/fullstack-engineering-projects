# Lesson: Project 002, Profile page

**Level 1 | Beginner | Planned time: 1 day**

> **About the book references.** I do not have the text of your books, so I cite chapters and topics from my knowledge of their tables of contents. Check each one against the contents page of your own copy.

## Skills you learn in this project

| # | Skill | Where it appears in the code |
|---|---|---|
| 1 | Link between pages and folders with relative URLs | `index.html`: `<a href="../project-001-developer-profile/">Home</a>` |
| 2 | Use content elements for what they mean | `figure`/`figcaption`, `dl` (facts), `ol` with `time` (timelines), `address` (contact) |
| 3 | Add an image properly | `<img>` with `alt`, `width` and `height`; in CSS `max-width: 100%; height: auto` |
| 4 | Reuse and extend a stylesheet | `css/styles.css` is Project 001's file plus a block marked "Project 002 additions" |
| 5 | Build a timeline with CSS only | `.timeline li` border-left plus a `::before` dot |
| 6 | Use Grid for a label/value list | `.facts { grid-template-columns: max-content 1fr; }` |
| 7 | See how one page needs several requests | Network tab exercise below |
| 8 | Write only what you can prove | Every entry on the page matches a certificate, email or your CV |

## Book references

| Skill | Book | Chapter / topic |
|---|---|---|
| Every resource has its own URI (addressability) | RESTful Web Services | Ch. 4 (The Resource-Oriented Architecture) |
| Relative and absolute URLs, and how a browser resolves them | HTTP: The Definitive Guide | Ch. 2 (URLs and Resources) |
| Status codes such as 200, 304, 404 | HTTP: The Definitive Guide | Ch. 3 (HTTP Messages) |
| `Content-Type` for HTML, CSS and SVG | HTTP: The Definitive Guide | Ch. 15 (Entities and Encodings) |
| Caching of CSS and images | HTTP: The Definitive Guide | Ch. 7 (Caching) |
| Committing and pushing changes | Pro Git | Ch. 2 (Git Basics) |

## How the code works

- **Relative links.** `../` means "go up one folder". Your two projects sit side by side, so from Project 002 the way to Project 001 is `../project-001-developer-profile/`. The browser turns it into a full address using the current page's URL.
- **The profile header** is a `<section>` with a `<figure>` (the image and its caption) and a `<dl>` (term and description pairs). On a phone the two stack; at 768 px the CSS makes two columns (`160px 1fr`).
- **The image** carries `width="160" height="160"`, so the browser reserves space before it loads and the page doesn't jump. `height: auto` in CSS keeps it in proportion when it shrinks.
- **`<time datetime="2023-10-09">`** gives machines a date they can read, while people see "9 October 2023".
- **The timeline** is an ordered list with the bullets removed. Each item has a grey left border; `::before` draws the blue dot on top of it.

## Your exercises

1. **Add your real photo.** Save a square photo (under 100 KB) as `assets/profile.jpg`, then change the `src` and `alt` text in `index.html`. Check its size in the Network tab.
2. **Cause a 404 on purpose.** Change the nav link `#education` to `certificates.html`, save, click it, and read the status in the Network tab. Then fix it. Write what the 404 means in your notes.
3. **Link the two projects.** In Project 001's `index.html`, add a nav link to Project 002 using a relative URL: `../project-002-profile-page/`.
4. **Check the data.** Compare every date and title on the page with your certificates. Fix anything that is not exact.
5. **Stretch:** make the timeline dots a different colour for education and experience, using a class on the `<li>`.

## HTTP exercise (after you deploy)

1. Open the live page, press **Ctrl+Shift+I**, go to **Network**, click **All**, and press **Ctrl+Shift+R**.
2. List every request: name, status, type and size. You should see the page, `styles.css` and the SVG image.
3. In `docs/http-notes.md`, record the `Content-Type` of each of the three. They should be different.
4. Reload normally (**Ctrl+R**) and note which requests become `304` or come from cache.
5. Do exercise 2 above and record the 404.

## Done checklist

- [ ] HTML validator: zero errors
- [ ] Lighthouse Accessibility and Best Practices: 90 or higher
- [ ] No sideways scrolling at 360 px; checked on a phone
- [ ] Every link works (nav, Home link, email)
- [ ] Image has `alt`, `width` and `height`
- [ ] Facts on the page match your documents
- [ ] Live link in the README; HTTP notes filled in
- [ ] Pushed to GitHub; tracker updated

## Common mistakes

- A wrong number of `../` in a relative link.
- Image with no `alt` text, or alt text like "image".
- Forgetting that GitHub Pages is case-sensitive: `Profile.jpg` and `profile.jpg` are different files.
- Putting claims on a public page that you cannot back up.
