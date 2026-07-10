# Solution: the 18 planted problems in "Byte & Bite"

Don't read this until you've made your own list! Issues are grouped by POUR principle. WCAG references are to WCAG 2.2 success criteria.

---

## Perceivable

### P1. Hero image has no `alt` attribute
`<img src="../assets/coffee.svg" width="320" height="180">` — a screen reader announces the file name or nothing.
**Fix:** describe it (`alt="A steaming cup of coffee"`) or, since it's decorative here, use `alt=""` so it's skipped. *(WCAG 1.1.1 Non-text Content)*

### P2. Opening hours in low-contrast text
`.hours { color: #b8b2a7; }` on the off-white background is roughly a 2:1 contrast ratio — WCAG requires at least **4.5:1** for body text. And it's the only place the address and hours appear.
**Fix:** darken the colour, e.g. `#6b6458` or darker. *(WCAG 1.4.3 Contrast Minimum)*

### P3. Form fields have placeholders instead of labels
"Your name", "E-mail address" exist only as placeholders. They vanish while typing and are unreliable in screen readers.
**Fix:** add a visible `<label for="...">` for every field. *(WCAG 1.3.1 Info and Relationships, 3.3.2 Labels or Instructions)*

### P4. Workshop availability shown by colour only
Full vs. open workshops differ only by a green or red dot. Colour-blind users can't tell them apart — and the dots are empty `<span>`s, so screen reader users get *no* information at all.
**Fix:** add text, e.g. a "Full" / "Spots available" badge next to each workshop (colour can stay as reinforcement). *(WCAG 1.4.1 Use of Color, 1.1.1)*

### P5. Validation errors are a red border and nothing else
Submit the empty form: fields get a red border (colour only), with no message saying what's wrong or how to fix it.
**Fix:** show a text error message per field, link it with `aria-describedby`, set `aria-invalid="true"`, and move focus to the first error. *(WCAG 1.4.1, 3.3.1 Error Identification, 3.3.3 Error Suggestion)*

---

## Operable

### O1. All focus outlines removed
`* { outline: none; }` — keyboard users can never see where they are.
**Fix:** delete that rule and add a clear indicator, e.g. `:focus-visible { outline: 3px solid #1d4ed8; outline-offset: 2px; }`. *(WCAG 2.4.7 Focus Visible)*

### O2. "Workshops ▾" dropdown only opens on hover
The trigger is a `<span>` (not focusable) and the panel opens with CSS `:hover` — keyboard and most touch users can never open it.
**Fix:** make the trigger a `<button>` with `aria-expanded`, toggle the panel on click/Enter/Space, close on Escape. *(WCAG 2.1.1 Keyboard)*

### O3. "Reserve" button is a `<div onclick>`
Not focusable, doesn't respond to Enter/Space, not announced as a button. Same for the "Join" `<span>` in the footer.
**Fix:** use `<button type="submit">` (and `<button>` for Join) — the styling can stay identical. *(WCAG 2.1.1, 4.1.2 Name, Role, Value)*

### O4. Positive `tabindex` scrambles the focus order
The form fields have `tabindex="3"`, `tabindex="1"`, `tabindex="2"` — tabbing jumps e-mail → workshop → name, in a different order than they appear visually.
**Fix:** remove all positive `tabindex` values; the natural DOM order is already correct. *(WCAG 2.4.3 Focus Order)*

### O5. No skip link
There's no way to jump past the header/navigation straight to the content.
**Fix:** add `<a class="skip-link" href="#main">Skip to content</a>` as the first focusable element (visually hidden until focused). *(WCAG 2.4.1 Bypass Blocks)*

---

## Understandable

### U1. No `lang` attribute
The document starts with a bare `<html>`. Screen readers must guess the pronunciation language.
**Fix:** `<html lang="en">`. *(WCAG 3.1.1 Language of Page)*

### U2. "Click here" links (three of them)
"Curious what people think of us? *Click here*." — in a screen reader's link list these are indistinguishable.
**Fix:** make the link text describe the destination: "Read our reviews", "Download the schedule (PDF)", "Get directions". *(WCAG 2.4.4 Link Purpose)*

### U3. Selecting a workshop instantly "navigates"
The `<select>` fires navigation `onchange`, so keyboard users who browse options with the arrow keys trigger it immediately — an unexpected context change.
**Fix:** never navigate on `change`; let the selection just be a selection (it's part of a form here), or require an explicit "Go" button. *(WCAG 3.2.2 On Input)*

### U4. Failed submit gives no guidance
Nothing tells you *which* field is wrong or *what* a correct value looks like (overlaps with P5 — this is the Understandable half of the same defect).
**Fix:** specific messages per field ("Please enter your e-mail address, like name@example.com") plus an error summary. *(WCAG 3.3.1, 3.3.3)*

### U5. E-mail fields are `type="text"`
Both e-mail inputs miss `type="email"` (and `autocomplete="email"`): no e-mail keyboard on mobile, no free browser validation, no autofill.
**Fix:** `<input type="email" autocomplete="email">`. *(WCAG 1.3.5 Identify Input Purpose)*

---

## Robust

### R1. Duplicate `id="email"`
The reservation form field and the footer newsletter field share `id="email"`. Scripts, labels and assistive technology only ever see the first one.
**Fix:** unique ids, e.g. `reserve-email` and `newsletter-email`. *(WCAG 4.1.1 Parsing / valid markup)*

### R2. Broken heading structure
The page has **no `<h1>`** — the hero tagline and "Upcoming workshops" are styled `<div>`s, and the only real heading is a lone `<h4>` ("Reserve your spot"). Screen reader users navigating by headings find almost nothing, in a nonsensical order.
**Fix:** tagline → `<h1>`, section titles → `<h2>`. *(WCAG 1.3.1)*

### R3. No landmarks
The top bar and page content are plain `<div>`s: no `<header>`, `<nav>`, or `<main>` (only the footer is semantic).
**Fix:** use `<header>`, `<nav>`, `<main>`, so screen reader users can jump between page regions. *(WCAG 1.3.1)*

### R4. Fake checkbox
"I agree to the house rules" is toggled by a styled `<span onclick>`: no checkbox role, no checked/unchecked state, no keyboard support, no label association — screen readers don't even know it exists. Note it isn't validated either, so it silently does nothing.
**Fix:** `<label><input type="checkbox"> I agree to the house rules</label>`, styled with CSS (`accent-color`). *(WCAG 4.1.2, 2.1.1)*

### R5. The workshop `<select>` has no accessible name
No `<label>` points at `#workshop-pick`; only the disabled placeholder option hints at its purpose.
**Fix:** `<label for="workshop-pick">Pick a workshop</label>`. *(WCAG 4.1.2, 1.3.1)*

---

## Checklist recap

| # | Issue | Principle |
|---|---|---|
| P1 | Image without alt | Perceivable |
| P2 | Low-contrast opening hours | Perceivable |
| P3 | Placeholder-only labels | Perceivable |
| P4 | Colour-only availability dots | Perceivable |
| P5 | Colour-only error indication | Perceivable |
| O1 | `outline: none` on everything | Operable |
| O2 | Hover-only dropdown | Operable |
| O3 | `<div>`/`<span>` as buttons | Operable |
| O4 | Positive tabindex, wrong focus order | Operable |
| O5 | No skip link | Operable |
| U1 | Missing `lang` | Understandable |
| U2 | "Click here" links | Understandable |
| U3 | Navigation on `select` change | Understandable |
| U4 | No error messages/guidance | Understandable |
| U5 | Wrong input types / no autocomplete | Understandable |
| R1 | Duplicate `id="email"` | Robust |
| R2 | No `<h1>`, broken heading levels | Robust |
| R3 | No landmarks (div soup) | Robust |
| R4 | Fake checkbox without semantics | Robust |
| R5 | Select without accessible name | Robust |

Several issues legitimately fit more than one principle (e.g. P5/U4) — if you classified one differently but understood *why* it's a problem, count it as found.
