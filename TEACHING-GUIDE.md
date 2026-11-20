# HTML & CSS Teaching Guide: Crown & Blade / Great Cut (Prime-Cut)

A lesson-by-lesson walkthrough of every HTML and CSS concept used in this project. Each concept points to the file where students can see it working.

## 0. Map of the project

| File | Role | Teaching purpose |
| --- | --- | --- |
| `semantics.html` + `style.css` | "Great Cut" lab page | Semantic HTML, media, selectors, colors, gradients, units, animation, positioning |
| `units.html` + `style.css` | Units demo | CSS units (absolute vs relative) |
| `flexbox.html` + `flexbox.css` | Layout lab | Flexbox and Grid basics |
| `index.html`, `about.html`, `team.html`, `services.html`, `reviews.html`, `book.html`, `contact.html` + `layout.css` | Final "Crown & Blade" site | Everything combined: Grid page layout, Flexbox components, forms, responsive design |
| `assets/` | Images, audio, video | Relative paths, media elements |

**Teaching order:** semantics.html, style.css, units.html, flexbox.html, then the full site.

---

# PART 1: HTML

## 1.1 Document skeleton (every page)

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>...</title>
    <link rel="stylesheet" href="layout.css" />
  </head>
  <body>...</body>
</html>
```

| Concept | What it does | Why it matters |
| --- | --- | --- |
| `<!doctype html>` | Tells the browser to use standards mode | Without it, the browser enters "quirks mode" |
| `<html lang="en">` | Root element, declares the language | Screen readers, translation, SEO |
| `<head>` vs `<body>` | Head holds metadata (not displayed). Body holds visible content | Basic page anatomy |
| `<meta charset="UTF-8">` | Character encoding | Makes `★`, `–`, `✦` and `&` render properly |
| `<meta name="viewport">` | Sets the mobile viewport width | **Required** for responsive CSS to work on phones |
| `<meta name="description">` (`semantics.html`) | Search-result snippet | SEO |
| `<title>` | Browser tab text | Usability and SEO |
| `<link rel="stylesheet" href>` | Attaches an **external** stylesheet | Separation of structure and style |
| `<!-- comments -->` | Notes for developers | Seen all through the files. The commented-out `<style>` block in `semantics.html` shows **internal CSS** as the alternative |

**Three ways to add CSS** (all discussed in the files):
1. **External**: `<link>` to a `.css` file (used throughout).
2. **Internal**: `<style>` in `<head>` (commented example in `semantics.html`).
3. **Inline**: `style="width: 98%;"` (used on `.bar-fill` in `reviews.html`). Use it only for one-off, data-driven values.

External CDN stylesheet: `index.html` loads **Font Awesome 6** from `cdnjs.cloudflare.com` to get `<i class="fa-solid fa-house">` icons.

## 1.2 Semantic structure elements

Taught in `semantics.html`, then applied in the full site.

| Element | Meaning | Where used |
| --- | --- | --- |
| `<header>` | Introductory area or site header | Both sites |
| `<nav aria-label="Main">` | Block of navigation links | Both sites |
| `<main id="main">` | The page's unique main content (one per page) | Both sites |
| `<section>` | A thematic grouping, usually with a heading | Every content group |
| `<article>` | Self-contained content that still makes sense alone | Service cards, barber profiles |
| `<aside>` | Related but secondary content | Booking tip (`semantics.html`), sidebar menu (`index.html`) |
| `<footer>` | Footer of the page or section | Both sites; also inside `<blockquote>` |
| `<address>` | Contact information | `semantics.html` footer |
| `<blockquote>` + `<cite>` | A quotation and its source | `semantics.html` |
| `<figure>` / `<figcaption>` | Image with a caption | Not used in any page yet. `layout.css` already styles `.gallery-item figcaption`, so it makes a good exercise to add |

**Talking point:** a `<div>` has no meaning. Semantic tags let browsers, screen readers and search engines understand the page. Compare `<div class="header">` with `<header>`.

## 1.3 Headings, text and inline elements

| Element | Purpose | Example |
| --- | --- | --- |
| `<h1>` to `<h4>` | Heading hierarchy (one `<h1>` per page) | `<h1 id="hero-title">` |
| `<p>` | Paragraph | Everywhere |
| `<strong>` | Strong importance (bold) | Prices, stats |
| `<small>` | Fine print | Copyright line |
| `<mark>` | Highlighted text | "seconds" in the hero title |
| `<span>` | Generic inline container | `<span class="price">` |
| `<br />` | Line break | Addresses |
| `<time datetime="08:00">` | Machine-readable time | Opening-hours table |
| `<i class="fa-...">` | Icon hook (Font Awesome) | Nav, footer |

## 1.4 HTML entities

Characters that are reserved or hard to type:

| Entity | Shows | Entity | Shows |
| --- | --- | --- | --- |
| `&amp;` | & | `&copy;` | © |
| `&bull;` | • | `&middot;` | · |
| `&ndash;` | – | `&mdash;` | — |
| `&ldquo;` | " | | |

`&amp;` is **required** for a literal `&` (e.g. `Crown &amp; Blade`).

## 1.5 Links and navigation

| Concept | Example | Notes |
| --- | --- | --- |
| Relative page link | `<a href="team.html">` | Links between pages of the site |
| Fragment (anchor) link | `href="#"`, `id="brian"` | Jumps to an element with that `id` |
| External link | `href="https://instagram.com"` | Absolute URL |
| `target="_blank"` + `rel="noopener noreferrer"` | Opens a new tab **safely** | Social links in footer |
| `tel:` link | `href="tel:+254725439354"` | Tap-to-call on phones |
| `mailto:` link | `href="mailto:email@example.com"` | Opens the mail app |
| `aria-current="page"` | Marks the current page for screen readers | `semantics.html` nav |
| `class="active"` | Styled current-page marker | `index.html` sidebar |

## 1.6 Lists and tables

- **Unordered list** `<ul><li>`: nav menus, amenities, footer links.
- **Ordered list** `<ol><li>`: the "How it works" steps.
- **Nested content in `<li>`**: headings and paragraphs inside list items.
- **Table** (`semantics.html`): `<table>`, `<caption>`, `<tbody>`, `<tr>`, `<th scope="col|row">`, `<td>`. The `scope` attribute tells assistive tech whether a header labels a column or a row.

## 1.7 Media

| Element | Attributes taught | File |
| --- | --- | --- |
| `<img>` | `src`, `alt`, `width`, `height`, `class` | All pages |
| `<audio>` | `controls`, `preload="none"`, nested `<source src type>` | `semantics.html` |
| `<video>` | `controls`, `preload="none"`, `poster`, `width`, `height`, `<source>` | `semantics.html` |

**Talking points:**
- `alt` is mandatory: accessibility plus fallback text.
- `preload="none"` saves bandwidth until the user presses play.
- Paths: `assets/logo.jpg` is **relative**, `https://images.unsplash.com/...` is **absolute**. Query-string options (`?w=800&q=80`) are processed by the image server.
- `<source>` lets you offer several formats; the browser picks the first it supports.

## 1.8 Forms

The most concept-dense part of the site (`index.html`, `book.html`, `contact.html`, `reviews.html`).

```html
<form action="book.html" method="get">
  <div class="form-row">
    <label for="client-name">Full Name</label>
    <input type="text" id="client-name" name="name" placeholder="e.g. David Kamau" required />
  </div>
  ...
  <button type="submit">Confirm Appointment Request</button>
</form>
```

| Concept | Details |
| --- | --- |
| `<form action method>` | Where and how data is sent (`get` puts it in the URL) |
| `<label for>` ↔ `<input id>` | Binds label to field. Clicking the label focuses the input |
| `name` attribute | The key sent with the form data. **Without it, the field is not submitted** |
| Input types | `text`, `tel`, `email`, `date`, `radio`, `checkbox` |
| `<select>` + `<option value>` | Dropdown. `value` is what is sent, the text is what the user sees |
| `<textarea rows>` | Multi-line text |
| `placeholder` | Hint text inside the field |
| `required` | Built-in browser validation (no JavaScript) |
| `disabled` | Unselectable option (the 17:00 slot in `book.html`) |
| `checked` | Pre-selected checkbox (SMS / WhatsApp preferences) |
| Radio groups | Radios sharing the same `name` are mutually exclusive (service picker, time slots) |
| Checkbox groups | Same `name`, multiple values allowed (`preferences`) |
| `<button type="submit">` | Submits the form |

**Demo:** submit `book.html` with an empty field to show built-in validation, then look at the URL after a valid submission to see `?name=...&phone=...`.

## 1.9 Interactive element without JavaScript

`contact.html` FAQ: `<details class="faq-item" open>` with `<summary>`. The `open` attribute makes one item expanded by default. Browsers handle the toggling natively.

## 1.10 Accessibility attributes used

| Attribute | Use |
| --- | --- |
| `alt` | Describes images |
| `aria-label` | Names nav landmarks and icon-only social links |
| `aria-labelledby="hero-title"` | Names a `<section>` from its heading's `id` |
| `aria-current="page"` | Identifies the current page |
| `lang` | Declares the language |
| `scope` on `<th>` | Table header direction |

## 1.11 Global attributes: `id` vs `class`

- **`id`**: unique per page. Used for anchors, `aria-labelledby`, and `for`/`id` pairing.
- **`class`**: reusable styling hook, and multiple classes can combine (`class="conta row"`, `class="btn-primary full-width"`, `class="showcase-banner banner-home"`).

---

# PART 2: CSS

## 2.1 Where the CSS lives

- **`style.css`** is the *lab* file. It has experiments (hence deliberately ugly output, such as aqua text on every element).
- **`layout.css`** is the *production* stylesheet for Crown & Blade. It is organized in commented sections.
- **`flexbox.css`** is the focused layout lab.

> Note for teaching: `style.css` uses `* { padding: 5px; margin: 5px; color: aqua }` as a **demo of the universal selector**. `layout.css` uses a *reset* instead (`padding: 0; margin: 0`).

## 2.2 Syntax anatomy

```css
selector {
  property: value;   /* declaration */
}
```

Comments: `/* ... */`. Both files use comments to label sections, and to disable code (e.g. the `.unit-mm` block).

## 2.3 Selectors (all in `style.css`, applied in `layout.css`)

| Selector type | Example | Meaning |
| --- | --- | --- |
| Element (type) | `body`, `header`, `h1` | Every matching tag |
| Universal | `* { ... }` | Every element |
| Class | `.btn`, `.hero` | Elements with `class="btn"` |
| ID | `#logo`, `#hero-title` (commented) | The one element with that `id` |
| Attribute | `a[href]` | Anchors that have an `href` |
| Attribute with value | `.option input[type="radio"]` | Inputs of a specific type |
| Descendant | `nav ul li`, `section p` | Any depth inside |
| Child | `section > p` | Direct children only |
| Adjacent sibling | `h3 + p` | The paragraph immediately after an `h3` |
| General sibling | `h1 ~ p` (commented) | All later sibling paragraphs |
| Group | `h1, h2 { ... }` | Same rules for several selectors |
| Compound | `.aside nav a.active` | Combines class, tag and descendant |
| Pseudo-class | `:hover`, `:focus`, `:first-child`, `:has()`, `:disabled`, `[open]` | State-based styling |
| Pseudo-element | `::before`, `::after`, `::-webkit-details-marker` | Generated or special parts |

Examples to point to in `layout.css`:
- `.card:hover`, `.btn-primary:hover` (hover states)
- `.form-row input:focus` (focus state)
- `.location-card h4:first-child` (structural pseudo-class)
- `.slot:has(input[type="radio"]:disabled)` (the modern `:has()` parent selector)
- `.faq-item[open]` (attribute state of `<details>`)
- `.addon-list li::before { content: "✦ "; }` (decorative generated content)
- `.faq-item summary::after { content: "+"; }` swapped to `"−"` when open

## 2.4 Cascade, inheritance and specificity

Key ideas shown in the project:
- **Inheritance:** `color: inherit` on `a` makes links take the parent's color. `font-family: inherit` on form fields fixes browsers' default form fonts.
- **Cascade order:** later rules win at equal specificity. `style.css` sets `* { color: aqua }`, but more specific rules (`section > p`, `h3 + p`) override it.
- **Specificity ladder:** element < class < ID < inline. Compare `.btn-primary` (one class) with `.aside nav a.active` (higher specificity), which is why the active state wins.
- **Reset:** `* { box-sizing: border-box; padding: 0; margin: 0 }` removes browser default spacing.

## 2.5 Colors

| Format | Example |
| --- | --- |
| Named | `white`, `aqua`, `grey`, `chocolate`, `antiquewhite` |
| Hex (RRGGBB) | `#4f2323`, `#0c0a09` |
| Hex with alpha | `#dddd` (short form, 4 digits) |
| `rgb()` | `rgb(0, 255, 255)` |
| `rgba()` (transparency) | `rgba(255, 255, 255, 0.18)` |
| `hsl()` | `hsl(0, 75%, 14%)` |
| `transparent` | `border: 20px solid transparent` |

## 2.6 Custom properties (CSS variables) in `layout.css`

```css
:root {
  --accent-amber: #d99b43;
  --radius-md: 10px;
}
.price { color: var(--accent-amber); }
```

- `:root` = the `<html>` element, so variables are global.
- `var(--name)` reads a variable.
- **Why:** change the whole theme in one place. The palette is grouped as backgrounds, borders, text, accent, radius.

## 2.7 Typography

| Property | Used for |
| --- | --- |
| `font-family` | Font stacks with fallbacks: `"Segoe UI", -apple-system, ..., sans-serif`; serif stack for headings |
| `font-size` | `rem` values throughout |
| `font-weight` | `500`, `600`, `700` |
| `font-style: italic` | `h3 + p`, `.review-body` |
| `line-height` | `1.6` on body (unitless) |
| `letter-spacing` | Uppercase labels (`0.16em`) |
| `text-transform: uppercase` | Labels and nav (`style.css` and `layout.css`) |
| `text-align` | `center`, `left`, `right` |
| `text-decoration: none` | Removes link underline |
| `text-shadow` | `2px 2px 1px black` (`style.css`) |

Design lesson: pairing a **serif** (Georgia) for headings with a **sans-serif** body gives the "luxury" feel.

## 2.8 The box model

Every element is a box: **content, padding, border, margin**.

| Property | Examples |
| --- | --- |
| `width`, `height` | `100px`, `100%`, `100vh`, `60%` |
| `min-height`, `max-width` | `min-height: 100vh`, `max-width: 1320px` |
| `padding` | `1.5rem 2rem` (vertical, horizontal shorthand) |
| `margin` | `margin: 0 auto` centers a block horizontally |
| `border` | `1px solid var(--border-subtle)` |
| `border-left: 3px solid transparent` | Reserves space so hover/active doesn't shift layout |
| `border-style: dotted` | `.box` in `style.css` |
| `border-radius` | `6px`, `50%` (circle), `999px` (pill) |
| `border-image` | `.border-img` in `style.css` (image used as border) |
| `box-sizing: border-box` | Width includes padding and border: **the single most useful reset** |
| `overflow: hidden` | Clips children to rounded corners (`.gallery-item`, `.bar-track`) |

Shorthand rules: 1 value = all sides; 2 = vertical/horizontal; 4 = top, right, bottom, left (clockwise).

## 2.9 CSS units (`units.html` + `style.css`)

| Type | Units | Notes |
| --- | --- | --- |
| Absolute | `px`, `mm`, `cm`, `in`, `Q` | Fixed size (the commented-out `.unit-mm` etc. rules) |
| Relative to font | `em` (parent's font size), `rem` (root font size), `%` | `.unit-em` compounds, `.unit-rem` stays predictable |
| Relative to viewport | `vw`, `vh` | `5vw` scales with window width, `100vh` = full screen height |
| Unitless | `line-height: 1.6`, `flex: 1`, `opacity` | Multipliers/ratios |
| Fractions | `fr` | Grid-only (see 2.14) |

**Best practice demonstrated in `layout.css`:** use `rem` for type and spacing, `%`/`fr` for layout, `px` for hairline borders and fixed icons.

## 2.10 Backgrounds and gradients

| Concept | Where |
| --- | --- |
| `background-color` | Everywhere |
| `background-image: url()` | `.hero`, `.container` (`style.css`) |
| `background-size: cover` | `.hero` |
| `background-repeat: no-repeat` | `.hero` |
| `background-attachment: fixed` | Parallax-style fixed background (`.hero`) |
| `background` shorthand | `.banner-home`: `center/cover no-repeat` |
| `linear-gradient` | `to right`, `to left`, `135deg`, `90deg` with stops (`0%`, `100%`) |
| `radial-gradient` | `.radial-grad`; `circle at top right` in `.showcase-banner` |
| `conic-gradient` | `.conic` color wheel with `from 45deg at 70% 20%` |
| **Layered backgrounds** | `.banner-home`: a semi-transparent gradient **on top of** a photo, separated by a comma, to keep text readable |
| `backdrop-filter: blur()` | Frosted-glass `.card` (`style.css`) |

## 2.11 Images and object fit

```css
img { display: block; max-width: 100%; }
.card-img { width: 100%; height: 185px; object-fit: cover; }
.barber-photo { object-position: top center; }
```

- `max-width: 100%`: responsive images that never overflow.
- `display: block`: removes the tiny gap under inline images.
- `object-fit: cover`: crops to fill without stretching.
- `object-position`: chooses the crop focus (faces at the top).
- `border-radius: 50%` on `img` in `flexbox.css` turns the logo into a circle.

## 2.12 The `display` property

| Value | Where |
| --- | --- |
| `block` | `img`, `.stat strong` |
| `inline-block` | `.brand-badge`, `.btn-primary`, `.eyebrow` (inline flow but accepts padding/margins) |
| `flex`, `inline-flex` | Most components, `nav ul` in `flexbox.css` |
| `grid`, `inline-grid` | Page layout and card grids |
| `none` | Hides the default `<summary>` arrow (`summary::-webkit-details-marker`) |

## 2.13 Flexbox (`flexbox.css`, then `layout.css`)

**Container properties:**

| Property | Values used | Effect |
| --- | --- | --- |
| `display: flex` | | Turns children into flex items |
| `flex-direction` | `row` (default), `column` | Main axis direction |
| `justify-content` | `center`, `space-between`, `space-around`, `flex-start` | Alignment on main axis |
| `align-items` | `center`, `baseline`, `flex-start` | Alignment on cross axis |
| `flex-wrap: wrap` | | Items flow to new lines |
| `gap` | `1rem`, `0.65rem` | Space between items (no margin hacks) |

**Item properties:**

| Property | Where |
| --- | --- |
| `flex: 1 1 100px` (grow, shrink, basis) | `.wrap-sect` in `flexbox.css` |
| `flex: 1` | `.bar-track`, `.rating-breakdown` fills the leftover space |
| `flex-shrink: 0` | Icons in `.footer-contact li i` won't squash |

**Where flex is used in the site:** the hero bar, sidebar, buttons row, card top (name left, price right), stat boxes, footer bottom, form rows (label above input via `column`), radio options, social icons centered with `justify-content` + `align-items`.

**Teaching shortcut:** centering anything = `display:flex; align-items:center; justify-content:center`.

## 2.14 CSS Grid (`flexbox.css`, then `layout.css`)

| Concept | Example |
| --- | --- |
| `display: grid` | `.container`, `.cards-grid` |
| `grid-template-columns` | `250px 1fr 1fr 1fr`, `repeat(2, 1fr)`, `1.3fr 1fr`, `1.5fr 1fr 1fr 1.3fr` |
| `grid-template-rows` | `auto 1fr auto` (header/content/footer) |
| `repeat()` | `repeat(3, 1fr)` |
| `fr` unit | Share of the free space |
| `gap` with two values | `0.65rem 1.5rem` (row gap, column gap) |
| **`grid-template-areas`** | Named page layout: header / sidebar + content / footer |
| `grid-area` | Places `.hero`, `.aside`, `.main-area`, `.footer` into the named areas |
| `inline-grid` | `.inline` in `flexbox.css` |

The whole page skeleton:

```css
grid-template-areas:
  "header header header header"
  "sidebar content content content"
  "footer footer footer footer";
```

**When to use which:** Flexbox for one dimension (a row or a column of things). Grid for two dimensions (rows and columns together). This site combines both: Grid for page and card grids, Flexbox inside each card.

## 2.15 Positioning and stacking (`style.css`)

| Property | Demo |
| --- | --- |
| `position: relative` | `.container`, `#logo`: anchor for absolute children |
| `position: absolute` | `.card`, `.txt`, `.box1`, `.box2`: placed relative to the nearest positioned ancestor |
| `top`, `left` | Offsets |
| `z-index` | `.box1` (1) vs `.box2` (5): controls which overlaps |
| Centering trick | `left: 50%; top: 20%; transform: translate(-50%, -50%)` |

## 2.16 Transitions, transforms and animation

| Concept | Where |
| --- | --- |
| `transition: all 0.25s ease` | Links in `layout.css` |
| `transition: transform 0.8s, backdrop-filter 0.5s` | Multiple properties with different durations (`style.css`) |
| `transform: translateY(-2px)` | Social icon lifts on hover |
| `transform: translateX(3px)` | Footer chevron slides on hover |
| `transform: rotateY(180deg)` | Card flip on hover (`style.css`) |
| `@keyframes changeColor { from {...} to {...} }` | Color animation |
| `animation: changeColor 3s infinite` | Applying it to `.box` |
| `cursor: pointer` / `not-allowed` | Feedback on clickable and disabled items |
| `scroll-behavior: smooth` on `html` | Smooth anchor scrolling |

## 2.17 Form styling

- Dark inputs: `background-color`, `border`, `color`, `padding`, `font-family: inherit`.
- `outline: none` + `:focus { border-color: ... }` replaces the default focus ring with a custom one. (Teaching note: when you remove the outline, always provide a visible replacement.)
- `resize: vertical` on `textarea`.
- `accent-color: var(--accent-amber)` tints native radios and checkboxes.
- `opacity: 0.4` + `cursor: not-allowed` for disabled slots.

## 2.18 Lists

`list-style: none` removes bullets on nav, footer and amenities lists. The decorative bullet is re-added with `::before` and `content: "✦ "`.

## 2.19 Responsive design with media queries

```css
@media (max-width: 960px) { ... }   /* tablet */
@media (max-width: 768px) { ... }   /* small tablet */
@media (max-width: 600px) { ... }   /* phone */
```

What changes at each breakpoint:
- **960px:** page grid collapses to a single column (`grid-template-columns: 1fr` and redefined `grid-template-areas`, stacking header, sidebar, content, footer). Sidebar nav turns horizontal (`flex-direction: row`, left border becomes bottom border). Card, team, contact and form grids go to one column. Footer goes to 2 columns.
- **768px:** the rating card stacks; time slots go from 3 to 2 columns.
- **600px:** footer to 1 column and the copyright bar stacks and centers.

**Mobile-first vs desktop-first:** this site is desktop-first (`max-width`). Discuss why `min-width` is the alternative.

Prerequisite reminder: this only works because of `<meta name="viewport">` in HTML.

## 2.20 Component patterns worth teaching

| Pattern | Class(es) | Concepts combined |
| --- | --- | --- |
| Buttons | `.btn-primary`, `.btn-secondary` | Grouped selectors, hover, transition, variables |
| Card | `.card`, `.card-top`, `.price` | Flex column, `justify-content: space-between`, border hover |
| Badge / pill | `.specialties span` | `border-radius: 999px` |
| Avatar | `.avatar-monogram` | Fixed size, `50%` radius, flex centering |
| Progress bar | `.bar-track` / `.bar-fill` | Inline `width: 98%` on the fill; `overflow: hidden` on the track |
| Star rating | `.stars-gold` | Flex + gap |
| Accordion | `.faq-item` | `<details>`, `[open]`, `::after` |
| Stats | `.stats-box` / `.stat` | Flex wrap, `min-width` |
| Footer | `.footer-grid` | 4-column grid with unequal `fr` |
| Sidebar nav | `.aside nav a` | Flex, icon alignment, transparent border trick |

## 2.21 Naming and organization (BEM-like habits)

- Descriptive, hyphenated class names (`.footer-contact`, `.rating-breakdown`).
- Modifier classes added alongside base classes (`.banner-home`, `.full-width`, `.active`, `.row`, `.column`).
- Stylesheet sections with banner comments, and **all media queries grouped** (note: a few are added later in the file for the reviews and booking sections, a good refactoring discussion).

---

# PART 3: Suggested lesson plan

| Session | Topics | Files |
| --- | --- | --- |
| 1 | Document skeleton, text, entities, links, lists | `semantics.html` |
| 2 | Semantic elements, tables, media, accessibility | `semantics.html` |
| 3 | Forms and validation | `book.html`, `contact.html` |
| 4 | CSS syntax, selectors, specificity | `style.css` |
| 5 | Colors, units, box model, typography | `style.css`, `units.html` |
| 6 | Backgrounds, gradients, animation, positioning | `style.css` |
| 7 | Flexbox | `flexbox.html/css` |
| 8 | Grid | `flexbox.html/css`, `layout.css` |
| 9 | Variables, components, responsive design | `layout.css`, all pages |
| 10 | Review project: build a new page (e.g. "Gift Cards") using the existing classes | |

# PART 4: Exercises

1. **Selectors:** in `semantics.html`, make only the paragraph directly after each `<h3>` italic, without adding a class. (Answer: `h3 + p`.)
2. **Specificity:** why does `.aside nav a.active` beat `.aside nav a`? Add `!important` somewhere, then explain why that is a bad fix.
3. **Units:** set the `html` font size to `20px` and watch which parts of `layout.css` scale (everything in `rem`) and which don't (`px`).
4. **Variables:** change `--accent-amber` to a green and check every page updates.
5. **Flexbox:** center a `<div>` both ways in the viewport using only flex.
6. **Grid:** change `.cards-grid` to 3 columns and add a `grid-column: span 2` card.
7. **Responsive:** add a breakpoint at 480px that makes `.hero` stack its button under the title.
8. **Forms:** add a `pattern` attribute to the phone field and a `min` attribute to the date input.
9. **Accessibility:** run through the site with only the keyboard (Tab). Where does the focus indicator disappear?

# PART 5: Common pitfalls found in this codebase (good "spot the bug" material)

- `semantics.html` nests `<a>` inside `<button>`. This is invalid HTML (interactive inside interactive). Style the link as a button (`.btn-primary`) instead, as the final site does.
- `.radial-grad` in `style.css` has color stops out of order (`60%` then `20%` then `10%`). Browsers fix up the stops, but the result is surprising.
- `semantics.html` ends the quote with `&ldquo;` twice. The closing mark should be `&rdquo;`.
- `style.css` `* { color: aqua; margin: 5px; padding: 5px }` shows why a universal selector with real values is risky. Compare to the clean reset in `layout.css`.
- `units.html` references `.unit-mm`, `.unit-cm`, `.unit-inch`, `.unit-quarter` and `.unit-pixel`, but those rules are commented out in `style.css`, so those headings render at the default size.
- `style.css` sets `h1 { text-align: center }` and `a[href] { font-size: 30px }`, which is useful to show that attribute selectors have broad reach.
- `layout.css` removes the focus outline on inputs. Fine since a border color replaces it, but discuss keyboard users.
- `README.md` describes "Great Cut" (floor plan, dashboard, dark mode) while the final pages are "Crown & Blade", so the README is ahead of the code. Use it to talk about documentation drift.
- Some `.html` pages link to files that don't exist yet (`barbers.html`, `dashboard.html` in `semantics.html`). Check for broken links before shipping.
- `index.html` is missing `<meta name="description">`.
