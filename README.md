# Career Navigator — clickable prototype

An AI-powered career transition platform that helps homemakers, immigrants,
long-term unemployed individuals, and 40+ career changers identify realistic
career paths, close skill gaps, and return to the workforce.

This is a **single-file, clickable HTML prototype** in the style of
[roadmap.sh](https://roadmap.sh) — no build step, no dependencies.

## Run it

Open `index.html` in any browser. That's it.

```bash
# or serve it locally
npx serve .
```

## What's inside

| View | Route | What it demonstrates |
|---|---|---|
| Home | `#home` | Landing page: value prop, four personas, how-it-works, B2B2C strip |
| Roadmaps | `#roadmaps` | The four persona roadmaps |
| Interactive roadmap | `#roadmap/homemaker` etc. | roadmap.sh-style map: clickable nodes, detail drawer with resources + AI-coach tips, progress tracking (saved in localStorage) |
| Assessment | `#assessment` | 5-question AI assessment demo → 3 matched career paths → personalized roadmap |
| Partners | `#partners` | B2B2C pitch for job centers, training schools, coaches, NGOs + pilot request form (demo) |
| Strategy | `#strategy` | Internal go-to-market timeline (community-led → partner-led → inbound → product-led) |

The four roadmaps:

- `homemaker` — Return to Work (homemakers re-entering the workforce)
- `immigrant` — New-Country Career Launch (new immigrants)
- `restart` — Back on Track (after long-term unemployment)
- `switch40` — Career Switch at 40+

## Notes

- All salaries, demand figures, and partner numbers are **sample data** for
  demo purposes.
- Light and dark themes are supported (toggle in the nav, follows OS
  preference by default).
- Roadmap layout is data-driven: edit the `ROADMAPS` object in `index.html`
  to change phases, steps, descriptions, resources, and AI-coach tips — the
  map redraws itself.
