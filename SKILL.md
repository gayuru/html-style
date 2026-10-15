---
name: html-style
description: House design and writing style for any standalone HTML page or Claude Artifact — plain-English copy (GOV.UK + Simplified Technical English) plus a Geist/Vercel-inspired (Inter + JetBrains Mono, ink/canvas palette, stacked-shadow surfaces, pill buttons, mono eyebrows, one mesh gradient; Sitemate blue for Sitemate work, purple otherwise) look with a light/dark switch. Use whenever building, generating, or styling an HTML page, report, checklist, dashboard, or Artifact, unless a different look is asked for.
---

# HTML design and writing style

Style every HTML page and Artifact with this system, and write its copy with the writing style below, unless asked for something else. Calm, Vercel/Geist-inspired: restraint over decoration.

## Install

Save this file as `~/.claude/skills/html-style/SKILL.md`. Everything needed is in this one file.

## How to use it

1. Paste the **Design system CSS** block below into a `<style>` tag in `<head>`.
2. Paste the **Dark theme CSS** block right after it, in the same `<style>` tag.
3. Add the **early script** right after `</style>`.
4. Put the **toggle button** in the page header, right-aligned next to the eyebrow.
5. Add the **toggle script** at the end of `<body>`.

### Fonts

- Sans: **Inter** (400/500/600). Mono: **JetBrains Mono** (400).
- Local files: load from Google Fonts: `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=JetBrains+Mono&display=swap`.
- Artifacts allow Google Fonts stylesheets, so the same link works there. If a page blocks external fonts, the system fallback stack in the CSS takes over.
- Keep `font-feature-settings: "ss01","ss02","cv11"` on `body`.

## The look in one breath

Off-white `#fafafa` page, near-black `#171717` ink, white cards floating on a **stacked shadow + inset hairline ring** (`--ds-1` … `--ds-5`). Mono uppercase **eyebrows** label sections. Tight negative letter-spacing on display sizes. Pill-shaped primary buttons in solid ink. One optional **mesh** gradient for hero atmosphere.

## Which brand colour

- **Sitemate work** (Sitemate, Storm, Dashpivot, AI Platform, a Sitemate ticket key or customer) → **Sitemate blue `#0085e8`**. Use `.mesh-bg-sitemate` and `--sitemate` / `--sitemate-deep` / `--sitemate-soft`.
- **Everything else** → the **purple** mesh (`.mesh-bg`) and `--violet`.

One brand per page. Never mix the two meshes.

Contrast: `--sitemate` is 3.8:1 on white, so use it for UI, borders, large text, and the mesh. For **body-size text use `--sitemate-deep` (6.2:1)**. `--link #0070f3` stays the link colour; Sitemate blue is a brand accent, not a link colour.

## Tokens (CSS vars)

- **Ink/text**: `--ink #171717` · `--body #4d4d4d` · `--mute #888`
- **Surfaces**: `--canvas #fff` (cards) · `--canvas-soft #fafafa` (page bg) · `--canvas-soft-2 #f5f5f5` · `--hairline #ebebeb`
- **Accents**: `--link #0070f3` · warning `#f5a623` · good `#0a6b2c` · error `#ee0000` · brand `--violet #7928ca` `--pink #ff0080` `--cyan #50e3c2`
- **Sitemate**: `--sitemate #0085e8` · `--sitemate-deep #0063ae` · `--sitemate-soft #d6ebfc`
- **Type**: `.display-xl/lg/md/sm` (600, negative tracking) · `.lead` 18px · body 16px · `.eyebrow` (mono caps) · `.mono`
- **Spacing**: `--xxs 4` `--xs 8` `--sm 12` `--md 16` `--lg 24` `--xl 32` `--2xl 40` `--3xl 48` `--4xl 64` `--5xl 96`
- **Radii**: `--r-xs 4` `--r-sm 6` `--r-md 8` `--r-lg 12` `--r-xl 16` `--r-pill 100`
- **Shadows**: `--ds-1` (ring only) → `--ds-5` (lifted). Cards default to `--ds-3`.

## Component classes

- `.card` / `.card-lg` / `.card-soft`: white surface, rounded, `ds-3` / `ds-4` / `ds-1`
- `.badge` + `.info` `.good` `.warn` `.error` `.sitemate` `.mono`: pill tags
- `.btn` + `.primary` `.secondary` `.sm`: pill buttons (primary = solid ink)
- `.eyebrow`: mono uppercase section label
- `.page` (max 1400) / `.prose` (max 880) / `.hairline` divider
- `.mesh-bg` / `.mesh-bg-sitemate`: hero atmosphere, top of page only

## Rules of thumb

1. **Page background is `--canvas-soft`, never pure white.** Cards are white and lift off it with `ds-3`.
2. **Hairline ring, not hard borders.** Use `--ds-*` shadows for separation. Use a 1px `--hairline` border only for dividers and tables.
3. **Every major section gets an eyebrow.** Mono, uppercase, `0.06em` tracking, `--body` colour.
4. **Do not override the negative letter-spacing** on `.display-*`.
5. **One primary action per view.** Primary = ink pill. Secondary = white pill with `ds-1`.
6. **Generous vertical rhythm.** Section padding `--4xl`/`--5xl`, card padding `--lg`/`--xl`.
7. **Keep the focus-visible ring and the reduced-motion block** (both in the CSS).
8. **Restraint.** No gradients except the one mesh. No shadows outside `--ds-*`. Colour is functional (links, status, brand), not decoration.
9. **Every colour goes through a token**, so the theme switch covers the whole page.

## Theme switch (required)

Every page ships a light/dark switch. **Light is the default.** Do not apply the viewer's OS dark preference automatically, so do **not** add a `@media (prefers-color-scheme: dark)` block. The choice persists per viewer in `localStorage` under `theme`, wrapped in try/catch. The button label reads "Dark mode" when light is active and "Light mode" when dark is active. On non-Sitemate pages, change the switch's active colour from `var(--sitemate)` to `var(--violet)`.

## Writing style (all page copy)

The words on the page follow plain English: GOV.UK style plus Simplified Technical English (ASD-STE100). Keep the substance. Change how it reads.

### Structure

- start from what the reader needs to know to act or decide
- put the most important point first: in the page, the section, the paragraph, and the sentence
- give one idea in each sentence and one topic in each paragraph
- keep paragraphs short: 3 sentences for steps, 6 for descriptions
- use numbered lists only for steps the reader does in order
- cap a visible list at about 5 items, then group the rest

### Sentences

- write short sentences: about 15 to 20 words, never more than 25
- use the active voice and name the actor
- use the present tense when you can
- address the reader as "you" and the team as "we"
- be specific: give numbers, names, and dates, not vague abstractions
- cut every word that does not add meaning

### Words

- use simple words, and use each word with one meaning only
- use a simple verb, not a phrasal verb: "start", not "kick off"
- no idioms, slang, metaphors, puns, or humour
- do not use: utilise, facilitate, leverage, deliver, impact (as a verb), unlock, deep dive, robust, key (as an adjective), landscape, ecosystem, seamless, successfully
- no hedging ("maybe", "might", "perhaps") unless the doubt is real
- no Latin abbreviations: write "for example", not "eg"
- write "and", not "&"

### Formatting

- sentence case everywhere: titles, headings, buttons, table headers
- headings front-load the topic, stay under 65 characters, and take no full stop
- bullets start lowercase, carry one idea each, and take no final full stop
- no bold, italics, or capitals for emphasis; the eyebrow and display classes do the hierarchy
- no exclamation marks
- emoji only at the start of a line, bullet, or table cell, never mid-sentence
- link text names the destination, never "click here" or "read more"
- dates as "4 June 2026", times as "10am to 11.30am"

### UI copy (buttons, states, messages)

- buttons name the action: "Save form", not "OK" or "Continue"
- success: `[Object] [past-tense verb].` for example "Report saved."
- error: what happened in plain words, then what to do next
- loading: verb-ing + object + one ellipsis character, for example "Generating your report…"
- confident, practical, helpful, warm, never cheesy: no "Woohoo", no forced excitement

### Self-check before you publish

- is the most important thing first?
- can a non-expert understand every sentence on first read?
- is every sentence active, short, and one idea?
- can you cut more words without losing meaning?

## Minimal skeleton

```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width, initial-scale=1">
<title>Short Name</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=JetBrains+Mono&display=swap" rel="stylesheet">
<style>/* design system CSS + dark theme CSS */</style>
<script>/* early script */</script>
</head>
<body>
  <div class="mesh-bg-sitemate" style="position:absolute;inset:0 0 auto 0;height:480px;z-index:-1"></div>
  <main class="page prose">
    <header style="display:flex;justify-content:space-between;align-items:center;padding:var(--xl) 0">
      <p class="eyebrow">Section label</p>
      <!-- toggle button -->
    </header>
    <h1 class="display-lg">Title</h1>
    <p class="lead">One-line lead.</p>
    <div class="card">…</div>
  </main>
  <script>/* toggle script */</script>
</body>
</html>
```

## Design system CSS

```css
/* ============================================================================
   HTML Design System — "Geist/Vercel-inspired"
   Inter + JetBrains Mono, ink/canvas palette, stacked-shadow surfaces,
   pill buttons, mono eyebrows, one mesh gradient.
   Self-contained. Inline this in standalone HTML files, or <link> it locally.
   ============================================================================ */

:root {
  /* — Ink & text — */
  --ink: #171717;            /* primary text, dark surfaces, primary buttons */
  --body: #4d4d4d;           /* body copy on light */
  --mute: #888888;           /* captions, meta, de-emphasised */

  /* — Surfaces — */
  --canvas: #ffffff;         /* cards */
  --canvas-soft: #fafafa;    /* page background */
  --canvas-soft-2: #f5f5f5;  /* inset / hover fills */
  --hairline: #ebebeb;       /* borders, dividers */
  --hairline-strong: #a1a1a1;

  /* — Accents — */
  --link: #0070f3;
  --link-deep: #0761d1;
  --link-bg-soft: #d3e5ff;
  --error: #ee0000;  --error-soft: #f7d4d6;  --error-deep: #c50000;
  --warning: #f5a623; --warning-soft: #ffefcf; --warning-deep: #ab570a;
  --good: #0a6b2c;   --good-soft: #dcf5e6;
  --violet: #7928ca; --pink: #ff0080; --cyan: #50e3c2;

  /* — Sitemate brand — use for Sitemate/Storm/Dashpivot work only — */
  --sitemate: #0085e8;        /* core brand blue; UI + large text (3.8:1 on white) */
  --sitemate-deep: #0063ae;   /* body-text safe (6.2:1 on white) */
  --sitemate-soft: #d6ebfc;   /* pale tint for badge/callout fills */

  /* — Type scale [size / line-height / letter-spacing] — */
  --fs-display-xl: 48px;  --lh-display-xl: 48px;  --ls-display-xl: -2.4px;
  --fs-display-lg: 32px;  --lh-display-lg: 40px;  --ls-display-lg: -1.28px;
  --fs-display-md: 24px;  --lh-display-md: 32px;  --ls-display-md: -0.96px;
  --fs-display-sm: 20px;  --lh-display-sm: 28px;  --ls-display-sm: -0.6px;
  --fs-body-lg: 18px;     --lh-body-lg: 28px;
  --fs-body-md: 16px;     --lh-body-md: 24px;
  --fs-body-sm: 14px;     --lh-body-sm: 20px;     --ls-body-sm: -0.28px;
  --fs-caption: 12px;     --lh-caption: 16px;
  --fs-code: 13px;        --lh-code: 20px;

  /* — Spacing scale — */
  --xxs: 4px; --xs: 8px; --sm: 12px; --md: 16px; --lg: 24px;
  --xl: 32px; --2xl: 40px; --3xl: 48px; --4xl: 64px; --5xl: 96px; --6xl: 128px;

  /* — Radii — */
  --r-xs: 4px; --r-sm: 6px; --r-md: 8px; --r-lg: 12px; --r-xl: 16px; --r-pill: 100px;

  /* — Shadows: inset hairline ring + stacked soft drop — */
  --ds-1: 0 0 0 1px var(--ring) inset;
  --ds-2: 0 0 0 1px var(--ring) inset, 0 1px 1px rgba(0,0,0,0.02), 0 2px 2px rgba(0,0,0,0.04);
  --ds-3: 0 0 0 1px var(--ring) inset, 0 2px 2px rgba(0,0,0,0.04), 0 8px 8px -8px rgba(0,0,0,0.04);
  --ds-4: 0 0 0 1px var(--ring) inset, 0 2px 2px rgba(0,0,0,0.04), 0 8px 16px -4px rgba(0,0,0,0.04);
  --ds-5: 0 0 0 1px var(--ring) inset, 0 1px 1px rgba(0,0,0,0.02), 0 8px 16px -4px rgba(0,0,0,0.04), 0 24px 32px -8px rgba(0,0,0,0.06);

  --ring: rgba(0,0,0,0.08);

  --max-page: 1400px;
  --max-prose: 880px;
}

* { box-sizing: border-box; }

html { scroll-behavior: smooth; }

body {
  margin: 0;
  background-color: var(--canvas-soft);
  color: var(--ink);
  font-family: "Inter", ui-sans-serif, system-ui, -apple-system, "Segoe UI", sans-serif;
  font-feature-settings: "ss01", "ss02", "cv11";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  font-size: var(--fs-body-md);
  line-height: var(--lh-body-md);
}

/* Visible focus rings on every interactive element */
:focus-visible {
  outline: 2px solid var(--link);
  outline-offset: 2px;
  border-radius: var(--r-xs);
}

@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.001ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.001ms !important;
    scroll-behavior: auto !important;
  }
}

/* — Typography helpers — */
.eyebrow {
  font-family: "JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, monospace;
  font-size: var(--fs-caption);
  line-height: var(--lh-caption);
  text-transform: uppercase;
  letter-spacing: 0.06em;
  color: var(--body);
}
.display-xl { font-size: var(--fs-display-xl); line-height: var(--lh-display-xl); letter-spacing: var(--ls-display-xl); font-weight: 600; }
.display-lg { font-size: var(--fs-display-lg); line-height: var(--lh-display-lg); letter-spacing: var(--ls-display-lg); font-weight: 600; }
.display-md { font-size: var(--fs-display-md); line-height: var(--lh-display-md); letter-spacing: var(--ls-display-md); font-weight: 600; }
.display-sm { font-size: var(--fs-display-sm); line-height: var(--lh-display-sm); letter-spacing: var(--ls-display-sm); font-weight: 600; }
.lead { font-size: var(--fs-body-lg); line-height: var(--lh-body-lg); color: var(--body); }
.muted { color: var(--mute); }
.mono { font-family: "JetBrains Mono", ui-monospace, SFMono-Regular, Menlo, monospace; }

a { color: var(--link); text-decoration: none; }
a:hover { text-decoration: underline; }

/* — Surfaces — */
.card {
  background: var(--canvas);
  padding: var(--lg);
  border-radius: var(--r-md);
  box-shadow: var(--ds-3);
}
.card-lg { padding: var(--xl); border-radius: var(--r-lg); box-shadow: var(--ds-4); }
.card-soft { background: var(--canvas-soft); box-shadow: var(--ds-1); }

/* — Badges / pills — */
.badge {
  display: inline-flex; align-items: center;
  font-size: var(--fs-caption); line-height: var(--lh-caption);
  padding: 2px 10px; border-radius: var(--r-pill);
  background: var(--canvas-soft-2); color: var(--body);
}
.badge.info { background: var(--link-bg-soft); color: var(--link-deep); }
.badge.good { background: var(--good-soft); color: var(--good); }
.badge.warn { background: var(--warning-soft); color: var(--warning-deep); }
.badge.error { background: var(--error-soft); color: var(--error-deep); }
.badge.sitemate { background: var(--sitemate-soft); color: var(--sitemate-deep); }
.badge.mono { font-family: "JetBrains Mono", ui-monospace, monospace; text-transform: uppercase; letter-spacing: 0.04em; }

/* — Buttons — */
.btn {
  display: inline-flex; align-items: center; justify-content: center;
  font-weight: 500; white-space: nowrap; user-select: none; cursor: pointer;
  border: none; transition: box-shadow .15s ease, background .15s ease;
  font-size: var(--fs-body-md); height: 48px; padding: 0 28px; border-radius: var(--r-pill);
}
.btn.primary { background: var(--ink); color: var(--canvas); }
.btn.primary:hover { opacity: 0.88; }
.btn.secondary { background: var(--canvas); color: var(--ink); box-shadow: var(--ds-1); }
.btn.secondary:hover { box-shadow: var(--ds-2); }
.btn.sm { height: 32px; padding: 0 12px; border-radius: var(--r-sm); font-size: var(--fs-body-sm); }

/* — Layout — */
.page { max-width: var(--max-page); margin: 0 auto; padding: var(--lg); }
.prose { max-width: var(--max-prose); margin: 0 auto; }
.hairline { border: none; border-top: 1px solid var(--hairline); margin: var(--xl) 0; }

/* — Brand mesh background (hero atmosphere) —
   `.mesh-bg`          purple — the default, for everything that isn't Sitemate
   `.mesh-bg-sitemate` Sitemate blue #0085e8 — for Sitemate/Storm/Dashpivot pages
   Pick one. Never both, never two meshes on a page.                            */
.mesh-bg,
.mesh-bg-sitemate {
  background-color: var(--canvas-soft);
  -webkit-mask-image: linear-gradient(to bottom, black 0%, black 40%, rgba(0,0,0,0.5) 75%, transparent 100%);
  mask-image: linear-gradient(to bottom, black 0%, black 40%, rgba(0,0,0,0.5) 75%, transparent 100%);
}
.mesh-bg {
  background-image:
    radial-gradient(at 25% 15%, rgba(121, 40, 202, 0.22) 0px, transparent 55%),
    radial-gradient(at 78% 22%, rgba(167, 139, 250, 0.28) 0px, transparent 55%),
    radial-gradient(at 50% 0%, rgba(139, 92, 246, 0.18) 0px, transparent 60%),
    radial-gradient(at 92% 55%, rgba(196, 181, 253, 0.22) 0px, transparent 55%),
    radial-gradient(at 8% 55%, rgba(216, 180, 254, 0.18) 0px, transparent 55%);
}
.mesh-bg-sitemate {
  background-image:
    radial-gradient(at 25% 15%, rgba(0, 133, 232, 0.22) 0px, transparent 55%),
    radial-gradient(at 78% 22%, rgba(93, 173, 240, 0.28) 0px, transparent 55%),
    radial-gradient(at 50% 0%, rgba(0, 133, 232, 0.16) 0px, transparent 60%),
    radial-gradient(at 92% 55%, rgba(150, 205, 248, 0.22) 0px, transparent 55%),
    radial-gradient(at 8% 55%, rgba(179, 219, 250, 0.18) 0px, transparent 55%);
}
```

## Dark theme CSS

```css
:root[data-theme="dark"] {
  --ink: #ededed; --body: #b4b4b4; --mute: #7d7d7d;
  --canvas: #141414; --canvas-soft: #0a0a0a; --canvas-soft-2: #1c1c1c;
  --hairline: #262626; --hairline-strong: #4a4a4a;
  --link: #52a8ff; --link-deep: #8cc4ff; --link-bg-soft: #0b2a4a;
  --error-soft: #3a0d0d; --error-deep: #ff7b7b;
  --warning-soft: #33250a; --warning-deep: #fbbf24;
  --good: #4ade80; --good-soft: #0d2e1a;
  --sitemate-deep: #7cc0ff; --sitemate-soft: #0b2a45;
  --ring: rgba(255,255,255,0.10);
  color-scheme: dark;
}
.theme-toggle { display: inline-flex; align-items: center; gap: 8px; height: 32px; padding: 0 12px; border-radius: var(--r-pill); border: none; background: var(--canvas); color: var(--ink); box-shadow: var(--ds-1); font-family: "Inter", ui-sans-serif, system-ui, sans-serif; font-size: var(--fs-body-sm); font-weight: 500; line-height: 1; cursor: pointer; transition: box-shadow .15s ease; }
.theme-toggle:hover { box-shadow: var(--ds-2); }
.theme-toggle .sw { position: relative; width: 26px; height: 14px; border-radius: var(--r-pill); background: var(--hairline-strong); flex: none; }
.theme-toggle .sw::after { content: ""; position: absolute; top: 2px; left: 2px; width: 10px; height: 10px; border-radius: 50%; background: var(--canvas); transition: transform .15s ease; }
.theme-toggle[aria-pressed="true"] .sw { background: var(--sitemate); } /* use var(--violet) on non-Sitemate pages */
.theme-toggle[aria-pressed="true"] .sw::after { transform: translateX(12px); }
```

## Early script

Place right after `</style>` so the page never flashes the wrong theme.

```html
<script>
(function(){var t='light';try{var s=localStorage.getItem('theme');if(s==='dark'||s==='light'){t=s;}}catch(e){}document.documentElement.setAttribute('data-theme',t);})();
</script>
```

## Toggle button

```html
<button type="button" class="theme-toggle" id="theme-toggle" aria-pressed="false" aria-label="Switch between light and dark mode"><span class="sw" aria-hidden="true"></span><span class="lbl">Dark mode</span></button>
```

## Toggle script

```html
<script>
(function(){
  var root = document.documentElement;
  var btn = document.getElementById('theme-toggle');
  if (!btn) return;
  var lbl = btn.querySelector('.lbl');
  function current(){ return root.getAttribute('data-theme') === 'dark' ? 'dark' : 'light'; }
  function paint(){
    var dark = current() === 'dark';
    lbl.textContent = dark ? 'Light mode' : 'Dark mode';
    btn.setAttribute('aria-pressed', dark ? 'true' : 'false');
  }
  btn.addEventListener('click', function(){
    var next = current() === 'dark' ? 'light' : 'dark';
    root.setAttribute('data-theme', next);
    try { localStorage.setItem('theme', next); } catch (e) {}
    paint();
  });
  paint();
})();
</script>
```
