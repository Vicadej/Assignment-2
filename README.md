# Campus Event Guide — Northridge University

## Project Description

Campus Event Guide is a two-page website for the Office of Student Engagement at Northridge University (a fictional school invented for this assignment). Its purpose is to give students one place to browse what's happening on campus — a home page listing upcoming events, and a detail page for the semester's featured event with a full schedule and quick facts.

**Intended audience:** currently enrolled students looking for something to do on campus (social events, career fairs, games, wellness sessions), especially first-years and students who aren't already plugged into individual clubs' social media. A secondary audience is other campus organizations, who could use this as a template for how their own events might be listed.

**Pages**
- `index.html` — home page with a hero banner, a highlighted featured event, a grid of 5 upcoming events, and an "About" section.
- `event.html` — a detail page for the featured event ("Fall Welcome Fest") with a large hero image, full description, schedule table, accessibility info, a quick-facts sidebar with an RSVP button, and a related-events section.

## Project Structure

```
Assignment-2/
├── index.html
├── event.html
├── css/
│   └── styles.css
├── images/
└── README.md
```

## Layout Decisions

**CSS Grid** was used wherever content needed to align on two axes at once (rows *and* columns), or needed unequal column widths:
- `.event-grid` (index.html, upcoming events) — the 5 event cards need to snap into strict, equal-width columns whose *count* changes at each breakpoint (1 → 2 → 3). Grid's `grid-template-columns` makes that a one-line change per breakpoint, which would need more workarounds with Flexbox.
- `.event-details-grid` (event.html, main content + sidebar) — a genuine two-column page layout with *unequal* column widths (`2fr 1fr`). Grid's `fr` units were the natural fit.
- `.featured-card` (index.html) — the featured-event card becomes a two-column image/content layout at the 600px breakpoint.

**Flexbox** was used wherever content needed to align or distribute along a single axis, especially when it also needed to wrap:
- `.site-nav ul` and `.header-inner` — the logo and nav links sit on one axis and need to wrap onto their own line on narrow screens; `justify-content: space-between` and `flex-wrap: wrap` handle this directly.
- `.hero-actions` and `.event-hero-tags` — button/tag rows that wrap onto a second line if the screen is too narrow.
- `.event-card` (internal layout) — stacks the image and body vertically and uses `margin-top: auto` on the "View Details" link to pin it to the bottom of the card regardless of description length — a classic one-axis Flexbox trick that Grid can't do as simply.
- `.related-events-list` (event.html) — a row of compact cards that should wrap onto multiple lines as space allows, rather than snapping to fixed columns, so Flexbox's `flex-wrap` fit better than Grid's fixed tracks.

## Responsive Design

The stylesheet is mobile-first: base (unprefixed) rules target the smallest screens, and two `min-width` media queries progressively enhance the layout.

| Breakpoint | What changes |
|---|---|
| Base (< 600px) | Single-column nav (logo above links), 1-column event grid, stacked featured card, single-column event-details layout (sidebar stacks below the main article), related-event cards wrap to 1 per row. |
| `min-width: 600px` | Header becomes a row (logo left, nav right), event grid becomes 2 columns, featured card becomes 2 columns (image beside text), footer becomes 3 columns. |
| `min-width: 900px` | Event grid becomes 3 columns, event-details layout becomes 2 columns (`2fr 1fr` article + sidebar), hero heading sizes increase, the event hero image gets a fixed height. |

**Testing.** Both pages were checked at three representative widths using a browser's responsive design mode — roughly 375px (phone), 768px (tablet), and 1280px (desktop) — confirming the nav collapses/expands correctly, the event grid changes column count at each breakpoint, and the event-details sidebar moves below the main content on narrow screens. Pages were also served locally (`python -m http.server`) to confirm all assets load correctly outside the editor.

## Semantic HTML

- **`<main>`** — exactly one per page, wrapping all primary content so assistive tech (and the "skip to main content" link) can jump straight past the repeated header/nav.
- **`<article>`** — used for each event card and for the event-detail write-up (`.event-main`), since each represents independent, self-contained content that would still make sense on its own, outside the page.
- **`<figure>` / `<figcaption>`** — wraps every image so its caption is explicitly associated with it in the markup, not just placed nearby visually. On event cards, the category badge (Social, Career, etc.) *is* the figcaption; on hero photos, a screen-reader-only figcaption describes the scene.
- **`<time datetime="…">`** — every date and time value (event cards, the schedule table, sidebar quick facts) uses `<time>` with a machine-readable `datetime` attribute, rather than plain text.
- **`<nav aria-label="…">`** — used for both the primary site navigation and the breadcrumb on event.html, so screen reader users can jump directly to either navigation landmark and tell them apart.
- **`<aside>`** — the event-detail Quick Facts sidebar is marked as tangential/supplementary to the main article, not part of the primary content flow.

## Sources

**Fonts.** Poppins (headings) and Inter (body text) are loaded from Google Fonts (fonts.google.com) via `<link>`, free to use under the Open Font License.

**Images.** All photographs in `images/` were downloaded from Unsplash (unsplash.com) and Pexels (pexels.com) and are used under their respective free-to-use licenses (neither requires attribution, but they're credited here for transparency):

| File | Used for |
|---|---|
| `images/hero.jpg` | Home page hero banner |
| `images/event-open-mic.jpg` | Open Mic Night card |
| `images/event-career-fair.jpg` | Career & Internship Fair card |
| `images/event-homecoming.jpg` | Homecoming Rivalry Game card |
| `images/event-food-fest.jpg` | International Food Festival card |
| `images/event-yoga.jpg` | Wellness & Yoga Workshop card |
| `images/welcome-fest.jpg` | Event detail page hero banner |

**Borrowed content.** None — all copy (event names, descriptions, schedule, organization names, and the university itself) was written for this assignment and is fictional.

## Viewing the Site

No build step or server is required. Clone the repository and open `index.html` in a browser, or serve the folder locally, e.g.:

```
npx serve .
```
