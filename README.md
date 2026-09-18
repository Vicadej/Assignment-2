# Campus Event Guide — Northridge University

A small, responsive two-page website built for the Office of Student Engagement so students can discover campus activities. "Northridge University," its organizations, and all events on the site are invented for this assignment.

**Pages**
- `index.html` — home page with a hero banner, a highlighted featured event, a grid of upcoming events, and an "About" section for the Office of Student Engagement.
- `event.html` — a detail page for the featured event ("Fall Welcome Fest") with a full description, schedule table, quick-facts sidebar, photo gallery, and campus map.

## Project structure

```
Assignment-2/
├── index.html
├── event.html
├── css/
│   └── styles.css
└── README.md
```

## Design decisions

**Layout & responsiveness.** The stylesheet is written mobile-first: the base rules target small screens (single-column event cards, stacked navigation), then two `min-width` breakpoints (`600px` and `900px`) progressively switch layouts to a two-column featured card, a 2- or 3-column event grid, and a two-column article/sidebar layout on the event page. This was chosen over a desktop-first approach because most students will first check event listings from a phone between classes.

**Color palette.** Navy (`#14213D`) and gold (`#FCA311`) were chosen as a classic "state university" color scheme that reads as trustworthy and energetic without needing a real school's branding. Neutral grays and a soft off-white background (`#F4F6FA`) keep long text sections readable, and all text/background pairings were checked for WCAG AA contrast.

**Typography.** Google Fonts' Poppins (headings) pairs a friendly, rounded geometric sans with Inter (body text), which is optimized for on-screen readability at small sizes. Both are loaded via `<link>` with `preconnect` hints for performance, and fall back to system sans-serif fonts if the request fails.

**Accessibility.** Both pages include a "skip to main content" link, a single `<h1>` per page, and landmark elements (`header`, `nav`, `main`, `aside`, `footer`). Interactive elements have visible focus outlines (`:focus-visible`), and the current page is marked in navigation with `aria-current="page"`.

**No JavaScript.** The deliverables call for HTML and CSS only, so navigation, layout, and interactivity (hover/focus states, responsive reflow) are handled entirely with semantic HTML and CSS — no build step or script is required to view the site.

**Images.** Photos are referenced at fixed paths in `images/` with descriptive alt text, ready for real photos to be dropped in:

| Path | Used for |
|---|---|
| `images/hero.jpg` | Home page hero banner |
| `images/event-open-mic.jpg` | Open Mic Night card |
| `images/event-career-fair.jpg` | Career & Internship Fair card |
| `images/event-homecoming.jpg` | Homecoming Rivalry Game card |
| `images/event-food-fest.jpg` | International Food Festival card |
| `images/event-yoga.jpg` | Wellness & Yoga Workshop card |

A dark gradient overlay sits between the hero photo and its text so the heading and buttons stay readable over any photo.

**Event cards.** Each of the 5 upcoming-event cards includes an image, name, date/time, location, a category tag (Social, Career, Athletics, Culture, Wellness), a short description, and a "View Details" link. Since this assignment only calls for one event detail page, every "View Details" link points to `event.html`; each link has a unique `aria-label` naming its event so it remains meaningful out of context (e.g. "View details for Open Mic Night") rather than pointing to unbuilt pages. The grid itself uses CSS Grid at three different widths — 1 column on mobile, 2 at the 600px breakpoint, 3 at the 900px breakpoint.

## Viewing the site

No build step or server is required. Clone the repository and open `index.html` in a browser, or serve the folder locally, e.g.:

```
npx serve .
```
