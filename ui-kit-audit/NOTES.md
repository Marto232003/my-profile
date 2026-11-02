# Auditing another UI kit – notes

## What I spotted by eye
- `.cta` has a radius of 8px and a font size of 17px, the other buttons 6px and 16px.
- `.signup` and `.cta` blues look the same but are written differently.
- Selector names like `.footer-button` describe where the button sits, not what it is.

## AI inventory (tables only, no refactor)
| Value | Used by |
| --- | --- |
| `#2f6fed` | .btn-hero, .ghost-link, .btn2, .footer-button, .tag |
| `#2e6fee` | .signup |
| `#3070ed` | .cta |
| padding `14px 28px` | .btn-hero, .btn2 |
| padding `14px 26px` / `15px 28px` / `12px 28px` | .signup / .cta / .footer-button |
| radius `6px` / `8px` | most buttons / .cta |
| font-size `16px` / `17px` / `15px` | most buttons / .cta / .footer-button |
| white `#fff` / `#ffffff` / `white` | mixed spellings |
| weight `bold` / `700` | mixed spellings |
| cards | .plan-card (24px, shadow 0.1) vs .feature-box (26px, shadow 0.12) |

Location-based names: `.btn-hero`, `.footer-button`, `.btn2`, `.feature-box`.

## Drift vs intent
| Accidental drift (6 families) | Winning value |
| --- | --- |
| Three blues | `#2f6fed` |
| Four paddings | `14px 28px` |
| Two radii | `6px` |
| Three font sizes | `16px` |
| Spellings of white and bold | `#ffffff`, `bold` |
| Two cards | one `.card`: 24px, shadow 0.1 |

| Deliberate difference | Why |
| --- | --- |
| `.ghost-link` | a real secondary variant; 12px 26px + 2px border = same outer size as 14px 28px |
| `.tag` | a label, not a button (999px radius, small text) |

AI listed the eight differences with the same confidence; only the designer's intent separates the six accidents from the two choices.

## Result
- About 60 lines of button and card CSS became about 30.
- "Book a demo" in the footer: built with existing classes, zero new CSS.
- Changing the brand blue to `#e2574c`: one line (`--brand-blue`) instead of five.
