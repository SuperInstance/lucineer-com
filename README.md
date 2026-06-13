# Lucineer

A **structured lucid dream practice tracker** deployed as a Cloudflare Worker at lucineer.com — featuring technique guides backed by sleep research, automated dream sign tracking with occurrence counts, monthly progress charts, and SSILD (Senses Initiated Lucid Dream) instructions.

## Why It Matters

Lucid dreaming practice fails not because techniques don't work, but because practitioners don't track what works. Most apps treat dream journaling as a passive diary — write dreams, maybe tag them. Lucineer treats it as a training log: your dream signs (recurring patterns that indicate you're dreaming) are tracked with occurrence counts, your lucid rate is charted month-over-month, and technique descriptions include evidence citations. The "Houses with impossible rooms: 11 occurrences" format directly answers: "What should trigger my reality checks?" Lucineer's differentiated approach: every technique lists its evidence base (LaBerge 1990, Stumbrys 2012) and its difficulty level, so users know what to expect.

## How It Works

**Architecture**: Single Cloudflare Worker serving complete HTML with inline CSS. The page is a static document rendered on every request — no client framework, no API calls. This delivers the fastest possible load time: sub-50ms globally via Cloudflare's edge network.

**Content design**: The application is organized around the practice loop:

```
Observe → Identify Dream Signs → Set Triggers → Practice → Measure → Adjust
```

**Core sections**:

1. **Technique library** — three pillars with citations:
   - **Reality Testing (RCT)**: Nose pinch, finger-through-palm, text reread. Evidence: LaBerge & Rheingold, 1990.
   - **WBTB (Wake Back to Bed)**: Alarm at 4.5-5h, wake 15-20 min, review journal, return to sleep. Evidence: Stumbrys et al., 2012.
   - **SSILD (Senses Initiated Lucid Dream)**: Post-WBTB, cycle through visual/auditory/tactile focus 4-5 times. Community-developed, widely validated.

2. **Dream sign tracker** — recurring elements with occurrence counts:
   - "Houses with impossible rooms" → 11 occurrences
   - "Water where it shouldn't be" → 9 occurrences
   - "High school people, wrong context" → 7 occurrences
   
   These are the user's personal triggers. When encountered while awake → reality check.

3. **Progress visualization** — monthly lucid rate bar chart:
   - October: 12% → November: 18% → December: 22% → January: 28%
   - Shows 2.3× improvement over 4 months of consistent practice

**Design philosophy**: Dark theme (#0a0a0a) with cyan accent (#22d3ee) — clinical and precise, distinguishing Lucineer from the dreamier LucidDreamer aesthetic. All serif body text (Georgia), monospace metadata (JetBrains Mono).

**Deployment**: Cloudflare Worker with custom domain `lucineer.com` via Workers custom domain routing.

## Quick Start

```bash
# Deploy
npx wrangler deploy

# Local development
npx wrangler dev
```

## API

| Route | Method | Description |
|-------|--------|-------------|
| `/` | GET | Full HTML lucid dream practice tracker |

## Architecture Notes

Lucineer is the companion application to LucidDreamer AI — same deployment pattern (Cloudflare Worker, single HTML response), different aesthetic and focus. Lucineer emphasizes practice tracking; LucidDreamer emphasizes dream journaling. Both serve the SuperInstance web portfolio. In **γ + η = C**, serverless deployment eliminates infrastructure γ entirely. See [Architecture](https://github.com/SuperInstance/SuperInstance/blob/main/ARCHITECTURE.md).

## References

- LaBerge, S. & Rheingold, H. *Exploring the World of Lucid Dreaming*, Ballantine (1990).
- Stumbrys, T. et al. "Induction of Lucid Dreams: A Systematic Review," IJoDR (2012).
- Cloudflare Workers Documentation. https://developers.cloudflare.com/workers/

## License

MIT
