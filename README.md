# Malcom Kazuva – Profile & Mini-Portfolio

**Student:** Malcom Kazuva (250931) · kazuvam@africau.edu
**Course:** Web Technologies (CIS2103), Africa University

A responsive profile page for a Computer Information Systems student, built with semantic HTML5, custom CSS3 and Tailwind CSS.

## Project structure

```
index.html   – semantic markup (from Assignment 1, preserved) + Tailwind classes
styles.css   – custom mobile-first CSS
profile.jpg  – profile photo
README.md
```

## Responsive Notes

### Breakpoints tested
Tested in the browser device toolbar at:
- **Mobile – 375px**
- **Tablet – 768px**
- **Desktop – 1280px**

At all three widths there is no horizontal scrollbar, no overlapping text and the navigation stays usable.

### Flexbox vs. Grid
| Section | Layout | Why |
|---|---|---|
| Header navigation | **Flexbox** (`flex`, `flex-col sm:flex-row`, `justify-center`, `items-center`, `gap`) | One-dimensional list of links: a column on mobile, a centred row from `sm`. |
| Contact form field groups | **Flexbox** (`flex flex-col gap-4` / `gap-2`) | Stacks label and input vertically with consistent spacing. |
| About section (`.profile-layout`) | **Grid** (`1fr` → `220px 1fr` → `260px 1fr`, `gap`) | Two-dimensional photo + text layout that changes columns per breakpoint. |
| Skills list (`.skills`) | **Grid** (`repeat(auto-fit, minmax(130px, 1fr))`, `gap`) | Tiles reflow automatically into as many columns as fit, without extra media queries. |
| Quick facts list | **Grid** (`1fr` → `repeat(3, 1fr)` from 768px, `gap`) | Fact cards stack on mobile and sit in three equal columns on larger screens. |

### Tailwind vs. custom CSS (the split)
- **Tailwind utilities:** the `<header>`/`<nav>` and the **Contact form**, including the responsive variants `sm:flex-row`, `sm:gap-4`, `sm:w-auto`, `sm:self-start`, `md:text-5xl`, `md:pt-12`, `md:pb-10` and `md:text-base`.
- **Custom CSS (`styles.css`):** page background, `main`/`section` cards, About grid, the "Get in touch" button, Skills grid, Quick Facts and footer. These use CSS variables for colour, spacing and type scale, and are written mobile-first with `@media (min-width: 768px)` and `@media (min-width: 1280px)` queries.
- Each element is styled by only one of the two approaches, so nothing is duplicated.
- Custom selectors such as `body.page` and `main h2` are slightly more specific than plain element selectors so the Tailwind CDN reset cannot override them.

### Box model
Spacing uses a small scale of CSS variables (`--space-sm/md/lg`) for padding and margins, with `box-sizing: border-box` everywhere and consistent borders and radii on cards.

### Visual design
- Blue/indigo palette defined once as CSS variables.
- Gradient header with pill-style navigation, gradient underline under each section heading, and a ringed profile photo.
- Cards, skill tiles and the call-to-action button lift slightly on hover (only on devices that support hover).
- A `prefers-reduced-motion` media query turns off animations and smooth scrolling for users who ask for that.

## Testing
- Tested at 375px, 768px and 1280px (see above).
- Semantic structure and accessibility work from Assignment 1 retained (`header`, `nav`, `main`, `section`, `article`, `aside`, `footer`, `aria-label`s, label/input pairs, image `alt`).
- No placeholder/Lorem Ipsum text.
- Note: the Tailwind Play CDN prints a "not for production" notice in the console; it is a warning, not an error.
