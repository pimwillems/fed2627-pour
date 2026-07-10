# Web Accessibility Demos — the POUR principles

Welcome! This repo is your hands-on playground for learning **web accessibility** through the four WCAG principles, known as **POUR**:

| Principle | Meaning |
|---|---|
| **P**erceivable | Users must be able to perceive the information — see it, hear it, or feel it (e.g. via braille) |
| **O**perable | Users must be able to operate every control — with a keyboard, mouse, touch, or voice |
| **U**nderstandable | Content and controls must be understandable and predictable |
| **R**obust | Markup must be reliably interpreted by browsers *and* assistive technology (like screen readers) |

Roughly 1 in 5 people has a disability that affects how they use the web. Accessibility isn't a nice-to-have — it's part of your job as a front-end developer (and in the EU, increasingly a legal requirement).

## Getting started

No build step, no dependencies, nothing to install. Clone or download the repo and **open `index.html` in your browser** — it's a launcher page that links to every demo.

```bash
git clone <this-repo-url>
cd accessibility
open index.html        # macOS — or just double-click it
```

## What's in here

```
accessibility/
├── index.html      ← start here: launcher page with links to everything
├── bad/            ← one page per POUR principle, done WRONG
├── best/           ← the SAME pages, done RIGHT
├── exercise/       ← your assignment (see below)
└── assets/         ← shared images
```

### `bad/` vs `best/` — spot the difference

Each principle has a **bad** page (red header) and a **best** page (green header) containing the *same five demos*. Open them side by side in two browser windows and compare. Some things you'll see:

- Images with no alt text vs. useful alt text
- A `<div onclick>` pretending to be a button vs. a real `<button>`
- "Click here" links vs. links that tell you where they go
- A keyboard trap you literally cannot Tab out of
- Div soup vs. proper semantic HTML with landmarks and headings

**Important:** the bad pages often *look* fine. They only fail when you use them the way many real users do — so don't just look at them, **operate** them (see below).

### `exercise/` — your assignment

The exercise folder contains the website of *Byte & Bite*, a café that hosts coding workshops. It looks polished and works fine with a mouse… but it hides **15+ accessibility problems** across all four POUR principles. Your job is to find them.

Read [`exercise/README.md`](exercise/README.md) for the full assignment. And no peeking at `SOLUTION.md` until you're done — you'd only be cheating yourself.

## How to actually test accessibility

Looking at a page tells you almost nothing. Use these techniques — they're the same ones professionals use:

1. **Put your mouse away.** Navigate with <kbd>Tab</kbd>, <kbd>Shift+Tab</kbd>, <kbd>Enter</kbd>, <kbd>Space</kbd> and the arrow keys. Can you reach everything? Can you *see* where you are?
2. **Turn on a screen reader.** macOS: VoiceOver (<kbd>Cmd+F5</kbd>). Windows: [NVDA](https://www.nvaccess.org/) (free). Close your eyes and try to use the page.
3. **Check colour contrast** with the DevTools colour picker or [WebAIM's contrast checker](https://webaim.org/resources/contrastchecker/).
4. **Validate your HTML** at [validator.w3.org](https://validator.w3.org/).
5. **Run an automated audit** — Lighthouse (in Chrome DevTools) or the [axe DevTools](https://www.deque.com/axe/devtools/) extension. Then notice how many issues these tools *miss*: automated checks typically catch less than half. There is no substitute for testing like a real user.

## Reading the source

Every planted problem in the `bad/` pages is marked with a `<!-- BAD: ... -->` comment in the HTML, so reading the source in your editor is a lesson in itself. The `best/` pages show the corrected version of the exact same demo.

## Useful references

- [WCAG quick reference](https://www.w3.org/WAI/WCAG22/quickref/) — the official checklist
- [MDN: Accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility) — practical developer docs
- [WebAIM](https://webaim.org/) — articles, tools, and the contrast checker
- [The A11Y Project](https://www.a11yproject.com/) — community-driven checklist and posts
