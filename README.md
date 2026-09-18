# Campus Event Guide — Northridge University

## Project Description

This is a two-page site I made for a fake school's Office of Student Engagement. The idea is pretty simple: give students one place to check what's going on around campus instead of digging through five different Instagram pages. There's a home page with a list of upcoming events, and a details page for whatever event is "featured" that week.

**Who it's for:** students at Northridge who want to find something to do — parties, career fairs, games, yoga, whatever. Probably most useful for freshmen who don't already know all the clubs.

**Pages**
- `index.html` — home page. Hero image up top, a featured event, a grid of 5 other events, and an About section.
- `event.html` — the details page for the featured event (Fall Welcome Fest). Has the full rundown, a schedule, a sidebar with the quick facts and an RSVP button, and a few related events at the bottom.

## Layout Decisions

I used **CSS Grid** anywhere I needed things lined up in actual rows and columns:
- `.event-grid` (the event cards on index.html) — needed the cards to snap into even columns and change how many columns there are depending on screen size (1 → 2 → 3). Grid made that easy with just `grid-template-columns`.
- `.event-details-grid` (event.html main content + sidebar) — two columns that aren't the same width (`2fr 1fr`), which Grid handles way better than trying to fake it with Flexbox.
- `.featured-card` — turns into a 2-column image + text layout once the screen's wide enough.

I used **Flexbox** anywhere stuff just needed to line up in a row (or column) and possibly wrap:
- `.site-nav ul` / `.header-inner` — logo and nav links, wraps onto its own line on small screens.
- `.hero-actions` / `.event-hero-tags` — button and tag rows that wrap if there's not enough space.
- `.event-card` — stacks the image and text vertically, and I used `margin-top: auto` on the "View Details" link so it always sticks to the bottom of the card no matter how long the description is. That's a Flexbox thing, not really doable with Grid as easily.
- `.related-events-list` — just a row of small cards that wraps to as many per line as fits, so Flexbox made more sense than forcing a fixed number of Grid columns.

## Responsive Design

I wrote the CSS mobile-first — the plain styles are for small screens, then I added two breakpoints on top of that:

- **Under 600px (default)** — nav is stacked (logo on top, links below), event cards are 1 per row, the featured card is stacked, and on the event page the sidebar just falls below the main content.
- **600px and up** — nav goes horizontal (logo left, links right), event cards go to 2 per row, featured card becomes 2 columns, footer becomes 3 columns.
- **900px and up** — event cards go to 3 per row, the event page becomes a real 2-column layout (main content + sidebar side by side), and text gets a bit bigger.

**How I tested it:** mostly just resized my browser window and used the responsive mode in dev tools, checking around phone size (375px), tablet (768px), and a normal laptop width (1280px) to make sure nothing broke — nav collapsing right, cards reflowing, sidebar dropping below content on the narrow view. Also ran it through a local server real quick just to double check everything loaded outside the editor.

## Semantic HTML

- **`<main>`** — one per page, wraps everything that isn't the header/nav/footer.
- **`<article>`** — used on each event card and on the main event write-up, since they're the kind of content that'd still make sense if you pulled them out on their own.
- **`<figure>` / `<figcaption>`** — every image is wrapped in one so the caption is actually tied to the image in the code, not just sitting near it. The little category badge on each event card (Social, Career, etc.) is technically the figcaption.
- **`<time datetime="…">`** — used this for every date/time on the site instead of just plain text, so it's machine-readable.

## Sources

**Fonts.** Just system fonts (`"Segoe UI", Arial, sans-serif`) — didn't pull in anything from Google Fonts or anywhere else.

**Images.** All the photos in `images/` came from Unsplash and Pexels, both free to use without needing credit, but listing them here anyway:

- `images/hero.jpg` — home page hero banner
- `images/event-open-mic.jpg` — Open Mic Night card
- `images/event-career-fair.jpg` — Career & Internship Fair card
- `images/event-homecoming.jpg` — Homecoming Rivalry Game card
- `images/event-food-fest.jpg` — International Food Festival card
- `images/event-yoga.jpg` — Wellness & Yoga Workshop card
- `images/welcome-fest.jpg` — event details page hero banner

**Borrowed content.** None — I wrote all the event names, descriptions, and made up the whole school myself.

## Viewing the Site

Just clone the repo and open `index.html` in a browser.
