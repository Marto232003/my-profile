# Profile page – notes for the AI-assisted challenges

## Understanding Font Awesome
- **What it is:** a library of ready-made icons you load once in the page, then call with a class (`fa-solid fa-heart`).
- **Why an icon library:** same style everywhere, scalable like text, no image to draw or export one by one.
- **Alternatives:** Google Material Symbols, Bootstrap Icons, Heroicons.
- **Implementation:** followed the official docs (free CSS loaded from a CDN) and added a heart next to my name,
  a location pin, section icons and a GitHub icon. AI explained the tool; the docs gave the code.

## Grouping content with div
- Elements that belong together: avatar + title + location + text + button = my intro; each hobby/skill = one card;
  the links = contact.
- Each group is now wrapped, and named when the name is obvious: `<nav>` (sidebar), `<main>`, `<header>` (intro),
  `<section class="cards">` with `<article>` cards, `<footer>` (contact).
- These tags render exactly like a `div`; they only add meaning for screen readers and search engines.
  `<container>` or `<box>` would not be valid HTML.

## Choosing Grid or Flexbox
- My cards are a structure of rows and columns, not one line that wraps → Grid describes it directly.
- `.cards { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }`
- Tested `1fr 1fr 1fr` (three columns) then back to two: one value to change. On mobile it falls back to one column.

## Profile with a fixed sidebar
- `.sidebar` is `position: fixed` on the left (200px), `.page-content` has `margin-left: 200px`,
  `.container` still centres the content. Internal links (`#about`, `#ux`…) jump to each section.
