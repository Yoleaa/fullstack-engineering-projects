# Design decisions (Project 002)

## ADR-001: Copy the stylesheet instead of sharing it
- **Context:** Projects 001 and 002 use the same look.
- **Decision:** Copy `styles.css` and add a clearly marked block of new rules.
- **Consequences:** Each project works on its own and deploys on its own, but a change to a shared rule has to be made twice. Later projects will share one stylesheet.

## ADR-002: SVG placeholder for the portrait
- **Decision:** Use a small SVG with initials until a real photo is added.
- **Consequences:** No broken image icon, and the file is tiny.
