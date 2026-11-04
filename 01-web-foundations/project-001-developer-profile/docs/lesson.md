# Lesson: Project 001, Developer profile website

**Level 1 | Beginner | Planned time: 1 day**

> **About the book references.** I do not have the text of your books, so I cite chapters and topics from my knowledge of their tables of contents. Check each one against the contents page of your own copy before relying on it.

## Skills you learn in this project

| # | Skill | Where it appears in the code |
|---|---|---|
| 1 | Structure a page with semantic HTML | `index.html`: `header`, `nav`, `main`, `section`, `article`, `footer`; one `h1`, then `h2`, then `h3` |
| 2 | Link inside a page with ids and anchors | `<a href="#about">` jumps to `<section id="about">` |
| 3 | Keep design values in one place with CSS custom properties | `:root { --signal: #0b5fa5; --space-3: 16px; }` in `styles.css` |
| 4 | Build a mobile-first responsive layout | Base CSS is for phones; one `@media (min-width: 768px)` block adds the wide layout |
| 5 | Lay out with Flexbox and Grid | Header and buttons use Flexbox; skills use Grid `auto-fit`; cards use Grid |
| 6 | Make a page accessible | `lang="en"`, skip link, `:focus-visible` outline, `aria-labelledby`, 4.5:1 contrast |
| 7 | Read an HTTP exchange | The Network-tab exercise below |
| 8 | Publish a static site with Git | GitHub Pages deployment in the README |

## Book references

| Skill | Book | Chapter / topic |
|---|---|---|
| A page is a *resource* at a *URI*; the HTML is a *representation* of it | RESTful Web Services | Ch. 1 (The Programmable Web and Its Inhabitants); Ch. 4 (The Resource-Oriented Architecture: resources, URIs, representations) |
| What a URL is; the `#fragment` part | HTTP: The Definitive Guide | Ch. 2 (URLs and Resources) |
| Requests, responses, methods, status codes, headers | HTTP: The Definitive Guide | Ch. 1 (Overview) and Ch. 3 (HTTP Messages) |
| `Content-Type` and media types | HTTP: The Definitive Guide | Ch. 15 (Entities and Encodings) |
| `Cache-Control`, `ETag`, `304 Not Modified` | HTTP: The Definitive Guide | Ch. 7 (Caching) |
| Git commits and branches | Pro Git | Ch. 1-2 (Getting Started; Git Basics) |

Eloquent JavaScript is not needed yet: this project has no JavaScript.

## How the code works

**`index.html`**
- The `<head>` has `charset`, the `viewport` meta tag (without it, phones shrink the page to desktop width) and the stylesheet link.
- `<main>` holds five `<section>` elements. Each has an `id` for the nav links and an `aria-labelledby` pointing to its heading, so screen readers announce the section name.
- Project cards are `<article>` elements because each one makes sense on its own.

**`css/styles.css`**
- `:root` holds colours, spacing and fonts as variables. Changing `--signal` re-colours links, buttons and the section line everywhere.
- `*, *::before, *::after { box-sizing: border-box; }` makes padding count inside an element's width, which prevents sideways scrolling.
- Phone styles come first. The wide layout only changes the header padding and makes the cards three across.
- `.skill-groups` uses `repeat(auto-fit, minmax(13rem, 1fr))`, so columns appear as space allows without a media query.
- `clamp(2rem, 7vw, 3.5rem)` on the `h1` scales the heading smoothly between phone and desktop.
- The blue line on the left of each section is a plain `border-left`. The idea comes from your engineering background: a cable run on a plan.

## Your exercises (this is where you learn it)

1. **Make it yours.** Replace the `github.com` and `linkedin.com` links with your real profile URLs, then check every claim on the page is something you can show.
2. **Change the palette.** Edit only the `:root` variables, then check contrast with Chrome DevTools (inspect a text element and open the colour picker). Keep 4.5:1 or higher.
3. **Break and fix it.** Delete the viewport meta tag and open the page on your phone. Write one sentence in `docs/decisions.md` about what happened, then put the tag back.
4. **Add a fourth project card** without copying the CSS: reuse the `.card` class.
5. **Stretch: dark mode.** Add `@media (prefers-color-scheme: dark) { :root { ... } }` that redefines `--ink`, `--paper` and `--surface`.

## HTTP exercise (about 20 minutes, after you deploy)

1. Open your deployed page in Chrome and press F12, then open **Network** and reload.
2. Click the first request (the document) and fill in `docs/http-notes.md`: method, URL, status code, `Content-Type`, caching headers, size.
3. Reload again. Did the status change (for example to `304`)? Why? (HTTP: The Definitive Guide, Ch. 7)
4. Write two sentences: what did the browser do, and what did the server do?
5. Link to RESTful Web Services: in your own words, what is the *resource* here, and what is its *representation*?

## Done checklist

- [ ] HTML validates at validator.w3.org with zero errors
- [ ] Lighthouse (DevTools) Accessibility and Best Practices at 90 or higher
- [ ] No sideways scrolling at 360 px, 768 px and 1280 px
- [ ] Keyboard only: you can reach every link with Tab and see where focus is
- [ ] Deployed; live link in the README
- [ ] `docs/http-notes.md` and `docs/decisions.md` filled in
- [ ] At least 8 meaningful commits

## Common mistakes

- Using `<div>` where `<section>`, `<nav>` or `<article>` fits.
- Fixed pixel widths that overflow a phone screen.
- Low-contrast grey text on a white background.
- Claiming skills on the page that you cannot demonstrate.
