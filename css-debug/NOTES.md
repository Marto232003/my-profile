# Debugging CSS – notes

## My hypotheses before asking AI
- Is the CSS file even loaded? The link points to `css/style.css` but the file is next to index.html.
- The title selector uses `#` (id) while the HTML uses a class.
- One line of the body rule has no `;` at the end.

## AI diagnosis (asked for a list, not a rewrite)
1. **index.html, `<link>`**: wrong path `css/style.css` → nothing loads. Fix: `href="style.css"`.
2. **body, `background-color: #f2f5fb`**: missing `;`, so the browser reads it glued to `text-align` and drops both. Fix: add `;`.
3. **`#page-title`**: matches no element (it is a class). Fix: `.page-title`.
4. **.tagline, `font-size: 24`**: no unit, declaration ignored. Fix: `24px`.
5. **a, `font-color`**: not a CSS property. Fix: `color`.

Hypotheses I had on my own: 1, 2 and 3. AI added 4 and 5. Nothing AI listed was a false alarm.

## Fixed one at a time (what changed on the page)
1. Path fixed → the button, bio width and some styles appear, but no background and no centring.
2. Semicolon added → light blue-grey background and everything centred.
3. Selector fixed → big dark spaced-out uppercase title.
4. Unit added → tagline becomes bigger than the paragraph.
5. `color` → white text on the blue button, readable at last.

## Test
Removing the `px` again: the tagline shrinks back, no error anywhere. Without AI I would find it with
the browser inspector: in the Styles panel the ignored declaration is crossed out with a warning icon.
