# Exercise: Audit "Byte & Bite"

Byte & Bite is a coffee bar that hosts coding workshops. Their website (`index.html`) **looks perfectly fine** — open it in your browser and click around with your mouse: everything appears to work.

It isn't fine. The page violates **all four POUR principles** (Perceivable, Operable, Understandable, Robust) in more than **15 places**.

## Your assignment

1. **Open `index.html` in your browser** and use it like a normal visitor first. Try to reserve a spot for a workshop.
2. **Now audit it.** Find as many accessibility problems as you can. For every problem, write down:
   - **Where** it is on the page
   - **Which POUR principle** it violates
   - **Why** it is a problem (who does it exclude?)
   - **How** you would fix it
3. **Bonus:** actually fix the page. Make a copy of `index.html` and repair every issue you found.

## How to hunt

You will not find everything by just looking — that's the point. Use these techniques, in this order:

- **Put your mouse away.** Try to complete the whole reservation using only <kbd>Tab</kbd>, <kbd>Shift+Tab</kbd>, <kbd>Enter</kbd>, <kbd>Space</kbd> and the arrow keys. Note everything you can't reach, can't see, or can't operate — and whether the order you move through the form makes sense.
- **Read the source code.** Open `index.html` in your editor. Look critically at every `<img>`, every form field, every `id`, every `onclick`, and at what *isn't* there (labels? headings? landmarks? `lang`?).
- **Use a screen reader.** macOS: VoiceOver (<kbd>Cmd+F5</kbd>). Windows: NVDA (free). Try to find out which workshops are full, and what the form fields are called.
- **Run an automated check.** Chrome/Edge DevTools → Lighthouse → Accessibility, or the axe DevTools extension. Note: automated tools typically find **less than half** of the real issues — compare their output with your own list.
- **Check contrast.** Use the browser DevTools colour picker or webaim.org/resources/contrastchecker on any text that looks faint.

## Scoring yourself

| Issues found | Level |
|---|---|
| 5–8 | Good start — you caught the obvious ones |
| 9–13 | Solid audit |
| 14+ | Excellent — recruiter-ready |

When you're done (and only then!), compare your list with `SOLUTION.md`.
